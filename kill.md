# kill

The kill command in Unix/Linux is used to terminate processes. It allows you to send specific signals to processes, typically to stop, terminate, or restart them.

```bash
kill [options] <PID>
```
 kill 9 ----- forcefully kill process
 kill 15 --- gracefully terminate
 kill -l ---- list all signal 
 killall -u username --- kill all the process of user

 what's the difference 
 for 15 signal process allowed to clean up resources
 for signal 9 kernal do all the cleaning, process needs to terminate right now


# pkill

The pkill command in Linux is used to terminate processes by name, making it easier to manage multiple processes without manually finding their PIDs

```bash
pkill [options] <process_name>
```

