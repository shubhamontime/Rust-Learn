# Rust File Extension

* Rust source code files use the **`.rs`** extension.
* Example: `main.rs`

# Print Hello World in Rust

**File name:** `main.rs`

```rust
fn main() {
    println!("Hello world!");
}
```

### Compile the code

<u>Command:</u>

```bash
rustc main.rs
```

### Run the code

<u>Command:</u>

```bash
./main
```

**Flow:** Write code → Compile → Run

# Rust Formatting(code ke style ko likne ke liye)
**`rustfmt`** is used to format Rust code in a standard style.

<u>Command:</u>

```bash
rustfmt main.rs
```

**Purpose:** Makes the code clean and properly formatted.

### `println!`

* `println!` is called a **macro** in Rust.
* The `!` tells Rust that it is a **macro**.
* If you remove `!`, it becomes `println()` and gives a **compiler error**.

```rust
println!("Hello, world!");  // Correct
```

```rust
println("Hello, world!");   // ❌ Error
```
# Semicolon `;` in Rust

* Most statements in Rust end with a **semicolon `;`**.
* Example:

```rust
println!("Hello, world!");
```

* `;` tells Rust that the **statement is finished**.

### Rust Binary(share code with anyone he not install rust but he can run the code)

* Write your Rust code.
* Compile it into a **binary(send this binary with anyone)**.
* Command:

```bash
cargo build --release
```
```
you get:- target/release/my_program(this is binary)
```
* Send the binary to another person.
* They can run it **without installing Rust**.
* The binary usually works only on the 
**same OS/platform**
**mac=mac**
*window=window*
***the person only see the result not see the main code*** 

# Cargo(we use cargo when code is large to compile)

* **Cargo** is Rust's **package manager and build tool** (like `npm` in JavaScript).

### Create a New Project

```bash
cargo new hello_cargo
```

This creates:

```text
hello_cargo/
├── Cargo.toml
└── src/
    └── main.rs
```

### `Cargo.toml`

`Cargo.toml` tells Cargo **about your project**.

```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2024"
```

* `name` → Project name
* `version` → Project version
* `edition` → Rust edition used by the project

### `src/`

* `src/` =main.rs (jo main code hai use ko likta hai)
* `main.rs` is the main Rust source file.

### Use of Cargo new hello_cargo

* `cargo new hello_cargo`(larger code ko compile karna kr liye use hota hai).
* `cargo build` (this command run in the terminal than code compile).

### `cargo build`

* First, go inside the project folder:

```bash
cd hello_cargo
```

* (hello_cargo ko select karna than cargo build run karna):

```bash
cargo build
```

* The compiled binary is created inside:

```text
target/debug/hello_cargo
```

* To run the binary:

```bash
./target/debug/hello_cargo or cargo run(both command work)
```

**Note:** The binary name is usually the same as the project name.

