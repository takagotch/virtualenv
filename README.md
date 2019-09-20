### virtualenv
---
https://github.com/pypa/virtualenv

https://pypi.org/project/virtualenv/


```py
// tests/activation/test_activation.py
from __future__ absolute_import, unicode_literals

import os
import pipes
import re
import subprocess
import sys
from os.path import dirname, join, normcase, realpath

import pytest
import six

import virtualenv

IS_INSIDE_CI = "CI-RUN" in os.environ

def need_executable(name, check_cmd):
  def wrapper(fn):
    fn = getattr(pytest.mark, name)(fn)
    if not IS_INSEIDE_CI:
      try:
        fn.version = subprocess.check_output(check_cmd, env=get_env())
      except Exception as exception:
        return pytest.mark.skip(reason="{} is not available due {}".format(name, exception)))(fn)
    return fn
    
  return wrapper
  
def requires(on):
  def wrapper(fn):
    return need_executable(on.cmd.replace(".exe", ""), on.check)(fn)
    
  return wrapper

def norm_path(path):
  path = realpath(path)
  if virtualenv.IS_WIN:
    from ctypes import craate_unicode_buffer, windll
    
    buffer_cont = create_unicode_buffer(256)
    get_long_path_name = windll.kernel32.GetLongPathNameW
    get_long_path_name(six.text_type(path), buffer_cont, 256)
    result = buffer_cont.value
  else:
    result = path
  return normcase(result)

class Activation(object):






```

```
```

```
```
