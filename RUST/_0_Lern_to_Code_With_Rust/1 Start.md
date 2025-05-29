[[_0 spis]]


# Source Code

- **source code**
	- is the code that developers write
	- is meant to be readable by humans
	- the computer cannot understand the Rust code itself
	- 



# Rust Compiler
- the Rust compiler is a program that translates our source code into an executable program
- the executable program is called a *binary* or *binary executable*
- the computer can understand and execute the instructions in the binary
- think of the computer like a translator


# `rustup`
- can update Rust (`rustup update`)
- can uninstall Rust (`rustup self uninstall`)
- can show documentations (`rustup doc`)
- 




# First project `cargo new hello_world`
`cargo new hello_word`

Rust project = Packages = Crates

```bash
$ cargo new hello_world 
    Creating binary (application) `hello_world` package
note: see more `Cargo.toml` keys and their definitions at https://doc.rust-lang.org/cargo/reference/manifest.html

```

## Two Types of Rust packages/crate
### binary crates -created by `cargo new`
- it is a standalone Rust application whose purpose is to be run by itself in isolation
- it is like a car (a fully functional piece of machinery that you are able to use automatically) 
### library crates
- it is one that exists to be used in other projects
- it is more like a tire or an engine

## `fn main()`

Rust will invoke the main function

**parameter** - it is a input to a function
`;` terminates 



# Tools to compile 
## One file  `rustc`

>[!info] kompilator `rustc`
> `rustc` to oficjalny kompilator, który zamienia:
> - Twój kod źródłowy (pliki *.rs*) 
> - w wykonywalny binarny program. 
> 
> Możesz go traktować jak odpowiednik *gcc* w świecie C/C++.
> 



## All project - `cargo build` or `cargo b`

### mode *debug*
It is **by default**
- fast
- unoptimized

the finial file is in `/target/debug/<project_name>`


### mode *release* `cargo build --release`
- longer to compile
- optimize for runtime performance 

the final file is in `/target/release/<project_name>`

### `cargo clean`
delete all of compiled executables


## `rustc` vs `cargo`
- `rustc` 
	- kompilator „niskiego poziomu”, 
	- kompiluje pojedynczy plik lub zestaw plików, 
	- nie radzi sobie sam z zależnościami czy zarządzaniem projektem.

- `cargo`
	- oficjalny menedżer projektów Rust, 
	- poza wywołaniem rustc automatycznie:
		- pobiera i kompiluje zależności z *crates.io*,
		- organizuje strukturę katalogów (`src/, Cargo.toml`),
		- udostępnia komendy 
			- `cargo build`, 
			- `cargo run`, 
			- `cargo test`
			- itp.



# Tools to format code
## For one file `rustfmt` 
`rustfmt <fileName>`

## For a project `cargo fmt`


# `cargo run` or `cargo r` = build + execute 
`cargo run` - build , run, give all metainfo
`cargo run --quiet` - build, run 



# `cargo check`
It checks the source code for any compile violations, but NOT PRODUCE AN ACTUAL EXECUTABLE  






































































