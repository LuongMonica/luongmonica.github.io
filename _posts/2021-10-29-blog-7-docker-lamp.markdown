---
layout: post
title:  "Blog 7 - Docker-Compose: LAMP Stack pt.2"
date:   2021-10-29 9:59:31 -0700
categories: jekyll update
---

[comment]: <note>

# **Last Week**
In last week's blog post, I talked about what a LAMP stack is, what Docker and Docker-Compose are, and finally how to install Docker and Docker-Compose in preparation for this week's blog. Today we'll be going over a project I did that uses Docker-Compose to create a simple LAMP stack.

# **Walkthrough**
1. The first step you need to take is doing a clone of my git repository and going into the cloned directory.
```
git clone https://github.com/LuongMonica/docker-compose-lamp
cd docker-compose-lamp
```
Let's take a look at all the important files. First, there's `idtable.sql`. This is a very basic mysqldump file. It just has 1 database named 'cloudproject' and 1 table named 'idtable'. The table has a few dozen rows of numbers. At the end of the day, the only data that will be in it is just numbers 1 - X. 

Next, let's talk about `newid.php`. This file will be placed in the document root of our web server container. It connects to the mysql container, auto-increments the value, and displays that value when you look at the page. 

The `docker-compose.yml` already has comments that detail each of the important parts of the file. Basically, our Docker-Compose project has 2 services; one container is a web server and the other is a mysql database. The web server builds its image using the Dockerfile. It's linked to the database container using `links` and will wait for the mysql container to start before it is created using `depends_on`.

Finally the `Dockerfile`. It really only updates, installs apache and php packages, copies in the `newid.php` into the document root, and then has an entrypoint and runs the apache service.

2. 
```
# bring up the docker-compose application in detached mode (run in the background)
$ docker-compose up -d
# give it like 30 seconds to completely spin up and connect to the database
# then check if it works:
$ curl localhost:8080/newid.php
# OR view the page in the browser
# if you see a number displayed you did it!
# everytime you refresh the page or curl again, the value will be incremented
```

# **Next Week**


# **More Info**
