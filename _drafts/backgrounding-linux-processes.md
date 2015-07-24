---
layout: post
title:  "How to Background Console Processes"
date:   2015-07-23 8:00 AM
tags: [cli, linux]
---

Create a .sql file with your command (I've only tried this with a single command in a file)
------------------------------------------------------------
vi whatever.sql

Pipe the SQL file into mysql
Force the process into the background with CTRL+z and bg
------------------------------------------------------------
mysql -u root -p < whatever.sql
(enter password)
CTRL+z
bg (enter)

The process is still running now. You can see it with the following
------------------------------------------------------------
jobs

It appears as if you can just exit the console at this point and the query will continue running.
I tested this and didn't see any issues. But, you can also disown the job and then exit.
------------------------------------------------------------
jobs
(get the job ID from the console output)
disown -h %1
