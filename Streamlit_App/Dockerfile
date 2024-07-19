FROM python:3.11.7
EXPOSE 8080


# Copy the requirements file into the container
#ADD packages.txt packages.txt

# Install system dependencies
RUN apt-get update \
    && apt-get install -y libgl1-mesa-glx \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ADD requirements.txt requirements.txt

# Increase the timeout value for pip and install the packages
RUN pip install --upgrade pip \
    && pip config set global.timeout 20000 \
    && pip install -r requirements.txt 
#    && pip install -r packages.txt

# Set the working directory in the container
WORKDIR /app3

# Copy the rest of the application code into the container
COPY . ./

# Install the requirements again if needed
#RUN pip install -r requirements.txt

# Define the entry point for the application
ENTRYPOINT ["streamlit", "run", "app.py", "--server.port=8080", "--server.address=0.0.0.0"]
