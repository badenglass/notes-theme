---
title: "Test Highlight"
date: 2022-08-26T22:29:10+08:00
draft: true
---

## Test for C
```c
#define UNICODE
#include <windows.h>
 
int main(int argc, char **argv) {
  int speed = 0, speed1 = 0, speed2 = 0; // 1-20
  printf("Set Mouse Speed by Maverick\n");
 
  SystemParametersInfo(SPI_GETMOUSESPEED, 0, &speed, 0);
  printf("Current speed: %2d\n", speed);
 
  if (argc == 1) return 0;
  if (argc >= 2) sscanf(argv[1], "%d", &speed1);
  if (argc >= 3) sscanf(argv[2], "%d", &speed2);
 
  if (argc == 2) // set speed to first value
    speed = speed1;
  else if (speed == speed1 || speed == speed2) // alternate
    speed = speed1 + speed2 - speed;
  else
    speed = speed1;  // start with first value
 
  SystemParametersInfo(SPI_SETMOUSESPEED, 0,  speed, 0);
  SystemParametersInfo(SPI_GETMOUSESPEED, 0, &speed, 0);
  printf("New speed:     %2d\n", speed);
  return 0;
}
```

## Test for Java

```java
import java.util.Map;
import java.util.TreeSet;
 
public class GetEnv {
  /**
   * let's test generics
   * @param args the command line arguments
   */
  public static void main(String[] args) {
    // get a map of environment variables
    Map<String, String> env = System.getenv();
    // build a sorted set out of the keys and iterate
    for(String k: new TreeSet<String>(env.keySet())) {
      System.out.printf("%s = %s\n", k, env.get(k));
    }
  }    
}
```

## Test for Python

```python
# test python (sample from offlineimap)
 
class ExitNotifyThread(Thread):
    """This class is designed to alert a "monitor" to the fact that a thread has
    exited and to provide for the ability for it to find out why."""
    def run(self):
        global exitthreads, profiledir
        self.threadid = thread.get_ident()
        try:
            if not profiledir:          # normal case
                Thread.run(self)
            else:
                try:
                    import cProfile as profile
                except ImportError:
                    import profile
                prof = profile.Profile()
                try:
                    prof = prof.runctx("Thread.run(self)", globals(), locals())
                except SystemExit:
                    pass
                prof.dump_stats( \
                            profiledir + "/" + str(self.threadid) + "_" + \
                            self.getName() + ".prof")
        except:
            self.setExitCause('EXCEPTION')
            if sys:
                self.setExitException(sys.exc_info()[1])
                tb = traceback.format_exc()
                self.setExitStackTrace(tb)
        else:
            self.setExitCause('NORMAL')
        if not hasattr(self, 'exitmessage'):
            self.setExitMessage(None)
 
        if exitthreads:
            exitthreads.put(self, True)
 
    def setExitCause(self, cause):
        self.exitcause = cause
    def getExitCause(self):
        """Returns the cause of the exit, one of:
        'EXCEPTION' -- the thread aborted because of an exception
        'NORMAL' -- normal termination."""
        return self.exitcause
    def setExitException(self, exc):
        self.exitexception = exc
    def getExitException(self):
        """If getExitCause() is 'EXCEPTION', holds the value from
        sys.exc_info()[1] for this exception."""
        return self.exitexception
    def setExitStackTrace(self, st):
        self.exitstacktrace = st
    def getExitStackTrace(self):
        """If getExitCause() is 'EXCEPTION', returns a string representing
        the stack trace for this exception."""
        return self.exitstacktrace
    def setExitMessage(self, msg):
        """Sets the exit message to be fetched by a subsequent call to
        getExitMessage.  This message may be any object or type except
        None."""
        self.exitmessage = msg
    def getExitMessage(self):
        """For any exit cause, returns the message previously set by
        a call to setExitMessage(), or None if there was no such message
        set."""
        return self.exitmessage
```

## Test for Bash

```bash
#!/bin/bash
cd $ROOT_DIR
DOT_FILES="lastpass weechat ssh Xauthority"
for dotfile in $DOT_FILES; do conform_link "$DATA_DIR/$dotfile" ".$dotfile"; done
 
# TODO: refactor with suffix variables (or common cron values)
 
case "$PLATFORM" in
    linux)
        #conform_link "$CONF_DIR/shell/zshenv" ".zshenv"
        crontab -l > $ROOT_DIR/tmp/crontab-conflict-arch
        cd $ROOT_DIR/$CONF_DIR/cron
        if [[ "$(diff ~/tmp/crontab-conflict-arch crontab-current-arch)" == ""
            ]];
            then # no difference with current backup
                logger "$LOG_PREFIX: crontab live settings match stored "\
                    "settings; no restore required"
                rm ~/tmp/crontab-conflict-arch
            else # current crontab settings in file do not match live settings
                crontab $ROOT_DIR/$CONF_DIR/cron/crontab-current-arch
                logger "$LOG_PREFIX: crontab stored settings conflict with "\
                    "live settings; stored settings restored. "\
                    "Previous settings recorded in ~/tmp/crontab-conflict-arch."
        fi
    ;;
```
## Test for HTML
```html
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html><head>
<title>A Tiny Page</title>
<style type="text/css">
<!--
      p { font-size:15pt; color:#000 }
    -->
</style></head><!-- real comment -->
<body bgcolor="#FFFFFF" text="#000000" link="#0000CC">
<script language="javascript" type="text/javascript">
      function changeHeight(h) {
        var tds = document.getElementsByTagName("td");
        for(var i = 0; i < tds.length; i++) {
          tds[i].setAttribute("height", h + "px");
      }}
</script>
<h1>abc</h1>
<h2>def</h2>
<p>Testing page</p>
</body></html>
```
## Test for CSS
```css
/*
Monokai style - ported by Luigi Maselli - http://grigio.org
*/
.hljs {
  display: block;
  overflow-x: auto;
  padding: 0.5em;
  background: #272822; color: #ddd;
}
.hljs-tag,
.hljs-keyword,
.hljs-selector-tag,
.hljs-literal,
.hljs-strong,
.hljs-name {
  color: #f92672;
}
.hljs-code {
  color: #66d9ef;
}
.hljs-class .hljs-title {
  color: white;
}
```
