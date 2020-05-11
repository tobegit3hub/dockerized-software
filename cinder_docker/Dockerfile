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
RUN pip install tox
RUN pip install python-cinderclient

# Initialize lvm
RUN apt-get install -y lvm2

# Get Cinder
ADD . /usr/lib/cinder
WORKDIR /usr/lib/cinder

# Build Cinder
RUN easy_install -U pip # For IncompleteRead
RUN pip install -r requirements.txt
RUN python setup.py install

RUN tox -egenconfig
RUN mkdir -p /var/log/cinder/
RUN mkdir -p /etc/cinder/
RUN mkdir /var/lib/cinder
RUN cp -r ./etc/cinder/* /etc/cinder/
RUN mv /etc/cinder/cinder.conf.sample /etc/cinder/cinder.conf
RUN mv /etc/cinder/logging_sample.conf /etc/cinder/logging.conf

RUN cinder-manage db sync

EXPOSE 8776

CMD cinder-all
