# Base image for the docker container
FROM python:3.10-slim-buster
# Inside Container
# make new folder inside container
WORKDIR /backend-flask

# Outside Container --> Inside Container
# this contains the libraries we want to run the app with
COPY requirements.txt requirements.txt
# Insatall the python libraries  used for the app
RUN pip3 install -r requirements.txt

#  Outside Container --> Inside Container
# . means everything in the current directory
# First period . /backend-flask (Outside container)
# Second period . /backed-flask (Inside conatineer)
COPY . .

# Environment variables
# Inside Container and remain set when the container is running
ENV FLASK_ENV=developement

EXPOSE ${PORT}

# CMD --> Command
CMD [ "python3", "-m", "flask", "run", "--host=0.0.0.0", "--port=4567"]