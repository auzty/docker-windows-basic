FROM python:3.8-buster 

# create myapp dir
RUN mkdir /myapp

# add / copy current directory to /myapp
ADD . /myapp

# set default working directory
WORKDIR /myapp

# install requirements
RUN pip install -r /myapp/requirements.txt

# set default command when container running
CMD ["python","/myapp/sample-2.py"]