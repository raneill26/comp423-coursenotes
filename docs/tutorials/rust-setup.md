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

Begin by creating a repository on your local machine. A repository is a type of centrally located storage where you can keep your files. To create one, open up terminal on your local machine. Navigate to where you would like to store your repository and type the following command:

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
git commit -m "Initial commit with README"
```

!!! note 
    The first line of code creates the README with the text "Rust Tutorial". Then, the changes (a created file with additions to it) are added and commited to our local repository. In Part 2, you will set up a remote repository using GitHub, a website that is a powerful tool for storing, saving, and collborating on projects. 

### Creating a remote repository using GitHub

Log into your account on GitHub. Create a new repository [here](https://github.com/new), and fill in the following fields:

- Repository Name: ```rust-tutorial```
- Description: ```A Rust Tutorial to help me set up my own project```
- Visibility: Public
- Make sure the repository is not initialized with a README.md, .gitignore, or license. 

Once these conditions are met, click ```Create your repository```.

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
Open VSCode, and open the "rust-tutorial" directory. Navigate to the left of the screen and click Extensions. In the search bar, search for Dev Containers, and install it. After it installs, navigate back to the File Explorer, and create a new directory inside your project called ```.devcontainer```. Create a file inside of this directory titled ```devcontainer.json```. Enter the following code into this file:

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
Click ```Ctrl + Shift + P``` (or ```Cmd + Shift + P``` on Mac), and type "Dev Containers: Reopen in Container." This reopens your project inside the dev container we just set up. Now you should see a file called ```main.rs``` appear in your project's directory, where you will be coding. To ensure the dev container gives you access to the correct version of Rust, run rustc --version in your terminal. You should see the most recent version of Rust show up.

## Part 3: Coding in Rust
Rust projects are structured using ```cargo```, Rust's package manager. Lets walk through the commands needed to run your code

### Using ```cargo new``` to create a Rust Project
Instead of locally creating files, you can use Cargo to generate a Rust project structure. Run the following commands in the terminal:

```
cargo new rust_tutorial_project --bin --vcs none  
cd rust_tutorial_project  
```

This creates a project folder called ```rust_tutorial_project``` inside of your directory that includes the file ```main.rs```. This is where you will do the coding for your project. The ```--vcs none``` flag (vcs is short for Version Control System) is included because source control is not needed for this small project. 

### Writing your first program in Rust
Open your ```main.rs``` file and copy and paste the following code:

```
fn main() {
    println!("Hello COMP423");
}
```

In Rust, all of your code will be in functions, similar to Java. There are no parameters used in your function, so you will keep the parenthesis empty for this snippet. The code in your function will be inside curly braces. For this tutorial, we are printing a string using the Rust function println!(). To learn more advanced Rust functions, you can go to the offical Rust language website [here](https://www.rust-lang.org/learn)

Now it's time to run your program!

### Building and running your program
Rust has two ways of running its programs: with ```cargo build``` and ```cargo run```. We will walk through both options here:

#### Using ```cargo build```:
Navigate to the VSCode terminal and enter the following commands:
```
cargo build
./target/debug/rust_tutorial_project  
```

#### Using ```cargo run```:
Navigate to the VSCode terminal and enter the following commands:
```
cargo run
```

#### What do each of these commands do?
```cargo build```:

- This compiles your program into a executable, but does not run it 
- This is similar to the ```gcc``` command from COMP211, where the code is compiled into an executable that can run independently from its source
- After you use ```cargo build```, you then run the executable you created

```cargo run```:

- This compiles runs your program together based on the source code
    
**Congratulations! You have just completed the Rust project setup tutorial! For more information on the Rust programming language, visit the [Rust Website](https://www.rust-lang.org/)**