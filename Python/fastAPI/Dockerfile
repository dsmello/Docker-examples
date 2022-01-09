FROM python:3.9-buster

# Create the user and group non-root
# The user don't have home dir, password and is a system user
RUN adduser --no-create-home --disabled-password  app

# Copy the files to the container and change the working directory and change the owner
COPY --chown=app:app . /app

USER app
WORKDIR /app

# Create the virtual environment and update the pip
RUN python -m venv venv
RUN /app/venv/bin/python -m pip install --upgrade pip

# Install the requirements
RUN ./venv/bin/pip install -r requirements.txt

# Run the application 
# To run a fastAPI server in production, will be necessary to use a dedicated ASGI server, in our case 'uvicorn'
# The entrypoint is the main function of the application
ENTRYPOINT ["./venv/bin/uvicorn", "main:app" ]


# In this case we want to set the port to 8080, we will use the CMD to pass this parameter to the application
# That is a good thing, because to allow to the user override the parameter, if he wanted in runtime without changing the Dockerfile
CMD ["--port", "8080"]