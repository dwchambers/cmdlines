# Python Commands

## Lists

**Add abc to end of list "name"**

`name.append("abc")`

**Delete last item of list "name**

`name.pop()`

**Remove abc from list "name"**

`name.remove("abc")`

**Insert abc into list "name" at position 5**

`name.insert(5, "abc")`

## Packages

**To create a distribution file and install the package**

1. Create a file setup.py with the following information:

```python
   from setuptools import setup
   
   setup(
       name='modulename',
       version='1.0'
       description='Write description here'
       author='David Chambers"
       url='github.com/dwchambers'
       py_modules=['modulename(s)']
   )
```

2. Create a file README.txt

3. Create a distribution file.

       py -3 setup.py sdist

4. Install the package.

       py -3 -m pip install modulename-1.0.zip`
       
       
