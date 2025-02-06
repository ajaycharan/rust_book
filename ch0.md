## install
```bash
$ curl --proto '=https' --tlsv1.3 https://sh.rustup.rs -sSf | sh
$ rustc --version
```
## update
```bash
$ rustup update
```
## uninstall
```bash
$ rustup self uninstall
```
## create a code dir
```bash
$ mkdir -p ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```
## write and run programs
file: main.rs
```rust
fn main() {
    println!("hello");
}
```
Save the file and go to terminal
```bash
$ rustc main.rs
$ ./main
```
## Anatomy of rust program
```rust
fn main() {

}
```
Main fn is always the first code that runs in every executable rust program. Its args go in `()` (empty here) and its body is in `{}` 
### formatting
can be done using `rustfmt` that comes with `rustc`
### println!
Calls a rust macro: The `!` means a macro call.
    - had the call been `println("hello")` the it would've been function call
## compiling and running are separate steps
### compile
```bash
$ rustc main.rs
```
This outputs a binary executable: `main`

## Cargo
Build system and package manager for rust:
    - builds code
    - download the libs
    - building the libs
Makes easier to manage dependencies for rust code. Comes installed with rust.
```bash
$ cargo --version
```
### create a project
```bash
$ cargo new hello_cargo # creates Cargo.toml file, src dir in it 
# also makes a .gitignore in the hello_cargo dir, but that won't happen if I run cargo new in an existing git repo
$ cd hello_cargo
```
Cargo.toml
```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2021"

[dependencies]
```
#### package
section heading to indicate the package configuration info that cargo needs to compile the program.
    - edition: version of rust to use
#### dependencies
list dependencies
#### crates
Packages of code called crates in rust.

src/main.rs
```rust
fn main() {
    println!("hello");
}
```
### build project (default: debug build)
```bash
$ cargo build
```
Creates executable `target/debug/hello_cargo`

Also creates a new file at top level (when run 1st time): `Cargo.lock`
#### Cargo.lock
keeps track of exact version of dependencies in the project. Never need to change it manually.
### run the executable
```bash
./target/debug/hello_cargo
```
### compile and run
```bash
$ cargo run
```
compile and run the executable in one command
### check compilation but not produce executable
```bash
$ cargo check
```
Is faster to check program since exec building step not done
### release build
```bash
$ cargo build --release
```
creates exec in `target/release` vs `target/debug`
## work on any rust project
```bash
$ git clone rust.org/proj
$ cd proj
$ cargo build
```
