# syntax=docker/dockerfile:1
FROM alpine:latest
LABEL maintainer="Jaemyeong Jin jaemyeong@me.com"

# install required packages
RUN apk add --update --no-cache \
    bash curl nano vim wget git openrc \
    gcc openssl-dev libffi-dev musl-dev linux-headers cargo pkgconfig \
    python3 python3-dev py3-pip

# create directory & copy source code & set working directory
RUN mkdir -p /repos/jaemyeong/HomeNetwork/Bestium
COPY . /repos/jaemyeong/HomeNetwork/Bestium
WORKDIR /repos/jaemyeong/HomeNetwork/Bestium

# create & activate python virtual environment, install python requirements
RUN /bin/bash -c "source ./bootstrap.sh"
RUN python3 clean.py

# expose default web server port (todo: dynamic expose?)
EXPOSE 7929

# activate python venv and launch application
CMD /bin/bash -c "source ./activate.sh; python3 app.py; /bin/bash"
