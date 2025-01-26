# Setting up a dev container for Go

Welcome to this step-by-step guide for setting up a Go project in a Dev Container! By the end of this tutorial, you'll have a fully functional Go development environment and a simple program that prints "Hello COMP423."

* Primary author: [Logan Gatza](https://github.com/lrgatza)
* Reviewer: [Nicholas Nguyen](https://github.com/Nickn2137)

## Prerequisites 

!!! info "Required Installations"
    Ensure your machine has the following tools installed before starting this tutorial!

1. **Git**: [Install Git](https://git-scm.com/downloads).
- **Docker**: [Install Docker Desktop](https://www.docker.com/products/docker-desktop/).
- **VS Code**: [Download VS Code](https://code.visualstudio.com/).
- **Dev-Containers Extension**: Install in VS Code via `Ctrl+Shift+X`.
- **Command-Line Basics**: Familiarity with terminal commands and Git.


## Part 1: Project Setup: Creating the Repositiory

1. Open a Terminal and navigate to a file location where you would like to store your project.

2. Create a new directory for your project: 

    !!! note "Directory Name"
          In this tutorial, we are calling our project `go-project`. If you would like to name your project something else, replace `go-project` with your desired project name.

    ```bash
    $ mkdir go-project
    $ cd go-project
    ```

3. Initialize a new Git repository:
    ```bash
    $ git init
    ```

    !!! note "Note about GitHub"
        If you were adding your project to a remote github repository, you would do that here. However we are only covering setting up the local project and dev container in this tutorial.


## Part 2: Setting up the Development Environment

1. In VS Code, open the `go-project` directory. You can do this via: `File > Open Folder`.

2. Create a `.devcontainer` directory in the root of your project with the following file inside of this "hidden" configuration directory:
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

    The `devcontainer.json` file defines the configuration for your development environment. Here, we're specifying the following:

    - `name`: A descriptive name for your dev container.
    
    - `image`: The Docker image to use, in this case, the latest version of a Go environment. Microsoft maintains a collection of base images for many programming language environments, but you can also create your own!
    
    -  `customizations`: Adds useful configurations to VS Code, like installing the Go extension. When you search for VSCode extensions on the marketplace, you will find the string identifier of each extension in its sidebar. Adding extensions here ensures other developers on your project have them installed in their dev containers automatically.

4. Reopen the project in the VSCode Dev Container by pressing `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac), typing `Dev Containers: Reopen in Container`, and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

    Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running go version to see your dev container is running a recent version of Go without much effort! (As of this writing: go1.23.0 released in August of 2024.)

## Part 3: Creating a Hello World Program

1. Initialize go module

    In your Dev Container Terminal, run the following command to enable dependency tracking for your code:
    ```bash
    $ go mod init example/hello
    ```

2. Create a new file named `hello.go`, in which you will write the following code:

    ```go
    package main

    import "fmt"

    func main() {
        fmt.Println("Hello COMP423")
    }
    ```
3. To run your code, use the following command:

    ```bash
    $ go run .
    ```
    This should have an expected output of 
    
    ```bash
    "Hello COMP423"
    ```
    !!! note "`go run` vs `go build`"
        Alternatively you could also use the following sequence of commands: 
        ```bash
        $ go build -o hello
        $ ./hello
        ```
        
        This achieves the same output as the `run` command but in a slighlty different way.
        
        - The `go run` command compiles and runs the code in one action, utilizing a temporary binary file that is then automatically deleted.
        - The `go build` command produces a standalone exectutable (`hello`) that can then be run using `./hello`

## Conclusion

Congratulations! 
You have successfully created a Development Environment and run a program in Go! The skills you learned can be easily applied to more programs you create in the future! 

### Sources

- [423 MkDocs Tutorial](https://comp423-25s.github.io/resources/MkDocs/tutorial/)
- [Go Documentation](https://go.dev/doc/tutorial/getting-started)
