# Setting up a dev container for Rust

* Primary author: [Ryan Neill](https://github.com/raneill26)
* Reviewer: [Julia Guzzo](https://github.com/jkguzzo)

In this tutorial, you'll learn how to begin your own project using the programming langugage Rust. Rust is an all purpose programming language used throughout all areas of programming. Before beginning your journey, ensure you have met all the prerequisites listed below.

## Prerequisites

1. A GitHub Account: If you don't have one, sign up at [GitHub](https://github.com)
2. Git installed: Install [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don’t already have it.
3. Visual Studio Code (VS Code): Download and install it from [here](https://code.visualstudio.com/).
4. Docker installed: Required to run the dev container. Get Docker [here](https://www.docker.com/products/docker-desktop/).
5. Command-line basics: A basic understanding of command-line and navigating through your terminal

## Part 1: Setting up your project
### Creating your local repository

Begin by creating a repository on your local machine. A repository is a type of centrally located storage where you can keep your files. Do create one, open up terminal on your local machine. Navigate to where you would like to store your repository and type the following commands:

```
mkdir rust-tutorial
```

In the future, you may name this whatever you like, but for the purposes of this tutorial, we will use "rust-tutorial". Now, lets move into this directory:

```
cd rust-tutorial
```

Now, initialize a new git repository inside this directory using the following command:

```
git init
```

Lastly, create a README.md file for your repository. This file will contain a general overview of your project as a point of reference for other contributers unfamilar with your code. 

```
echo "# Rust Tutorial" > README.md 
git add README.md
git commit -m “Initial commit with README”
```

The first line of code creates the README with the text "Rust Tutorial". Then, the changes (a created file with additions to it) are added and commited to our local repository. In Part 2, you will set up a remote repository using GitHub, a website that is a powerful tool for storing, saving, and collborating on projects. 

### Creating a remote repository using GitHub

Log into your account on GitHub. Create a new repository [here](https://github.com/new), and fill in the following fields:

- Repository Name: ```rust-tutorial```
- Description: ```A Rust Tutorial to help me set up my own project```
- Visibility: Public
- Make sure the repository is not initialized with a README.md, .gitignore, or license. 

Create your repository.

### Connecting your local and remote repositories
Return to the terminal on your local machine and ensure you are still in your local repository. To connect your repositories, run the following command:

```
git remote add origin https://github.com/<your-username>/rust-tutorial.git
```

The default branch name should be ```main```. Ensure this is correcting using ```git branch```. If the default branch isn't named 'main', rename it to main using the following command:

```
git branch -M main  
```

Now, push your changes from your local repository to your remote repository. Remember, you have already added and commited your changes. All you need to do now is push them using the following command: 

```
git push --set-upstream origin main
```

Confirm your repositories are linked by navigating to your GitHub repository to confirm the changes were pushed.

## Part 2: Configuration of Dev Containers
A "dev container" is a Docker container specifically configured to provide a fully featured development environment. This makes collaboration with partners easy, as all collaboraters work in a uniform environment. 

### Configure your container
Open VSCode, and open the "rust-tutorial" directory. Naviagte to the left of the screen and click Extensions. In the search bar, search for Dev Containers, and install it. After it installs, navigate back to the File Explorer, and create a new directory inside your project called ```.devcontainers```. Create a file inside of this directory titled devcontiner.json. Enter the following code into this file:

```
{
  "name": "Rust Tutorial",
  "image": "mcr.microsoft.com/vscode/devcontainers/rust",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": [
        "rust-lang.rust-analyzer"
      ]
    }
  },
  "postCreateCommand": "cargo init --bin --name hello_423 && touch main.rs"
}
```

This code does the following: 

- Creates a name of your container
- Specifies the docker image to use
- Customizes programming languages and extensions
- Runs a command everytime the dev container is built
- Gives users the latest version of Rust

### Reopen the Project in a VSCode Dev Container
Click ```Ctrl + Shift + P``` (or ```Cmd + Shift + P``` on Mac), and type "Dev Containers: Reopen in Container." This reopens your project inside the dev container we just set up. Now you should see a file called ```main.rs``` appear in your project's directory, where you will be coding. 

## Part 3: Coding in Rust
Copy and paste the following code into your ```main.rs```:

```
fn main() {
    println!("Hello COMP423");
}
```

Save the file, and reopen your dev container. Now it's time to run your program!

### Running your program
To run your program, enter the following code in your VSCode terminal: 

```
rustc main.rs
./main
```

Here is a breakdown of what this accomplishes:

- ```rustc main.rs```: This compiles your program
- ```./main```: This runs your program


**Congratulations! You have just completed the Rust project setup tutorial!**