# Python: A demo project to show how to conteinerize your code

This is a simple project with one module and a REST server using the FastAPI framework.

Our Dockerfile will do the following steps:
- Create a user and group non-root.  # It's not necessary to do this, but it's good to do it.
- Change the runnin user to the user created.
- Copy files from this project folder to the container.
- Install dependencies (Pip install -r requirements.txt) 
- Add the entrypoint to the Dockerfile


## Who is this for?
For beginners who want to learn how to conteinerize your code.

## how to build and run.
- Build the Dockerimage:
```bash
docker build -t my_docker_app:python .
```

- Run the Dockerimage:
```bash
docker run --rm --name=my_docker_app -p 8080:8080 my_docker_app:python
```