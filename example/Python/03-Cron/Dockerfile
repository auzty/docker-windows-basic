FROM python:3.8-buster 

# create myapp dir
RUN mkdir /myapp

# add / copy current directory to /myapp
ADD . /myapp

# set default working directory
WORKDIR /myapp

# install requirements
RUN pip install -r /myapp/requirements.txt

# temporary sed for my own country
#RUN sed -i -e 's/deb.debian.org/kebo.pens.ac.id/g' /etc/apt/sources.list
# update and install cron package and deleting apt cache for saving docker images size
RUN apt-get update && apt-get install -y cron --no-install-recommends && rm -rf /var/lib/apt/lists/*

# Adding mycron to /etc/cron.d
RUN cp -f /myapp/mycron /etc/cron.d/mycron

# Adding mycron to crontab
RUN crontab /myapp/mycron

# set default command cron with foreground (-f)
CMD ["/usr/sbin/cron","-f","-l","-L","15"]