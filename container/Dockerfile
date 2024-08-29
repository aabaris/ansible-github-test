FROM python:3.10-slim-bullseye

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      build-essential git && \
    apt-get clean -y

RUN mkdir -p /srv/ansible

COPY requirements.txt /srv/ansible/requirements.txt
COPY galaxy-requirements.yml /srv/ansible/galaxy-requirements.yml

RUN python3 -m venv /srv/ansible/env
RUN /srv/ansible/env/bin/pip install -r /srv/ansible/requirements.txt
RUN /srv/ansible/env/bin/ansible-galaxy install -r /srv/ansible/galaxy-requirements.yml
