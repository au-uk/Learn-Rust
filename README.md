# Rust Aide-mémoire
 Following "The Book" ( https://doc.rust-lang.org/book/ and https://github.com/rust-lang/book/ ) while taking to notes to help me (and perhaps you) remember the what... "seemed important at the time, but is now sadly forgotten".

## Why Learn Rust

The Rust programming language is fundamentally about empowerment. From “systems-level” work without the exploits, crashes, or corruption. To CLI apps and web apps, with code quite pleasant to write.

Sounds Smashing... Lets give it a go.

## Step 1 (Installation)

I'm planning on using rustup (rather than brew) after reading a few discussions on the pros and cons ( https://users.rust-lang.org/t/best-way-to-install-rust-on-os-x-rustup-or-brew/6362 ).

rustup install process can be found here: https://www.rust-lang.org/tools/install (and in the book here https://doc.rust-lang.org/book/ch01-01-installation.html )

## Step 2 (Write, Compile and Run)

### Write the code

```
> cat main.rs
fn main() {
    println!("Hello, world!");
}
```
Notes:
- main is always the first function in a Rust program
- Any parameters, go inside the parentheses ()
- Good style to place the opening curly bracket on the same line as the function declaration, adding one space in between () {
- Rust style is to indent with four spaces, not a tab
- println! is a macro. If it was a function it would without the !
- Most lines of Rust code end with a semicolon

### Compile the code

```
> rustc main.rs
> ls
main	main.rs
>file main
main: Mach-O 64-bit executable x86_64
```

### Run the software

```
>./main
Hello, world!
```
## Cargo

Cargo is Rust’s build system and package manager
```
cargo --version
```

### Create a new project with Cargo

Most projects should be created using Cargo.

```
cargo new project-name
```
This will create the following, within a folder named "project-name".
```
>find .
.
./Cargo.toml
./src
./src/main.rs
```
Note:
- Cargo.toml includes software package version information and dependencies
- Packages of code are referred to as crates
- Cargo expects source files to live inside the ./src directory

### Compile a project with Cargo

Run cargo build from within the project directory. This will create a ./target directory with a number of files. ./target/debug/"project-name" is your compiled software.

Note:
- cargo build --release to compile it with optimisations
- cargo run - will compile the code and run the software
- cargo check - will ... check it compiles
- use // for comments


## Libraries, Functions, Macros and Variables

```
use std::io;                                    //This is a Library

fn main() {                                     //This is a function
    println!("Guess the number!");              //This is a macro

    println!("Please input your guess.");       //This is also a macro

    let mut guess = String::new();              //let makes the variable guess
                                                //mut makes guess mutable
                                                //so guess is a mutable variable
                                                //bound to a new, empty String
    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {}", guess);
}

```


Standard Library Documentation = https://doc.rust-lang.org/std/prelude/index.html
