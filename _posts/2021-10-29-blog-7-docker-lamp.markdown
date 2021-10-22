---
layout: post
title:  "Blog 7 - Docker-Compose: LAMP Stack pt.2"
date:   2021-10-29 9:59:31 -0700
categories: jekyll update
published: false
---

[comment]: <note>

# **Last Week**


# **Walkthrough**

```
# clone my github repo that contains all the necessary files
$ git clone https://github.com/LuongMonica/docker-compose-lamp
$ cd docker-compose-lamp
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
