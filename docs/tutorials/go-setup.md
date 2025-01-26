# Setting up a dev container for Go

* Primary author: [Logan Gatza](https://github.com/lrgatza)
* Reviewer: [Nicholas Nguyen](https://github.com/Nickn2137)

## Prerequisites 

!!! info "Required Installations"
    Ensure your machine has the following tools installed before starting this tutorial!

- **Git**: [Install Git](https://git-scm.com/downloads)
- **Docker**: [Install Docker Desktop](https://www.docker.com/products/docker-desktop/)
- **VS Code**: [Download VS Code](https://code.visualstudio.com/)
- **Dev-Containers Extension**: Install in VS Code via `Ctrl+Shift+X`.
- **Knowledge of Command-Line Basics**


## Part 1: Project Setup: Creating the Repositiory

1. Open a Terminal and navigate to a file location where you would like to store your project.

2. Create a new directory for your project: 

    !!! note "Directory Name"
          In this tutorial, we are calling our project `go-project`. If you would like to name your project something else, replace `go-project` with your desired project name.

    ```bash
    mkdir go-project
    cd go-project
    ```

3. Initialize a new Git repository:
    ```bash
    git init
    ```

!!! note "Note about GitHub"
    If you were adding your project to a remote github repository, you would do that here. However we are only covering setting up the local project and dev container in this tutorial.


## Part 2: Setting up the Development Environment

1. In VS Code, open the `go-project` directory. You can do this via: `File > Open Folder`.

2. Create a .devcontainer directory in the root of your project with the following file inside of this "hidden" configuration directory:
    `.devcontainer/devcontainer.json`

3. Edit `devcontainer.json` to include the following:

    ```json
    {
        "name": "Go Dev Container",
        "image": "mcr.microsoft.com/devcontainers/go:latest",
        "features": {},
        "customizations": {
          "vscode": {
            "settings": {},
            "extensions": ["golang.go"]
          }
        }
    }
    ```

4. Reopen the project in the VSCode Dev Container by pressing `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac), typing `Dev Containers: Reopen in Container`, and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

    Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running go version to see your dev container is running a recent version of Go without much effort! (As of this writing: go1.23.0 released in August of 2024.)

## Part 3: Creating a Hello World Program



## Sources

- 423 tutorial
- go documentation
