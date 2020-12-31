# robotology_docker
Dockerize the robotology-based development with vscode. A project to learn Docker.

A long-time goal is to ship robotics project based employing the [Robotology superbuild](https://github.com/robotology/robotology-superbuild), 
and avoid the "works on my machine" issue.

The idea is to develop code that is executable in a configured machine or 
just build the container using the [devcontainer](https://github.com/Giulero/robotology_docker/blob/main/.devcontainer) files 
and develop in an already configured environment.

Clone the project and open it in Visual Studio Code. It will build the container starting from the `.json` file

**or**

run in the terminal
```bash
docker build --build-arg USERNAME="your git user name" --build-arg USEREMAIL="your git email" --tag robotology_docker:$(date +%s) .devcontainer/
```

In the [Dockerfile](https://github.com/Giulero/robotology_docker/blob/main/.devcontainer/Dockerfile) some compilation flags are handled (for now no Matlab).

