# pull official base image
FROM python:3.10.8-slim-buster

# set working directory
WORKDIR /usr/src/app

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install system dependencies
RUN apt-get update \
  && apt-get -y install netcat gcc \
  && apt-get clean

# install python dependencies
RUN pip install --upgrade pip
RUN pip install fastapi==0.85.1
RUN pip install uvicorn==0.19.0
#COPY ./requirements.txt .
#RUN pip install -r requirements.txt

# add app
COPY . .

# run the entrypoint
CMD ["uvicorn", "app.main:app", "--reload", "--host", "0.0.0.0", "--port", "8000", "--workers", "1"]
