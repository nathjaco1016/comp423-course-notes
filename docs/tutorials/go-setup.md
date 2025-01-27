# Setting Up a Dev Container for Go

* Primary author: [Nathan Jacobs](https://github.com/nathjaco1016)
* Reviewer: [Arun Somasundaram](https://github.com/asomasu2)

## **Prerequisites**

The following is necessary for this tutorial:

* **Visual Studio Code**: We will use this as our code editor.
* **Docker**: This is what we use to run our development container.
* **VS Code Dev Container Extension**: A VS Code plugin that allows us to use dev containers.
* **Git**: Git is the version control which is necessary for the project.

<br>

## **Step 1**: Create Project Directory: :rocket:

Open a terminal and reate your project directory, and go into it with the following commands.

``` bash
mkdir go-project
cd go-project
```

<br>

## **Step 2**: Initialize Git Repo:

'git init' is the command you will type in the terminal that sets up git repository for your project.

``` bash
git init
```

Create a README file by typing this in the terminal:

``` bash
echo "# Go Dev Container" > README.md
git add README.md
git commit -m "Initial commit with README"
```

The next step is to navigate to github.com and login with your username and password. Once logged in, you should see a green "New" 
button next to "Top Repositories". Click the "New" button. 

You only need to fill in these details, do not do anything else:

- Repository Name: go-dev-container
- Description: "Setting up a go-dev-container"
- Visibility: Public

Click create repository, and add the GitHub repository by typing this in the same terminal you opened earlier

``` bash
git remote add origin https://github.com/<your-username>/go-dev-container.git
``` 
Insert your GitHub username where it says (your-username).

Check your default branch name with the subcommand "git branch" in the terminal. If the result is not *main, rename it to main with the following command: git branch -M main.

Push your local commits to the GitHub repository:

```bash
git push --set-upstream origin main
```

<br>

## **Step 3**: Create Dev Container:

The dev container allows us to have a consistent dev environment with all the necessary dependencies for our project.
To do this, follow these steps:

* Open VS Code
* Click File > Open > go-dev-container
* Make a folder called .devcontainer in your main project directory (go-project)
* Create a file called devcontainer.json inside the .devcontainer folder
* Add the following code to the devcontainer.json file:

``` json
{
    "name": "Go Dev Container",
    "image": "mcr.microsoft.com/devcontainers/go:latest",
    "customizations": {
        "vscode": {
            "settings": {
                "terminal.integrated.shell.linux": "/bin/bash"
            },
            "extensions": [
                "golang.go"
            ]
        }
    },
    "remoteUser": "vscode"
}
```

The 'image' uses the base microsoft image for go. This includes every dependency we need in our dev container.

<br>

## **Step 4**: Reopen the project in the new dev container

Follow these steps to open the project in our new dev container:

* Open the project folder in VS Code
* If a "reopen project in dev container" pops up, click it.
* If this does not pop up, do control (or command on mac) combined with shift and p, then type "Dev Containers: Reopen in dev container" and click this option.

<br>

## **Step 5**: Make a simple program

First, ensure that you have Go with the following code (in VS Code terminal):

``` bash
go version
```

This should output an up to date Go version.

Then, you need to make the Go module. This code uses the 'go mod' command to make the 'go.mod' file, which tracks dependencies for the project. Run this code in the terminal:

``` bash
go mod init github.com/<your-username>/go-project
```

Now, follow these steps to make your program:

* Create a file in your main directory called "main.go"
* Add the following code to the file, then save the file:

``` Go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```

You now have a simple Go program! Using the Println function from fmt (which we imported above), we are able to write a function in the function main (from the main package) that will print "Hello COMP423" when we run the file. 

<br>

## **Step 6**: Run the program

To run our program, simply type the following code and enter it in your terminal:

``` bash
go run main.go
```

This should print "Hello COMP423" into your terminal. If you see this, you successfully ran your program!

!!! note

    You should also try running your program using the build command. 'go build' makes a binary that we can execute many times, while 'go run' compiles and runs the program in a single step.

    ``` bash
    go build -o hello_comp
    ./hello_comp
    ```

## **Step 7**: Commit changes

Commit your work by running these commands:

``` bash
git add .
git commit -m "First commit, added our programming and set up dev container."
```

You then must push your changes to github to update the repository on there:

``` bash
git push -u origin main
```

## **Summary**

Now, you have a fully functional Go project with a program that runs on a dev container!

Let's look over what you did:

* You created a project directory
* You initialized a git repository
* You created and started a development container for your project
* You made and ran a Go program
* You updated your github repository from the command line

Now you can further develop your skills and create cool projects! :smile: