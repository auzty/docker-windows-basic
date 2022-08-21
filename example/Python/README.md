# Example Exercise 

## 01 - Simple Python

This directory contains basic python script without any dependencies, and then set the default command when container is created.

### how to build

dir : `01-Simple-Python`

> docker build -t simple-python .

### how to run

> docker run --rm simple-python

![sample-py](../../readme-resources/01-simple-py.jpg)

*notes :* the container will be execute `simple.py` and then exited. 

## 02 - Adding Pip

This directory contains python script that require NumPy dependencies, you must install or add it to make it run properly

### how to build

dir : `02-Adding-Pip`

> docker bild -t simple-python2 .

(if you want to test what dependencies that cause error, you can comment on dockerfile at line 13)

```dockerfile
#truncated...
# install requirements
RUN pip install -r /myapp/requirements.txt
#truncated...
```

### how to run

> docker run --rm simple-python

The output if you commented that line will be :

![sample-err](../../readme-resources/02-simple-py-err.jpg)

But if you're not commented, the result should be like this

![sample-ok](../../readme-resources/02-simple-py-ok.jpg)
