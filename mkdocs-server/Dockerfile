FROM ubuntu:12.04
MAINTAINER tobe tobeg3oogle@gmail.com

RUN apt-get -y update

# Install mkdocs
RUN apt-get install -y python && \
    apt-get install -y python-pip && \
    pip install mkdocs

RUN mkdir /mkdocs
WORKDIR /mkdocs

EXPOSE 8000

CMD ["mkdocs", "serve"]