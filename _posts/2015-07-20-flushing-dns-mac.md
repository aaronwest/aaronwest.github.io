---
layout: post
title:  "Flushing DNS Cache on Mac OS X"
date:   2015-07-20 4:43 PM
tags: [cli, os x]
---
Below are the various Bash commands needed to flush DNS on Mac OS X. There are several different versions of the commands depending on which version of OS X in use. Ensure you are selecting the command appropriate for your OS. HT to [OSXDaily](http://osxdaily.com/2014/11/20/flush-dns-cache-mac-os-x/) for additional explanations on what is happening under the covers.

#### Flush DNS on OS X Yosemite 10.10.4 and Newer
When 10.11.x aka 'El Capitan' ships this command should continue to function. This set of commands will flush all DNS caches on OS X including Multicast DNS and Unicast DNS.

```bash
sudo dscacheutil -flushcache; sudo killall -HUP mDNSResponder
```

#### Flush DNS on OS X Yosemite 10.10 through 10.10.3
In these versions of OS X there are two separate commands to execute to clear the two difference DNS caches, Multicast DNS and Unicast DNS. You can run only one of these commands if you know which cache you are targeting or both if you prefer a more heavy-handed approach.

```bash
# Option 1: Clear Multicast DNS
sudo discoveryutil mdnsflushcache
# Option 2: Clear Unicast DNS
sudo discoveryutil udnsflushcaches
# Option 3: Concatenate both commands.
sudo discoveryutil mdnsflushcache; sudo discoveryutil udnsflushcaches
```

#### Flush DNS on OS X Mavericks 10.9
```bash
dscacheutil -flushcache; sudo killall -HUP mDNSResponder
```

#### Flush DNS on OS X Lion 10.7 and OS X Mountain Lion 10.8
```bash
sudo killall -HUP mDNSResponder
```

#### Flush DNS on OS X Leopard 10.5 and OS X Snow Leopard 10.6
```bash
sudo dscacheutil -flushcache
```

#### Flush DNS on OS X Tiger 10.4 and Earlier
```bash
lookupd -flushcache
```
