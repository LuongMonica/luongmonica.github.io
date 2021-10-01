---
layout: post
title:  "Blog 4 - Cortex XSOAR pt. 5"
date:   2021-10-01 9:59:31 -0700
categories: jekyll update
published: false
---

![Cortex XSOAR logo](/assets/xsoar-logo.png)

# **Recap of Last Week**
Last week, we talked more about playbooks and went over an important part of writing them: how to do a loop.

Now, let's talk more about writing playbooks, specifically conditionals.

# **Playbooks - Conditionals and Filters & Transformers**

![Conditional](/assets/xsoar-conditional.png)<br/><font size="2.75px"><em>Conditional task</em></font>

Conditionals, of course, are used for creating branching paths in your playbook. You can create if-then-else statements in XSOAR. To create a simple if-else statement, create a conditional task and select **Built-in**, **Manual**, or **Choose Automation**. You'll most likely be using Built-in and Choose Automation the most. **Built-in** allows you to create a logical statement from the built-in string, date/time, boolean, or number functions. Some examples are 'Equal', 'StartsWith', 'GreaterThan', 'IsTrue', and 'Contains'. Thus, in a playbook, you can do something like create a task that does an `!ad-search` for users whose passwords have expired, create a conditional task that checks if those users' display name is Equal to 'Monica Luong', and if yes, unexpire their password and reactivate their account. Else, do nothing. This made up playbook would search for all the AD accounts whose passwords have expired. It would then check if 'Monica Luong' has an expired password for their AD account and unexpire it if that's the case. The next option, **Choose Automation** allows you to create a conditional task whose results are based on a script, either one you've written or one that's been written for you and has been tagged as 'Conditional'. An example of a pre-written automation script is BetweenDates. This script determines if the inputted value is between the 2 date times. It will return 'yes' or 'no' based on if the value is or isn't between those 2 dates. Lastly, is the **Manual** option for conditionals, which I myself have not used yet. However, it creates a conditional task which must be manually resolved by a user. For example, in an access incident investigation, you might ask the user if they attempted to access their account. A manual task checks if the user responded.

# **Next Week**
The next blog post will be a continuation of this one. Look forward to continue learning about XSOAR!

# **More Info**
[Cortex XSOAR](https://www.paloaltonetworks.com/cortex/cortex-xsoar)

[Cortex XSOAR Docs](https://xsoar.pan.dev/docs/concepts/getting-started-guide)

[Sub-playbook Loop](https://docs.paloaltonetworks.com/cortex/cortex-xsoar/6-0/cortex-xsoar-admin/playbooks/configure-a-sub-playbook-loop.html)

[Sub-playbook Tutorial](https://docs.paloaltonetworks.com/cortex/cortex-xsoar/6-0/cortex-xsoar-admin/playbooks/configure-a-sub-playbook-loop/sub-playbook-tutorial.html)

[Create a Conditional Task](https://docs.paloaltonetworks.com/cortex/cortex-xsoar/5-5/cortex-xsoar-admin/playbooks/playbook-tasks/create-a-conditional-task.html)