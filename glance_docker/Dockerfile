FROM ubuntu:15.04
MAINTAINER tobe tobeg3oogle@gmail.com

RUN apt-get update -y

# Install tools
RUN apt-get install -y git
RUN apt-get install -y python-dev
RUN apt-get install -y python-pip
RUN apt-get install -y libmysqlclient-dev # For MySQL-python
RUN apt-get install -y libpq-dev # For pg_config
RUN apt-get install -y libffi-dev # For ffi.h
RUN apt-get install -y libxml2-dev # For xmlversion.h
RUN apt-get install -y libxslt-dev
RUN pip install python-glanceclient

ADD ./requirements.txt /etc/requirements.txt
RUN easy_install -U pip # For IncompleteRead
RUN pip install -r /etc/requirements.txt

# Get Glance
ADD . /usr/lib/glance
WORKDIR /usr/lib/glance

# Build Glance
#RUN easy_install -U pip # For IncompleteRead
#RUN pip install -r requirements.txt
RUN python setup.py install

RUN mkdir -p /var/log/glance/
RUN mkdir -p /etc/glance/
RUN cp -r ./etc/* /etc/glance/
ADD ./custom-glance-api.conf /etc/glance/glance-api.conf

RUN glance-manage db sync

EXPOSE 9292

CMD glance-api
