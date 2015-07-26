---
layout: post
title:  "How to Background Linux Console Processes"
date:   2015-07-26 1:30 PM
tags: [cli, linux]
---
This week our data team were talking about ways to run a Python script without having the execution attached to your console session. There's more than way one to accomplish this but here's the one they settled on.

```bash
nohup python python_script.py </dev/null &
```

The discussion reminded me of a similar, and equally useful, workflow we had a Dataium. We used all kinds of databases over the years but in the beginning MySQL 5.5.x was our goto. We operated a fairly sizable database which served as a backend to a desktop Adobe AIR / Flex application. One of the challenges we had with the configuration was performance following a database restart. We approached this problem by writing SQL scripts which mirrored common query patterns from our users. This concept of *warming the MySQL query cache* was incredibly useful.

When we first began testing the solution we were running the SQL code from Bash scripts. Several of the queries were fairly long running and having operators sit at their terminal waiting for the scripts to complete was less than desireable.

We got around this issue by _backgrounding_ the Bash scripts after we started them. Before I illustrate how we did this please realize there are additional ways to go about this. And we used them even to the point of automating the solution. In the beginning though we found this manual way to be perfectly fine until we had things working the way we wanted.

With a Bash script running in the terminal we forced it to the background using the following.

```bash
# Execute a bash script. After it is running press CTRL + z.
CTRL + z
# Next, press bg to background the process.
bg
```

Now, you can use your terminal session for other things. To see which processes have been backgrounded you can run this command:

```bash
jobs
```

Even though the script is running in the background it is still associated with the logged in terminal user. If you need to change this for some reason, lets imagine it's the end of day and you're heading home, you can view the list of running `jobs` to get the job ID from the list. Then, you can use the `disown` command to disown the process/job. This tells Linux not to send a SIGHUP to the job if your shell receives a SIGHUP.

```bash
jobs
(get the job ID from the console output)
disown -h %1
```
