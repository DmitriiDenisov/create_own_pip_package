# Creating pip package

### Minimum instructions

1. Create an account in https://pypi.org/

2. Choose name for package that is available, i.e. check that nobody already taken it

3. Create such structure of files:

```
my_package
|-- setup.py
|-- src
|   |-- my_package.py
```

4. In `my_package.py` put some functions, like this one:

```
def say():
	print('QQ!')
```

5. In `setup.py` put this code:

```
from setuptools import setup

setup(
      name='helloworld_v1', # name of your package which will be used 
      version='0.1', # version of your package, you have to change it every time you upload something 
      description='Say hello!', # description of your package
      py_modules=["scripts"], # list of files from src directory. After installing we will call `from scripts import say`
      package_dir={'': 'src'} # this is needed as we have all our scripts in src directory
      )

```
