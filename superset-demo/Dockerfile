FROM ubuntu:14.04

LABEL Description="Simple demo of superset"

ENV PORT 8080
ENV USERNAME admin
ENV PASSWORD admin
ENV FIRSTNAME admin
ENV LASTNAME admin
ENV EMAIL admin@bogus.com

RUN apt-get update && apt-get -y install build-essential libssl-dev libffi-dev python-dev python-pip libsasl2-dev libldap2-dev
RUN pip install --upgrade setuptools pip
RUN pip install superset
RUN fabmanager create-admin --app superset --username $USERNAME --password $PASSWORD --firstname $FIRSTNAME --lastname $LASTNAME --email $EMAIL
RUN superset db upgrade
RUN superset load_examples
RUN superset init

EXPOSE $PORT

ENTRYPOINT ["/usr/local/bin/superset", "runserver", "-p", $PORT]
