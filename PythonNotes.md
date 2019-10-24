# Python Helpers

## Python Process Stuck How to Debug:

(Thanks to https://gist.github.com/reywood/e221c4061bbf2eccea885c9b2e4ef496)

1. Ensure gdb is installed:
```
yum install gdb
```

2. Install pyrasite

```
pip install pyrasite
```

(included in the repo)

3. Find the pid of the stuck python process and run:

```
# Assuming process ID is 987
$ pyrasite-shell 987
```

And then run:

```
import sys, traceback
for thread_id, frame in sys._current_frames().items():
    print 'Stack for thread {}'.format(thread_id)
    traceback.print_stack(frame)
    print ''
```

For Instance:

```
sudo pyrasite-shell 25950
Pyrasite Shell 2.0
Connected to '/usr/bin/python /opt/tetration/oracle/src/Oracle.py --json_dir /opt/tetration/oracle/tetrules'
Python 2.7.5 (default, Jul 13 2018, 13:06:57)
[GCC 4.8.5 20150623 (Red Hat 4.8.5-28)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
(DistantInteractiveConsole)

>>> import sys, traceback
>>> for thread_id, frame in sys._current_frames().items():
...     print 'Stack for thread {}'.format(thread_id)
...     traceback.print_stack(frame)
...     print ''
```
