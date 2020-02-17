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

6. Execute: 

``` python3 setup.py bdist_wheel ```

This will create some additional files, including `dist/newhello-0.1-py3-none-any.whl`

7. Execute:

``` twine upload dist/* ```
If twine is not installed, then execute `pip install twine`

**For every next twine uploading we need to specify which wheel package we are going to upload. For example: **

`twine upload dist/newhello-0.0.1-py3-none-any.whl`

8. Example can be found in `helloworld_v1` folder, just rename name in `setup.py` and follow 6, 7
