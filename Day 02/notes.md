# Guessing Game 
## New game bana raha hai guess wala
### Create the Project

```bash
cargo new guessing_game
```

* This creates a new Rust project.


```bash
cd guessing_game
```

### Guessing Game Code

```rust
use std::io;(this is external liberay code input output code)

fn main() {
    println!("Guess the number!");

    println!("Please input your guess.");

    let mut guess = String::new();
    * `mut is mutable means ye change kar sakta hai agar mut nahi likha too no change hoga` 
    * `string::new(empty) empty re space par hum string ki value rakta hai`
    * `ye string ko prelude value define hai ke ye string hai ise liye ye external liberay ka use nahi kiya hai but use std is not belog to prelude`

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");
    * io pehel likha tha too abe use kar sakta hai
    * stdin ka matlab hai standard input.
    * read_line() user ki poori line read karta hai.
    * &mut guess:- read_line() ko permission do ki woh user ka input guess ke andar likh sake. 
    * expect() check karta hai kiResult successful hai ya error agar succefull hai too continue.
    * if error ata hai than show failed to read line.

    println!("You guessed: {}",guess);
  
* `"You guessed: "` → Normal text.
* `{}` → Placeholder for a value(output store hoga).
* example show the guess use 
let x = 5;
let y = 10;
println!("x = {x} and y + 2 = {}", y + 2);
output X = 5;
Y = 12;


}
```


### Guessing Game Code(without explain)

```rust
use std::io;

fn main() {
    println!("Guess the number!");

    println!("Please input your guess.");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    println!("You guessed: {guess}");
}

### Important Points

* `use std::io;` → Imports Rust's **standard input/output library**.
* `let mut guess` → Creates a **mutable variable** to store the user's input.
* `io::stdin()` → Gets input from the user.
* `read_line(&mut guess)` → Reads the user's input and stores it in `guess`.
* `expect(...)` → Shows an error message if input reading fails.


### `rand` Crate

* `rand` is an **external crate (library/package)** used to generate random numbers.
* Add `rand` as a dependency in **`Cargo.toml`**:
* rand add cargo build or cargo add rand
```toml
[dependencies]
rand = "0.10.2" 
```
* 0 = Major
Purana code ya purane features ab naye version ke sath bina changes ke kaam nahi karenge. User ko apna code update karna padega.
* 8 = Minner
Sab kuch purane tareeqe se kaam karta rahega, bas kuch nayi functionality jud gayi hai.
* 5 = Patch
Koi naya feature add nahi hota aur na hi purana code break hota hai; sirf purani galtiyan/bugs theek kiye jate hain.


* rand :- rand re paste karo with version than dependence ke niche than cargo build run kar sare external liberary ko rust add kar deta hai
* `rand = "0.8"` → Tells Cargo which version of the `rand` crate to use.
