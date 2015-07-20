---
layout: post
title:  "Flushing DNS Cache on Mac OS X"
date:   2010-11-30 4:43 PM
tags: cli, "os x"
---
Introduction on what you will find below.

<!---
Review this before publishing!
http://osxdaily.com/2014/11/20/flush-dns-cache-mac-os-x/
--->

Flush DNS on OS X (10.10)
```
sudo discoveryutil udnsflushcaches
```

Flush DNS on OS X 10.9
```
dscacheutil -flushcache; sudo killall -HUP mDNSResponder
```

Flush DNS on OS X 10.7 and 10.8
```
sudo killall -HUP mDNSResponder
```

Flush DNS on OS X 10.5 and 10.6
```
sudo dscacheutil -flushcache (sudo may not be needed)
```

Flush DNS on OS X 10.4 and earlier
```
lookupd -flushcache
```