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

* `rand` is an **external crate (library/package)** used to generate random numbers or random thing.
* Add `rand` as a dependency in **`Cargo.toml`**:
* rand add cargo build or cargo add rand
```toml
[dependencies]
rand = "0.8.5" 
```
* 0 = Major
Purana code ya purane features ab naye version ke sath bina changes ke kaam nahi karenge. User ko apna code update karna padega.
* 8 = Minner
Sab kuch purane tareeqe se kaam karta rahega, bas kuch nayi functionality jud gayi hai.
* 5 = Patch
Koi naya feature add nahi hota aur na hi purana code break hota hai; sirf purani galtiyan/bugs theek kiye jate hain.


* rand :- rand ro paste karo with version dependence ke niche than cargo build run kar sare external liberary ko rust add kar deta hai 
* impotant point 0.8.5 ye change hoga too code mein bhi change ata hai matlab agar new version 0.10.8 ko like gaya too code mein bhi change aye ga 

* `rand = "0.8"` → Tells Cargo which version of the `rand` crate to use.



# Guessing Game — Complete Code(agar code chiye too scr mein hai)

### Imports

```rust
use std::cmp::Ordering;
* use std::cmp::Ordering; Rust ke standard library (std) se Ordering naam ke ek built-in Enum ko aapke program mein import karta hai, jiska use do values ko aapas mein compare (tulna) karne ke liye hota hai.
use std::io;
use rand::Rng;
```

* `Ordering` → Compares two values.
* `io` → Takes input from the user.
* `Rng` → Generates random numbers.

### Generate Secret Number

```rust
let secret_number = rand::thread_rng().gen_range(1..=100);
```

* Generates a random number between **1 and 100**.
* Stores it in `secret_number`.

### `loop`
* Guessing Game mein loop ka use isliye kiya jata hai taaki player ko baar-baar guess karne ka mauka mile jab tak woh sahi number na dhoondh le.
```rust
loop {
```

* Repeats the code again and again until `break`.

### Take User Input

```rust
let mut guess = String::new();

io::stdin()
    .read_line(&mut guess)
    .expect("Failed to read line");
```

* `guess` stores the user's input.
* `read_line()` reads the input.

### Convert Input to Number

```rust
let guess: u32 = match guess.trim().parse() {
    Ok(num) => num,
    Err(_) => continue,
};
```
* Rust mein u32 ek data type hai jiska matlab hota hai: Unsigned 32-bit Integer.
* u (Unsigned): Iska matlab isme sirf positive numbers (aur 0) store ho sakte hain. Isme negative (-) numbers allowed nahi hote or 32 (32-bit): Yeh memory mein 32 bits (yaani 4 bytes) jagah leta hai or range min = 0, max =2^32-1. 
* `trim()` → Removes extra spaces/newlineu (Unsigned): Iska matlab isme sirf positive numbers (aur 0) store ho sakte hain. Isme negative (-) numbers allowed nahi hote.

32 (32-bit): Yeh memory mein 32 bits (yaani 4 bytes) jagah leta hai..
* `parse()` → Converts the input from **String to number**.
* `Ok(num)` → Input is valid.
* `Err(_)` → Invalid input, so `continue` starts the loop again.

### Compare Guess

```rust
match guess.cmp(&secret_number) {
    Ordering::Less => println!("Too small!"),
    Ordering::Greater => println!("Too big!"),
    Ordering::Equal => {
        println!("You win!");
        break;
    }
}
```
* match mein sare outcome likna padta hai nahi too error show karega bool lika too true false both
* `Less` → Guess is too small.
* `Greater` → Guess is too big.
* `Equal` → Guess is correct → **You win!** → `break` stops the loop.

### Flow

**Generate number → Take guess → Convert to number → Compare → Repeat until correct**
