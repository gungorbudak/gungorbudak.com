---
author: Güngör Budak
date: '2015-08-30T06:13:00.001+03:00'
slug: simple-way-of-pythons-subprocesspopen
tags:
- subprocess
- popen
- pipe
- python
- popen with timeout
title: Simple Way of Python's subprocess.Popen with a Timeout Option
year: '2015'
---

<a href="https://docs.python.org/2/library/subprocess.html" target="_blank">subprocess</a> module in Python provides us a variety of methods to start a process from a Python script. We may use these methods to run an external commands / programs, collect their output and manage them. An example use of it might be as following:

```python
from subprocess import Popen, PIPE


p = Popen(['ls', '-l'], stdout=PIPE, stderr=PIPE)
stdout, stderr = p.communicate()
print stdout, stderr
```

These lines can be used to run `ls -l` command in Terminal and collect the output (standard output and standard error) in `stdout` and `stderr` variables using communicate method defined in the process.

However, if the ls command never ends, we will never get any output because the external program just hangs. This happens sometimes with some programs e.g. trying to generate 3D molecule from 2D MOL file using Open Babel when the MOL file is not correctly formed. As the Open Babel just tries to generate 3D and doesn't check if the MOL file is okay, we never get an output from that run. So the program and our script hang.

Python has many different options to solve this problem like using `multiprocessing` or `threading` module, signal module etc. But here I'll describe a very simple method that worked for me fine. This is tested in Linux environment with Python version 2.7.

**popen_timeout.py**

```python
from time import sleep
from subprocess import Popen, PIPE


def popen_timeout(command, timeout):
    p = Popen(command, stdout=PIPE, stderr=PIPE)
    for t in xrange(timeout):
        sleep(1)
        if p.poll() is not None:
            return p.communicate()
    p.kill()
    return False

print popen_timeout(['python',
                    '/home/gungor/Desktop/test.py'], 25)
```

**test.py**

```python
import time


for i in xrange(10):
    time.sleep(2)
    print "Gungor", i
```

Example run 1 where the external program doesn't exceed the timeout threshold

```bash
gungor@gungors-mint ~/Desktop $ python popen_timeout.py
('Gungor 0\nGungor 1\nGungor 2\nGungor 3\nGungor 4\nGungor 5\nGungor 6\nGungor 7\nGungor 8\nGungor 9\n', '')
```

In this example, I ran popen_timeout.py with 25 seconds timeout on an external program (test.py) which runs for 20 seconds and outputs lines of strings to the standard output which are collected with communicate method by popen_timeout.py.

Example run 2 where the external program would take longer than the timeout threshold

```bash
gungor@gungors-mint ~/Desktop $ python popen_timeout.py
False
```

The popen_timeout.py just returns False. Because the external program was still running when the timeout has been achieved and it has been killed afterwards.

You can use this method to control the execution of the external programs in Python.
