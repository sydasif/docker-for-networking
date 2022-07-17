### -------------------------------------------------
# Use an official Python runtime as a parent image
### -------------------------------------------------
FROM python:slim-bullseye

### -------------------------------------------------
### Metadata information
### -------------------------------------------------
LABEL name="Python Automation"
LABEL maintainer="sydasif78@gmail.com"

### -------------------------------------------------
### Update Setup
### -------------------------------------------------
RUN apt update 

### -------------------------------------------------
### Install pip and netmiko
### -------------------------------------------------
RUN pip install --upgrade pip \
&& pip install netmiko 

### -------------------------------------------------
### Set the working directory to /home
### -------------------------------------------------
WORKDIR /home

### -------------------------------------------------
# Copy the app.py into the container home dir
### -------------------------------------------------
COPY app.py /home
