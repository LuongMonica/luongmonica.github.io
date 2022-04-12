---
layout: post
title:  "Blog 10: GitHub Actions"
date:   2022-04-22 9:59:31 -0700
categories: jekyll update
---
![GitHub Actions Logo](/assets/gh-actions.jpg)
# **Recap and Intro**
Hello! Last week we finished talking about AWS. We covered Auto Scaling and Monitoring by talking about the services ELB, CloudWatch, and EC2 Auto Scaling. In this final post, we'll talk about GitHub Actions. Let's get started!

# **GitHub Actions** 
GitHub Actions is a CI/CD tool that works with your GitHub repositories to do workflow automation. You can do all sorts of things, including linting, building a container, and deploying a web service. GH Actions is completely free for public repositories and self-hosted runners (the application that runs your Actions). For private repositories you get a certain amount of runtime minutes per month, depending on what GitHub Plan you have. Still, it's pretty generous and gives you 2,000 minutes per month if you're on the Free plan. There's no reason not to use GH Actions!

## **Basics**
So how do we get started? First, you'll want to create a GitHub repo; it can be public or private. In your repo, create a folder called `.github/workflows`. This is where we'll be storing our Actions. GH actions are written in your favorite language, YAML. In the `workflows` directory, create a file like `first-action.yml`. In your file, you'll need a few key sections. Take a look at the code below:

```yaml
name: First Action
on: [push]
jobs:
  hello-world:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: run echo cmd
        run: |
          echo "Hello World"
          ls -l
```

The first `name` is the name of your workflow. This is optional, but highly recommended. `on` is when your workflow will be triggered. In this case, it'll run everytime there's a push. `jobs` groups together all the jobs (tasks) that will run in this workflow. `hello-world` is the name of the defined job. `runs-on` defines the OS that the runner will use to execute the job. `steps` groups together each part of the `hello-world` job. `uses` defines the location of the action. In this case, it's located in the [actions/checkout](https://github.com/actions/checkout) repo. `run` is telling the runner to execute a command. The `|` allows you to have multi-line statements. 

To see the results of a run, look to the left of the latest commit hash for a green check (✔️), red X (❌), or yellow-ish dot (🟡). You can also go to the Actions tab in your repo.

## **Example** 
Now let's take a look at a more complicated example. This workflow is for doing a terraform plan. It sets up your AWS credentials, does a `terraform init`, a `terraform plan`, and finally outputs the plan as a comment on the pull request you created. This action only runs when a PR is created and has changes in the terraform directory of the repo. 

```yaml
name: tf plan

on:
  pull_request:
    paths:
    - "terraform/**"

jobs:
  tf-plan: 
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: "Setup - Build AWS Credentials"
        run: |
          mkdir -p ~/.aws
          echo "[default]" > ~/.aws/credentials
          echo "aws_access_key_id = ${{ secrets.ACCESS_KEY_ID }}" >> ~/.aws/credentials
          echo "aws_secret_access_key = ${{ secrets.SECRET_ACCESS_KEY }}" >> ~/.aws/credentials
      - uses: hashicorp/setup-terraform@v1

      - name: "run terraform init"
        run: |
          terraform init
        working-directory: terraform

      - name: "Terraform Plan"
        id: plan
        run: |
          terraform plan -no-color
        working-directory: terraform

      - uses: actions/github-script@0.9.0
        env: 
          STDOUT: "```terraform\n${{ steps.plan.outputs.stdout }}\n```"
        with: 
          script: |
            github.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo, 
              body: process.env.STDOUT
            })
```

# **Outro**
Thank you for reading along! I hope you learned at least one new thing throughout this blogging journey. I started this blog because it was an assignment for CIT480 (Senior Design), but who knows? I might just update it in the future if I want to talk about something cool I've learned! If you have any questions or comments, please feel free to reach out to me at <monica.luong.234@my.csun.edu>. 

# **More Info**
[GitHub Actions](https://github.com/features/actions)

[Quickstart](https://docs.github.com/en/actions/quickstart)

[Learn GH Actions](https://docs.github.com/en/actions/learn-github-actions)

[GH Actions - Docs](https://docs.github.com/en/actions/)

[Repo For GH Actions](https://github.com/actions)
