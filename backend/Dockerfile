# Use the official Ubuntu 22.04 as the base image
FROM ubuntu:22.04

# Install necessary packages
RUN apt-get update && \
    apt-get install -y python3.10 python3-pip && \
    apt-get clean

# Set the working directory
WORKDIR /backend

# Copy all files from the local "Backend" directory to the working directory in the container
COPY ./ /backend

# Install dependencies
RUN pip3 install -r /backend/requirements.txt

# Install gevent
RUN pip3 install gevent

# Download the Spacy model
RUN python3 -m spacy download en_core_web_sm

# Expose the Flask server port
EXPOSE 8000

# Start the Flask server using gevent WSGIServer
CMD ["python3", "/backend/run.py"]
