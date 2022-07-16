FROM python:slim-bullseye
### -------------------------------------------------
### Metadata information
### -------------------------------------------------
LABEL name="Python Automation"
LABEL maintainer="sydasif78@gmail.com"

### -------------------------------------------------
### Setup Python tooling
### -------------------------------------------------
RUN apt update 

### -------------------------------------------------
### Install Poetry to help with dependency management
### -------------------------------------------------
RUN pip install --upgrade pip \
&& pip install netmiko 

### -------------------------------------------------
### Caching dependencies
### -------------------------------------------------
WORKDIR /home

# Creating folders, and files for a project:
COPY app.py /home

