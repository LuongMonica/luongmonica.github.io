---
layout: post
title:  "Blog 7 - Docker-Compose: LAMP Stack pt.2"
date:   2021-10-29 9:59:31 -0700
categories: jekyll update
---

# **Last Week**
In last week's blog post, I talked about what a LAMP stack is, what Docker and Docker-Compose are, and finally how to install Docker and Docker-Compose in preparation for this week's blog. Today we'll be going over a project I did that uses Docker-Compose to create a simple, 2-tiered LAMP stack. (A 2 tier architecture, if you aren't aware, is simply when the data and application layers are separated. In this case, it means we are creating 1 container that's the database and 1 container that's the application.)

# **Walkthrough**
**1.** The first step you need to take is doing a clone of [my git repository](https://github.com/LuongMonica/docker-compose-lamp) and going into the cloned directory.
```
git clone https://github.com/LuongMonica/docker-compose-lamp
cd docker-compose-lamp
```

Let's take a look at all the important files. First, there's `idtable.sql`. This is a very basic mysqldump file. It just has 1 database named 'cloudproject' and 1 table named 'idtable'. The table has a few dozen rows of numbers. At the end of the day, the only data that will be in it is just numbers 1 - X. 

Next, let's talk about `newid.php`. This file will be placed in the document root of our web server container. It connects to the mysql container, auto-increments the value, and displays that value when you look at the page. 

The `docker-compose.yml` already has comments that detail each of the important parts of the file. Basically, our Docker-Compose project has 2 services; one container is a web server and the other is a mysql database. The web server builds its image using the Dockerfile. It's linked to the database container using `links` and will wait for the mysql container to start before it is created using `depends_on`.

Finally the `Dockerfile`. It really only updates, installs apache and php packages, copies in the `newid.php` into the document root, and then has an entrypoint which runs the apache service in detached mode in the foreground.

**2.** Now that we know what each file in the repo is for and does, we can use Docker-Compose to create our project.
```
# bring up the docker-compose application in detached mode (run in the background)
$ docker-compose up -d
```

![Docker Compose Command Output](/assets/docker-compose-lamp-ss.jpg)<br/><font size="2.75px"><em>Output of 'docker-compose up -d'</em></font>

This can take a little while (few minutes) to complete since it needs to pull and build the mysql image (if you don't already have one), pull and build the ubuntu image, update the package lists of the web container, and finally install the apache and php packages.

Once it's finished, you'll see 2 lines that say `Creating mysql ... done` and `Creating webserver ... done`. These are the names of our 2 containers.

**3.** Now that our containers are created and they are in the same network, courtesy of Docker-Compose, let's test out our application!
```
curl localhost:8080/newid.php
# everytime you curl again, the value will be incremented
```

![Curl](/assets/docker-compose-curl-ss.jpg)<br/><font size="2.75px"><em>Output of curl command</em></font>

You can also access it in your browser by going to the same URL `localhost:8080/newid.php`. Everytime you refresh the page, the value will be incremented.

![Browser](/assets/docker-compose-browser-ss.jpg)<br/><font size="2.75px"><em>Application in the browser</em></font>

![Browser Refresh](/assets/docker-compose-browser-refresh-ss.jpg)<br/><font size="2.75px"><em>After refresh</em></font>

> &#128216; **Note:** If you get an error like the one below, the application is not able to connect to the database. In most cases, this is just because it hasn't gotten the chance to yet. Give it like 30 seconds to completely spin up and connect to the database before you try again.

![Curl Error](/assets/docker-compose-curl-error.jpg)<br/><font size="2.75px"><em>Error output of curl command</em></font>

**4.** If you want to stop: `docker-compose down`

![Docker-compose down](/assets/docker-compose-down.jpg)<br/><font size="2.75px"><em>Output of 'docker-compose down'</em></font>

# **Next Week**
Thanks for following along with this post. I hope you learned something cool! I'm not sure what my next blog will be about, but stay tuned! I might talk about JavaScript and MEAN/MERN/MEVN stacks. 

# **More Info**
[Docker Docs](https://docs.docker.com/)

[Docker Compose Overview](https://docs.docker.com/compose/)