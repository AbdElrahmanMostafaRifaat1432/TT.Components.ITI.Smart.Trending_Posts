FROM python:3.10
EXPOSE 8080

# Copy the requirements file into the container
ADD requirements.txt requirements.txt

# Increase the timeout value for pip and install the packages
RUN pip install --upgrade pip \
    && pip config set global.timeout 7000 \
    && pip install -r requirements.txt

# Set the working directory in the container
WORKDIR /app3

# Copy the rest of the application code into the container
COPY . ./

# Install the requirements again if needed
#RUN pip install -r requirements.txt

# Define the entry point for the application
ENTRYPOINT ["streamlit", "run", "app.py", "--server.port=8080", "--server.address=0.0.0.0"]
