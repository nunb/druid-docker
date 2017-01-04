FROM ubuntu:14.04

RUN apt-get update && apt-get -y install build-essential libssl-dev libffi-dev python-dev python-pip libsasl2-dev libldap2-dev

RUN pip install --upgrade setuptools pip

RUN pip install superset

RUN fabmanager create-admin --app superset

RUN superset db upgrade
RUN superset load_examples
RUN superset init
RUN superset runserver -p 8080
CMD ["superset", "runserver", "-p", "8080"]
