---
layout: post
title: Debugging PostgreSQL
description:
date: 2021-11-04
image:
image_caption:
permalink: debugging-postgresql
tags: [postgresql]
---

## Where to find PostgreSQL logs

If you installed PostgreSQL through `brew` on MacOS, then the log is likely going to be in `/usr/local/var/log/postgres.log`.

You can tail the logs using:

```
tail -f /usr/local/var/log/postgres.log
```

If you installed a specific version of PSQL, then `brew services list` will likely contain something similar to:

```
➜  ~ brew services list
Name          Status  User     Plist
postgresql@13 started username /Users/username/Library/LaunchAgents/homebrew.mxcl.postgresql@13.plist
```

In this case, the log file will be in `/usr/local/var/log/postgresql@13.log`

## Lock file "postmaster.pid" already exists

If you see the following error:

```
2021-11-04 15:12:39.466 [2904] FATAL:  lock file "postmaster.pid" already exists
2021-11-04 15:12:39.466 [2904] HINT:  Is another postmaster (PID 455) running in data directory "/usr/local/var/postgresql@13"?
```

the fix is to simply remove the *pid* file and allow Postgres to restart:

```
➜  ~ rm /usr/local/var/postgresql@13/postmaster.pid
```
