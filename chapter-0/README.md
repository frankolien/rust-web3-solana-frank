# Chapter 0: Rust Fundamentals Bootcamp 🦀

```sh
+---------------------------------------------------------------------+
|                     RUST FUNDAMENTALS BOOTCAMP                      |
+---------------------------------------------------------------------+
|                                                                     |
|   Variables & Types ──> Control Flow ──> Ownership & Borrowing      |
|         |                    |                    |                  |
|         v                    v                    v                  |
|   Structs & Enums ──> Error Handling ──> Traits & Generics          |
|         |                    |                    |                  |
|         v                    v                    v                  |
|   Collections ──────> Iterators & Closures ──> Modules & Crates     |
|                              |                                      |
|                              v                                      |
|                    Ready for Solana! 🚀                             |
|                                                                     |
+---------------------------------------------------------------------+
```

## Table of Contents

* [**Introduction**](#introduction)
    * [**1. Hello, Rust! 👋**](#1-hello-rust-)
    * [**2. Variables & Mutability 📦**](#2-variables--mutability-)
    * [**3. Data Types 🔢**](#3-data-types-)
    * [**4. Functions 🔧**](#4-functions-)
    * [**5. Control Flow 🚦**](#5-control-flow-)
    * [**6. Ownership & Borrowing 🏠**](#6-ownership--borrowing-)
    * [**7. Structs 🏗️**](#7-structs-)
    * [**8. Enums & Pattern Matching 🎯**](#8-enums--pattern-matching-)
    * [**9. Error Handling ⚠️**](#9-error-handling-)
    * [**10. Collections 📚**](#10-collections-)
    * [**11. Traits & Generics 🧬**](#11-traits--generics-)
    * [**12. Iterators & Closures 🔄**](#12-iterators--closures-)
    * [**13. Lifetimes 🕐**](#13-lifetimes-)
    * [**14. Modules, Crates & Cargo 📦**](#14-modules-crates--cargo-)
    * [**15. Common Standard Library Types 🧰**](#15-common-standard-library-types-)
    * [**16. Macros 🪄**](#16-macros-)
* [**Conclusion**](#conclusion)

## Introduction

Welcome to **Chapter 0** — the prerequisite chapter of this series! Before we dive into the thrilling world of [**Web3**](https://en.wikipedia.org/wiki/Web3) and [**Solana**](https://solana.com) development, we need to build a rock-solid foundation in [**Rust**](https://www.rust-lang.org/), the programming language that powers Solana's blazing-fast runtime.

Rust is not just another programming language. It's a systems programming language that guarantees **memory safety** without a garbage collector, achieves **fearless concurrency**, and delivers performance on par with C and C++[^1]. These are the exact properties that make it the language of choice for building secure and high-performance blockchain infrastructure like Solana.

This chapter is designed as a **complete Rust bootcamp from scratch**. We assume zero Rust knowledge. By the end, you will have mastered every Rust concept you'll need to understand the Solana code in Chapters 1 through 5. We'll cover everything from variables and types, through Rust's unique ownership system, all the way to traits, generics, and macros — with tons of hands-on examples along the way.

Think of this chapter as your **training grounds** before stepping onto the battlefield. Every warrior sharpens their blade before battle, and every Solana developer masters Rust before touching the blockchain. Let's begin! 🦀

[^1]: https://www.rust-lang.org/

---

### 1. Hello, Rust! 👋

Every programming journey begins with a single step — and in Rust, that step is printing "Hello, world!" to the console. But before we write our first line of code, let's understand what makes Rust special and how a Rust program is structured.

#### Why Rust?

Rust was created by [**Mozilla**](https://en.wikipedia.org/wiki/Rust_(programming_language)) and first released in 2015. It was designed to solve a fundamental problem: how do you write software that is both **fast** and **safe**? Languages like C and C++ give you speed but let you shoot yourself in the foot with memory bugs. Languages like Python and Java keep you safe but sacrifice raw performance. Rust gives you **both** — speed and safety — and it does this through its innovative **ownership system**, which we'll explore in depth later.

```sh
+-----------------------------------------------+
|          Why Rust for Blockchain?              |
+-----------------------------------------------+
|                                                |
|   Memory Safety ──> No Garbage Collector       |
|         |                                      |
|         v                                      |
|   Zero-Cost Abstractions ──> C-like Speed      |
|         |                                      |
|         v                                      |
|   Fearless Concurrency ──> Safe Parallelism    |
|         |                                      |
|         v                                      |
|   Strong Type System ──> Fewer Bugs            |
|                                                |
+-----------------------------------------------+
```

Here's why Rust is the **perfect language** for Solana and blockchain development:

- **No garbage collector**: Rust manages memory at compile time, which means no unpredictable pauses — critical for blockchain validators processing thousands of transactions per second.
- **Memory safety**: The compiler catches entire classes of bugs (null pointers, dangling references, buffer overflows) before your code ever runs.
- **Zero-cost abstractions**: You can write high-level, expressive code without paying a runtime performance penalty.
- **Fearless concurrency**: Rust's type system prevents data races at compile time, making concurrent programming safe by default.

#### Your First Rust Program

Let's write the classic "Hello, world!" program:

```rust
fn main() {
    println!("Hello, world! Welcome to the Rust Bootcamp! 🦀");
}
```

Let's break this down piece by piece:

- **`fn`** — This keyword declares a **function**. Functions are the building blocks of Rust programs.
- **`main`** — This is the **entry point** of every Rust program. When you run a Rust binary, execution begins in `main`.
- **`println!`** — This is a **macro** (note the `!`). Macros in Rust are like super-powered functions — they generate code at compile time. `println!` prints text to the console followed by a newline.
- **`"Hello, world!"`** — This is a **string literal**, a piece of text enclosed in double quotes.

#### How Rust Compilation Works

Unlike interpreted languages (Python, JavaScript), Rust is a **compiled language**. This means your code goes through a compilation step before it can run:

```sh
+------------------+     +------------------+     +------------------+
|   Source Code    | --> |     Compiler     | --> |    Binary        |
|   (.rs files)    |     |     (rustc)      |     |  (executable)    |
+------------------+     +------------------+     +------------------+
         |                       |                        |
    You write this        rustc checks for          Machine code
    in your editor        errors & compiles          that runs fast
```

To compile and run a Rust program from the command line:

```sh
# Compile the program
rustc main.rs

# Run the compiled binary
./main
```

Or, using [**Cargo**](https://doc.rust-lang.org/cargo/) (Rust's build system and package manager):

```sh
# Create a new project
cargo new hello_rust

# Build and run
cd hello_rust
cargo run
```

    Hello, world! Welcome to the Rust Bootcamp! 🦀

#### Comments in Rust

Comments are notes you leave in your code for yourself or other developers. The compiler ignores them entirely:

```rust
fn main() {
    // This is a single-line comment

    /* This is a
       multi-line comment */

    /// This is a documentation comment (used by `cargo doc`)
    /// It generates HTML documentation for your code

    println!("Comments are ignored by the compiler!");
}
```

**Key Takeaway**: Rust is a compiled, statically-typed language with a strong focus on safety and performance. The `fn main()` function is where execution begins, and `println!` is a macro for console output.

---

### 2. Variables & Mutability 📦

In Rust, variables are **immutable by default**. This might feel strange if you come from languages like Python or JavaScript where you can reassign variables freely. But immutability is one of Rust's superpowers — it makes your code safer and easier to reason about.

#### Declaring Variables with `let`

```rust
fn main() {
    let x = 5;
    println!("The value of x is: {}", x);
}
```

    The value of x is: 5

The `{}` inside the string is a **placeholder**. Rust replaces it with the value of `x` when printing. You can have multiple placeholders:

```rust
fn main() {
    let name = "Solana";
    let version = 2;
    println!("{} version {} is amazing!", name, version);
}
```

    Solana version 2 is amazing!

#### Immutability by Default

Try to change an immutable variable and the compiler will stop you:

```rust
fn main() {
    let x = 5;
    x = 6; // ERROR! Cannot assign twice to immutable variable
    println!("{}", x);
}
```

```sh
error[E0384]: cannot assign twice to immutable variable `x`
 --> src/main.rs:3:5
  |
2 |     let x = 5;
  |         - first assignment to `x`
3 |     x = 6;
  |     ^^^^^ cannot assign twice to immutable variable
```

This is Rust **protecting you**. By default, once a value is bound to a name, it can't change. This prevents an entire category of bugs where values change unexpectedly.

#### Making Variables Mutable with `mut`

When you do need a variable to change, add the `mut` keyword:

```rust
fn main() {
    let mut x = 5;
    println!("The value of x is: {}", x);

    x = 6;
    println!("The value of x is now: {}", x);
}
```

    The value of x is: 5
    The value of x is now: 6

Think of it like this: `let` creates a **locked box**, and `let mut` creates an **unlocked box** that you can open and change the contents of.

```sh
+-------------------+     +-------------------+
|  let x = 5;       |     |  let mut x = 5;   |
|  +-----+          |     |  +-----+          |
|  |  5  | 🔒       |     |  |  5  | 🔓       |
|  +-----+          |     |  +-----+          |
|  Cannot change!   |     |  x = 6; ✅        |
+-------------------+     +-------------------+
```

#### Constants

Constants are values that are **always immutable** — you can never add `mut` to them. They must have their type annotated, and they must be set to a constant expression (known at compile time):

```rust
const MAX_TRANSACTIONS_PER_BLOCK: u64 = 710_000;
const LAMPORTS_PER_SOL: u64 = 1_000_000_000;

fn main() {
    println!("Solana can process {} transactions per block", MAX_TRANSACTIONS_PER_BLOCK);
    println!("1 SOL = {} lamports", LAMPORTS_PER_SOL);
}
```

    Solana can process 710000 transactions per block
    1 SOL = 1000000000 lamports

**Key differences between `let` and `const`**:
- `const` must always have a type annotation (e.g., `: u64`)
- `const` values must be computable at compile time
- `const` can be declared in any scope, including global scope
- `const` is always immutable — you can never use `mut`
- Convention: `SCREAMING_SNAKE_CASE` for constant names

#### Shadowing

Rust allows you to declare a new variable with the **same name** as a previous one. The new variable **shadows** the old one:

```rust
fn main() {
    let x = 5;
    println!("x = {}", x);

    let x = x + 1;       // Shadows the previous x
    println!("x = {}", x);

    let x = x * 2;       // Shadows again
    println!("x = {}", x);

    // You can even change the type with shadowing!
    let x = "now I'm a string!";
    println!("x = {}", x);
}
```

    x = 5
    x = 6
    x = 12
    x = now I'm a string!

Shadowing is different from `mut` because:
- Each `let x` creates a **brand-new variable** — the old one is gone
- You can change the **type** of the value (try doing that with `mut`!)
- The resulting variable is still immutable after the reassignment

This is incredibly useful for transforming data step by step while keeping things immutable.

**Key Takeaway**: Variables are immutable by default in Rust. Use `mut` for mutable variables, `const` for compile-time constants, and shadowing to transform values while keeping immutability.

---

### 3. Data Types 🔢

Rust is a **statically typed** language, which means every variable must have a known type at compile time. The compiler can usually **infer** the type from the value, but sometimes you need to annotate it explicitly.

Rust's types fall into two main categories: **scalar types** (single values) and **compound types** (groups of values).

```sh
+-----------------------------------------------------+
|                    RUST DATA TYPES                   |
+-----------------------------------------------------+
|                                                      |
|   SCALAR TYPES          |   COMPOUND TYPES           |
|   ┌──────────────┐      |   ┌──────────────┐        |
|   │  Integers    │      |   │  Tuples      │        |
|   │  i8, i16,    │      |   │  (i32, f64,  │        |
|   │  i32, i64,   │      |   │   bool)      │        |
|   │  i128, isize │      |   └──────────────┘        |
|   │  u8, u16,    │      |   ┌──────────────┐        |
|   │  u32, u64,   │      |   │  Arrays      │        |
|   │  u128, usize │      |   │  [i32; 5]    │        |
|   └──────────────┘      |   └──────────────┘        |
|   ┌──────────────┐      |                            |
|   │  Floats      │      |                            |
|   │  f32, f64    │      |                            |
|   └──────────────┘      |                            |
|   ┌──────────────┐      |                            |
|   │  Boolean     │      |                            |
|   │  bool        │      |                            |
|   └──────────────┘      |                            |
|   ┌──────────────┐      |                            |
|   │  Character   │      |                            |
|   │  char        │      |                            |
|   └──────────────┘      |                            |
+-----------------------------------------------------+
```

#### Integer Types

Integers are whole numbers — no decimal points. Rust provides both **signed** (can be negative) and **unsigned** (always positive or zero) integers in various sizes:

| Length | Signed | Unsigned | Range (Signed) |
|--------|--------|----------|----------------|
| 8-bit | `i8` | `u8` | -128 to 127 |
| 16-bit | `i16` | `u16` | -32,768 to 32,767 |
| 32-bit | `i32` | `u32` | -2.1B to 2.1B |
| 64-bit | `i64` | `u64` | -9.2 quintillion to 9.2 quintillion |
| 128-bit | `i128` | `u128` | Astronomically large |
| arch | `isize` | `usize` | Depends on 32/64-bit system |

Why does this matter for Solana? Because **lamports** (the smallest unit of SOL) are stored as `u64` values. You'll see `u64` everywhere in Solana programs:

```rust
fn main() {
    // In Solana, balances are stored as u64 (lamports)
    let balance: u64 = 1_000_000_000; // 1 SOL = 1 billion lamports
    let fee: u64 = 5_000;             // Typical transaction fee

    println!("Balance: {} lamports", balance);
    println!("Fee: {} lamports", fee);
    println!("After fee: {} lamports", balance - fee);

    // Different integer sizes
    let small: u8 = 255;           // Max value for u8
    let medium: u32 = 4_294_967_295; // Max value for u32
    let big: u64 = 18_446_744_073_709_551_615; // Max value for u64

    println!("u8 max: {}", small);
    println!("u32 max: {}", medium);
    println!("u64 max: {}", big);
}
```

    Balance: 1000000000 lamports
    Fee: 5000 lamports
    After fee: 999995000 lamports
    u8 max: 255
    u32 max: 4294967295
    u64 max: 18446744073709551615

**Number literals** in Rust support several convenient formats:

```rust
fn main() {
    let decimal = 98_222;       // Underscores for readability
    let hex = 0xff;             // Hexadecimal
    let octal = 0o77;           // Octal
    let binary = 0b1111_0000;   // Binary
    let byte = b'A';            // Byte (u8 only)

    println!("Decimal: {}", decimal);
    println!("Hex: {}", hex);
    println!("Octal: {}", octal);
    println!("Binary: {}", binary);
    println!("Byte: {}", byte);
}
```

    Decimal: 98222
    Hex: 255
    Octal: 63
    Binary: 240
    Byte: 65

#### Floating-Point Types

Floating-point numbers have decimal points. Rust has `f32` (single precision) and `f64` (double precision, the default):

```rust
fn main() {
    let x = 2.0;       // f64 (default)
    let y: f32 = 3.0;  // f32

    // Basic arithmetic
    let sum = 5.0 + 10.5;
    let difference = 95.5 - 4.3;
    let product = 4.0 * 30.0;
    let quotient = 56.7 / 32.2;
    let remainder = 43.0 % 5.0;

    println!("Sum: {}", sum);
    println!("Difference: {}", difference);
    println!("Product: {}", product);
    println!("Quotient: {}", quotient);
    println!("Remainder: {}", remainder);
}
```

    Sum: 15.5
    Difference: 91.2
    Product: 120
    Quotient: 1.7608695652173911
    Remainder: 3

#### Booleans

The boolean type has exactly two values: `true` and `false`. Booleans are one byte in size and are used heavily in control flow:

```rust
fn main() {
    let is_active: bool = true;
    let is_executable = false;

    println!("Account active: {}", is_active);
    println!("Account executable: {}", is_executable);

    // Booleans from comparisons
    let balance: u64 = 500;
    let has_enough = balance > 100;
    println!("Has enough balance: {}", has_enough);
}
```

    Account active: true
    Account executable: false
    Has enough balance: true

#### Characters

The `char` type represents a single [**Unicode**](https://en.wikipedia.org/wiki/Unicode) character. Unlike strings (double quotes), characters use **single quotes** and are 4 bytes in size:

```rust
fn main() {
    let letter = 'a';
    let emoji = '🦀';
    let chinese = '中';
    let heart = '❤';

    println!("{} {} {} {}", letter, emoji, chinese, heart);
}
```

    a 🦀 中 ❤

#### Tuples

Tuples group multiple values of **different types** into one compound type. They have a fixed length — once declared, their size cannot change:

```rust
fn main() {
    // A tuple with three different types
    let transaction: (u64, bool, &str) = (1_000_000, true, "transfer");

    // Destructuring: unpack tuple into individual variables
    let (amount, is_signed, tx_type) = transaction;
    println!("Amount: {}, Signed: {}, Type: {}", amount, is_signed, tx_type);

    // Access individual elements by index (0-based)
    let amount = transaction.0;
    let is_signed = transaction.1;
    let tx_type = transaction.2;
    println!("First element: {}", amount);
    println!("Second element: {}", is_signed);
    println!("Third element: {}", tx_type);
}
```

    Amount: 1000000, Signed: true, Type: transfer
    First element: 1000000
    Second element: true
    Third element: transfer

#### Arrays

Arrays group multiple values of the **same type** with a **fixed length**. They're stored on the stack, making them very fast:

```rust
fn main() {
    // An array of 5 integers
    let validators: [&str; 5] = ["Everstake", "Chorus One", "Figment", "Certus One", "Solflare"];

    // Access elements by index
    println!("First validator: {}", validators[0]);
    println!("Last validator: {}", validators[4]);

    // Initialize array with same value
    let zeroes = [0u8; 32]; // 32 bytes of zeros (like a blank pubkey)
    println!("Array of 32 zeros: {:?}", zeroes);

    // Array length
    println!("Number of validators: {}", validators.len());
}
```

    First validator: Everstake
    Last validator: Solflare
    Array of 32 zeros: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
    Number of validators: 5

**Arrays vs. Vectors**: Arrays have a fixed size known at compile time. If you need a dynamically-sized collection, use a `Vec<T>` (we'll cover this in the Collections section).

#### Strings in Rust

Strings in Rust deserve special attention because they're more complex than in most languages. Rust has two main string types:

```sh
+------------------------------------------------------+
|                  STRINGS IN RUST                      |
+------------------------------------------------------+
|                                                       |
|   &str (string slice)         String (owned string)   |
|   ┌──────────────────┐       ┌──────────────────┐    |
|   │ "hello"          │       │ String::from(     │    |
|   │                  │       │   "hello"         │    |
|   │ • Immutable      │       │ )                 │    |
|   │ • Fixed size     │       │ • Mutable         │    |
|   │ • Borrowed ref   │       │ • Growable         │   |
|   │ • Stack / static │       │ • Heap allocated   │   |
|   └──────────────────┘       └──────────────────┘    |
|                                                       |
+------------------------------------------------------+
```

```rust
fn main() {
    // &str - string slice (borrowed, immutable, lightweight)
    let greeting: &str = "Hello, Solana!";

    // String - owned string (mutable, heap-allocated)
    let mut owned_greeting = String::from("Hello");
    owned_greeting.push_str(", Solana!");
    owned_greeting.push('!');

    println!("Slice: {}", greeting);
    println!("Owned: {}", owned_greeting);
    println!("Length: {}", owned_greeting.len());

    // Converting between the two
    let slice_from_owned: &str = &owned_greeting; // String -> &str (cheap)
    let owned_from_slice: String = greeting.to_string(); // &str -> String (allocates)

    // String formatting
    let name = "Validator";
    let id = 42;
    let formatted = format!("{}#{}", name, id); // Like println! but returns a String
    println!("Formatted: {}", formatted);
}
```

    Slice: Hello, Solana!
    Owned: Hello, Solana!!
    Length: 15
    Formatted: Validator#42

#### Type Casting

Rust doesn't do **implicit type conversions** — you must be explicit. Use `as` for basic casts:

```rust
fn main() {
    let x: i32 = 42;
    let y: f64 = x as f64;          // i32 to f64
    let z: u8 = x as u8;            // i32 to u8 (be careful with overflow!)

    let big: u64 = 1_000_000_000;
    let small: u32 = big as u32;     // u64 to u32

    println!("i32: {}", x);
    println!("f64: {}", y);
    println!("u8: {}", z);
    println!("u32: {}", small);

    // Be careful! Casting can truncate or wrap
    let too_big: u16 = 256;
    let truncated: u8 = too_big as u8; // 256 wraps to 0 for u8!
    println!("256 as u8 = {} (wrapped!)", truncated);
}
```

    i32: 42
    f64: 42
    u8: 42
    u32: 1000000000
    256 as u8 = 0 (wrapped!)

**Key Takeaway**: Rust has a rich type system with integers (signed/unsigned in various sizes), floats, booleans, characters, tuples, arrays, and two string types. Types are checked at compile time, and conversions must be explicit.

---

### 4. Functions 🔧

Functions are the **building blocks** of Rust programs. You've already seen `fn main()` — the special entry point. But you can define as many functions as you want, and they're how you organize and reuse your code.

#### Defining Functions

```rust
fn greet() {
    println!("Welcome to the Solana ecosystem!");
}

fn main() {
    greet();       // Call the function
    greet();       // Call it again!
}
```

    Welcome to the Solana ecosystem!
    Welcome to the Solana ecosystem!

Convention: Rust uses **snake_case** for function and variable names (e.g., `calculate_fee`, not `calculateFee`).

#### Parameters

Functions can accept **parameters** — values you pass into the function. Every parameter **must** have a type annotation:

```rust
fn print_balance(lamports: u64) {
    let sol = lamports as f64 / 1_000_000_000.0;
    println!("Balance: {} lamports ({:.4} SOL)", lamports, sol);
}

fn transfer(from: &str, to: &str, amount: u64) {
    println!("Transferring {} lamports from {} to {}", amount, from, to);
}

fn main() {
    print_balance(5_000_000_000);
    print_balance(500_000);
    transfer("Alice", "Bob", 1_000_000_000);
}
```

    Balance: 5000000000 lamports (5.0000 SOL)
    Balance: 500000 lamports (0.0005 SOL)
    Transferring 1000000000 lamports from Alice to Bob

#### Return Values

Functions return values using the `->` syntax. The **last expression** in a function body is automatically the return value (no semicolon!):

```rust
fn add(a: i32, b: i32) -> i32 {
    a + b  // No semicolon = this is the return value
}

fn calculate_fee(lamports: u64) -> u64 {
    let fee_rate = 5000; // 5000 lamports base fee
    fee_rate
}

fn lamports_to_sol(lamports: u64) -> f64 {
    lamports as f64 / 1_000_000_000.0
}

fn main() {
    let sum = add(3, 7);
    println!("3 + 7 = {}", sum);

    let fee = calculate_fee(1_000_000);
    println!("Fee: {} lamports", fee);

    let sol = lamports_to_sol(2_500_000_000);
    println!("2.5 billion lamports = {} SOL", sol);
}
```

    3 + 7 = 10
    Fee: 5000 lamports
    2.5 billion lamports = 2.5 SOL

**Important**: Notice the difference between expressions and statements:
- **Expression**: `a + b` — produces a value (no semicolon)
- **Statement**: `a + b;` — does NOT produce a value (has a semicolon)

Adding a semicolon to the last line changes it from "return this value" to "execute this and return nothing" — a very common Rust gotcha!

```rust
fn returns_five() -> i32 {
    5       // ✅ Returns 5
}

// fn returns_nothing() -> i32 {
//     5;   // ❌ ERROR! Returns () not i32. The semicolon kills the return value.
// }

fn main() {
    println!("{}", returns_five());
}
```

    5

#### Early Returns

You can use the `return` keyword to exit a function early:

```rust
fn check_balance(balance: u64, amount: u64) -> bool {
    if amount > balance {
        println!("Insufficient funds!");
        return false; // Early return
    }
    println!("Transaction approved!");
    true // Last expression is the return value
}

fn main() {
    let result1 = check_balance(1000, 500);
    println!("Result: {}\n", result1);

    let result2 = check_balance(100, 500);
    println!("Result: {}", result2);
}
```

    Transaction approved!
    Result: true

    Insufficient funds!
    Result: false

#### Functions Returning Multiple Values with Tuples

```rust
fn get_account_info() -> (u64, bool, &'static str) {
    let balance = 5_000_000_000;
    let is_executable = false;
    let owner = "SystemProgram";
    (balance, is_executable, owner)
}

fn main() {
    let (balance, executable, owner) = get_account_info();
    println!("Balance: {}", balance);
    println!("Executable: {}", executable);
    println!("Owner: {}", owner);
}
```

    Balance: 5000000000
    Executable: false
    Owner: SystemProgram

**Key Takeaway**: Functions are declared with `fn`, use snake_case names, require type annotations for parameters, and return the last expression (without semicollon). The `return` keyword is used for early exits.

---

### 5. Control Flow 🚦

Control flow lets your program make decisions and repeat actions. Rust provides `if`/`else`, `loop`, `while`, and `for` — and each one has some Rust-specific twists.

#### `if` / `else if` / `else`

```rust
fn classify_transaction(amount: u64) {
    if amount == 0 {
        println!("Empty transaction");
    } else if amount < 1_000_000 {
        println!("Micro transaction ({} lamports)", amount);
    } else if amount < 1_000_000_000 {
        println!("Standard transaction ({} lamports)", amount);
    } else {
        println!("Whale transaction! ({} lamports)", amount);
    }
}

fn main() {
    classify_transaction(0);
    classify_transaction(500);
    classify_transaction(50_000_000);
    classify_transaction(5_000_000_000);
}
```

    Empty transaction
    Micro transaction (500 lamports)
    Standard transaction (50000000 lamports)
    Whale transaction! (5000000000 lamports)

**Rust twist**: `if` is an **expression**, meaning it can return a value! This is like the ternary operator (`? :`) in other languages but more powerful:

```rust
fn main() {
    let balance = 100;
    let status = if balance > 0 { "active" } else { "empty" };
    println!("Account status: {}", status);

    // You can even use it for assignment with multiple conditions
    let tier = if balance > 1000 {
        "gold"
    } else if balance > 100 {
        "silver"
    } else {
        "bronze"
    };
    println!("Account tier: {}", tier);
}
```

    Account status: active
    Account tier: bronze

#### `loop` — Infinite Loop

`loop` creates an infinite loop. You break out with `break`, and you can return a value from the loop:

```rust
fn main() {
    let mut counter = 0;

    // loop with break
    loop {
        counter += 1;
        if counter == 5 {
            break;
        }
    }
    println!("Counter reached: {}", counter);

    // loop that returns a value!
    let mut attempts = 0;
    let result = loop {
        attempts += 1;
        if attempts * 10 >= 50 {
            break attempts; // Return the value from the loop
        }
    };
    println!("Took {} attempts to reach 50", result);
}
```

    Counter reached: 5
    Took 5 attempts to reach 50

#### `while` — Conditional Loop

`while` loops run as long as a condition is true:

```rust
fn main() {
    let mut balance: i64 = 100;
    let fee: i64 = 15;
    let mut transactions = 0;

    while balance >= fee {
        balance -= fee;
        transactions += 1;
        println!("Transaction {}: balance = {}", transactions, balance);
    }

    println!("Final balance: {} (after {} transactions)", balance, transactions);
}
```

    Transaction 1: balance = 85
    Transaction 2: balance = 70
    Transaction 3: balance = 55
    Transaction 4: balance = 40
    Transaction 5: balance = 25
    Transaction 6: balance = 10
    Final balance: 10 (after 6 transactions)

#### `for` — Iterating Over Collections

`for` loops are the most common loop in Rust. They iterate over anything that implements the `Iterator` trait:

```rust
fn main() {
    // Iterate over a range
    println!("Counting blocks:");
    for block in 1..=5 {    // 1..=5 is inclusive (1, 2, 3, 4, 5)
        println!("  Block #{}", block);
    }

    // Iterate over an array
    let validators = ["Alice", "Bob", "Charlie", "Diana"];
    println!("\nValidator Roll Call:");
    for validator in validators.iter() {
        println!("  Present: {}", validator);
    }

    // Iterate with index using enumerate
    println!("\nValidator Positions:");
    for (index, validator) in validators.iter().enumerate() {
        println!("  Position {}: {}", index, validator);
    }

    // Iterate over a range (exclusive end)
    println!("\n0..5 range:");
    for i in 0..5 {         // 0, 1, 2, 3, 4 (excludes 5)
        print!("{} ", i);
    }
    println!();
}
```

    Counting blocks:
      Block #1
      Block #2
      Block #3
      Block #4
      Block #5

    Validator Roll Call:
      Present: Alice
      Present: Bob
      Present: Charlie
      Present: Diana

    Validator Positions:
      Position 0: Alice
      Position 1: Bob
      Position 2: Charlie
      Position 3: Diana

    0..5 range:
    0 1 2 3 4

#### `loop` Labels and `continue`

You can label loops and use `break`/`continue` with specific labels when you have nested loops:

```rust
fn main() {
    // continue: skip current iteration
    println!("Skip even numbers:");
    for i in 0..10 {
        if i % 2 == 0 {
            continue; // Skip to next iteration
        }
        print!("{} ", i);
    }
    println!();

    // Named loops: break out of outer loop from inner loop
    let mut found = false;
    'outer: for x in 0..10 {
        for y in 0..10 {
            if x + y == 15 {
                println!("Found: x={}, y={}", x, y);
                found = true;
                break 'outer; // Break out of the OUTER loop
            }
        }
    }
    println!("Found pair summing to 15: {}", found);
}
```

    Skip even numbers:
    1 3 5 7 9
    Found: x=6, y=9
    Found pair summing to 15: true

#### `match` — Powerful Pattern Matching

`match` is one of Rust's most powerful features. It's like a supercharged `switch` statement:

```rust
fn describe_http_status(code: u16) {
    match code {
        200 => println!("200: OK - Transaction successful"),
        400 => println!("400: Bad Request - Invalid transaction"),
        404 => println!("404: Not Found - Account doesn't exist"),
        429 => println!("429: Too Many Requests - Rate limited"),
        500 => println!("500: Internal Server Error - RPC node error"),
        _ => println!("{}: Unknown status code", code), // _ catches everything else
    }
}

fn main() {
    describe_http_status(200);
    describe_http_status(404);
    describe_http_status(418);

    // match is also an expression
    let balance: u64 = 500;
    let status = match balance {
        0 => "empty",
        1..=999 => "low",
        1_000..=999_999 => "medium",
        _ => "high",
    };
    println!("Balance status: {}", status);
}
```

    200: OK - Transaction successful
    404: Not Found - Account doesn't exist
    418: Unknown status code
    Balance status: low

**Key Takeaway**: Rust's control flow includes `if`/`else` (which are expressions!), three loop types (`loop`, `while`, `for`), and the powerful `match` expression for pattern matching. Loop labels allow breaking out of nested loops.

---

### 6. Ownership & Borrowing 🏠

This is **the most important section** in this entire chapter. Ownership is what makes Rust unique among programming languages. It's the mechanism by which Rust guarantees memory safety without a garbage collector — and it's the concept that trips up most newcomers.

Understanding ownership is **critical** for Solana development, because Solana programs deal with accounts and data that must be carefully managed.

#### The Three Rules of Ownership

```sh
+-----------------------------------------------------------+
|              THE THREE RULES OF OWNERSHIP                  |
+-----------------------------------------------------------+
|                                                            |
|  1. Each value in Rust has exactly ONE owner               |
|                                                            |
|  2. There can only be ONE owner at a time                  |
|                                                            |
|  3. When the owner goes out of scope, the value is dropped |
|                                                            |
+-----------------------------------------------------------+
```

Let's see what this means in practice:

```rust
fn main() {
    {                           // s is not valid here — it hasn't been declared yet
        let s = String::from("hello");  // s is valid from this point forward
        println!("{}", s);      // we can use s here
    }                           // scope is over, s is DROPPED (memory freed)

    // println!("{}", s);       // ERROR! s no longer exists
}
```

    hello

#### Move Semantics

When you assign a value to another variable, Rust doesn't copy it — it **moves** it. The original variable becomes invalid:

```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1;                  // s1 is MOVED to s2

    // println!("{}", s1);        // ERROR! s1 no longer valid
    println!("{}", s2);           // s2 owns the value now
}
```

    hello

Why? Let's visualize what happens in memory:

```sh
BEFORE MOVE:                    AFTER MOVE:

 s1                              s1 (invalid!)
 +--------+                     +--------+
 | ptr  ──┼──> "hello"          | xxxxxx |
 | len: 5 |   (heap data)       | xxxxxx |
 | cap: 5 |                     +--------+
 +--------+
                                 s2
                                 +--------+
                                 | ptr  ──┼──> "hello"
                                 | len: 5 |   (heap data)
                                 | cap: 5 |
                                 +--------+
```

This prevents **double-free** errors — if both `s1` and `s2` tried to free the same memory when they went out of scope, that would corrupt memory. Rust solves this by invalidating `s1` after the move.

#### Clone — Deep Copy

If you actually want to **copy** heap data, use `clone()`:

```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1.clone(); // Deep copy — both s1 and s2 are valid

    println!("s1 = {}", s1);
    println!("s2 = {}", s2);
}
```

    s1 = hello
    s2 = hello

#### Copy Types (Stack-Only Data)

Simple types that live on the stack (integers, booleans, chars, floats) implement the `Copy` trait. They're **copied** automatically instead of moved:

```rust
fn main() {
    let x: i32 = 5;
    let y = x;     // x is COPIED, not moved (i32 implements Copy)

    println!("x = {}", x);  // ✅ Both valid!
    println!("y = {}", y);  // ✅

    // These types are Copy:
    // - All integer types (i8, u8, i32, u64, etc.)
    // - Booleans (bool)
    // - Floating point (f32, f64)
    // - Characters (char)
    // - Tuples of Copy types: (i32, f64)
}
```

    x = 5
    y = 5

#### Ownership and Functions

Passing a value to a function **moves** it (or copies it for Copy types):

```rust
fn takes_ownership(s: String) {
    println!("Got: {}", s);
} // s is dropped here — memory is freed

fn makes_copy(x: i32) {
    println!("Got: {}", x);
} // x is a copy, the original is unaffected

fn main() {
    let s = String::from("hello");
    takes_ownership(s);
    // println!("{}", s);  // ERROR! s was moved into the function

    let x = 5;
    makes_copy(x);
    println!("x is still: {}", x); // ✅ i32 is Copy
}
```

    Got: hello
    Got: 5
    x is still: 5

#### Returning Ownership

Functions can give ownership back by returning values:

```rust
fn create_greeting(name: &str) -> String {
    let greeting = format!("Hello, {}!", name);
    greeting // Ownership of the String is MOVED to the caller
}

fn main() {
    let g = create_greeting("Solana Developer");
    println!("{}", g); // We own it now
}
```

    Hello, Solana Developer!

#### References and Borrowing

Constantly moving ownership around is tedious. Instead, you can **borrow** a value using **references** (`&`). Borrowing lets you use a value **without taking ownership**:

```rust
fn calculate_length(s: &String) -> usize {  // s is a REFERENCE to a String
    s.len()
} // s goes out of scope, but since it doesn't own the String, nothing is dropped

fn main() {
    let s = String::from("hello");
    let len = calculate_length(&s);  // Pass a REFERENCE (borrow)

    // s is still valid because we only borrowed it!
    println!("The length of '{}' is {}", s, len);
}
```

    The length of 'hello' is 5

```sh
+----------------------------------------------------+
|               BORROWING VISUALIZED                  |
+----------------------------------------------------+
|                                                     |
|  main()            calculate_length()               |
|  +--------+        +--------+                       |
|  | s ─────┼──┐     | s ─────┼──┐                   |
|  +--------+  |     +--------+  |                    |
|              |                 |                     |
|              └──> "hello" <───┘                     |
|              (owned)  (borrowed via &)              |
|                                                     |
+----------------------------------------------------+
```

#### Mutable References

By default, references are **immutable** — you can look but not touch. To modify borrowed data, use a **mutable reference** (`&mut`):

```rust
fn add_exclamation(s: &mut String) {
    s.push_str("!!!");
}

fn main() {
    let mut s = String::from("Hello, Solana");
    println!("Before: {}", s);

    add_exclamation(&mut s);
    println!("After: {}", s);
}
```

    Before: Hello, Solana
    After: Hello, Solana!!!

#### The Borrowing Rules

Rust enforces strict borrowing rules at compile time:

```sh
+----------------------------------------------------------+
|               THE RULES OF BORROWING                      |
+----------------------------------------------------------+
|                                                           |
|  At any given time, you can have EITHER:                  |
|                                                           |
|    • ONE mutable reference (&mut T)                       |
|        OR                                                 |
|    • ANY number of immutable references (&T)              |
|                                                           |
|  But NEVER both at the same time!                         |
|                                                           |
|  Also: References must always be valid (no dangling refs) |
|                                                           |
+----------------------------------------------------------+
```

```rust
fn main() {
    let mut s = String::from("hello");

    // Multiple immutable borrows — OK!
    let r1 = &s;
    let r2 = &s;
    println!("{} and {}", r1, r2);
    // r1 and r2 are no longer used after this point

    // Single mutable borrow — OK! (r1 and r2 are done)
    let r3 = &mut s;
    r3.push_str(" world");
    println!("{}", r3);
}
```

    hello and hello
    hello world

**Why these rules?** They prevent **data races** at compile time. A data race occurs when:
1. Two or more pointers access the same data at the same time
2. At least one of them is writing
3. There's no mechanism to synchronize access

Rust's borrow checker makes data races **impossible** — they're caught before your program ever runs!

**Key Takeaway**: Ownership is Rust's core innovation. Each value has one owner, ownership can be transferred (moved) or shared (borrowed). Borrowing follows strict rules: either one mutable reference or many immutable references, never both. This eliminates data races and memory bugs at compile time.

---

### 7. Structs 🏗️

Structs let you create **custom data types** by grouping related values together. If you're familiar with classes in other languages, structs are similar — but without inheritance. They're fundamental to Solana programming, where accounts and instructions are represented as structs.

#### Defining and Instantiating Structs

```rust
// Define a struct
struct Account {
    address: String,
    balance: u64,
    is_executable: bool,
    owner: String,
}

fn main() {
    // Create an instance
    let account = Account {
        address: String::from("7XhivnMM..."),
        balance: 5_000_000_000,
        is_executable: false,
        owner: String::from("SystemProgram"),
    };

    println!("Address: {}", account.address);
    println!("Balance: {} lamports", account.balance);
    println!("Executable: {}", account.is_executable);
    println!("Owner: {}", account.owner);
}
```

    Address: 7XhivnMM...
    Balance: 5000000000 lamports
    Executable: false
    Owner: SystemProgram

#### Mutable Structs

The entire struct must be mutable to modify any field — Rust doesn't allow individual fields to be mutable:

```rust
struct Wallet {
    name: String,
    balance: u64,
}

fn main() {
    let mut wallet = Wallet {
        name: String::from("My Wallet"),
        balance: 1_000_000_000,
    };

    println!("Before: {} - {} lamports", wallet.name, wallet.balance);

    wallet.balance += 500_000_000; // Modify a field
    println!("After: {} - {} lamports", wallet.name, wallet.balance);
}
```

    Before: My Wallet - 1000000000 lamports
    After: My Wallet - 1500000000 lamports

#### Field Init Shorthand

When parameter names match field names, you can use shorthand:

```rust
struct Validator {
    name: String,
    stake: u64,
    active: bool,
}

fn create_validator(name: String, stake: u64) -> Validator {
    Validator {
        name,       // shorthand for name: name
        stake,      // shorthand for stake: stake
        active: true,
    }
}

fn main() {
    let v = create_validator(String::from("Everstake"), 10_000_000);
    println!("{}: {} stake, active: {}", v.name, v.stake, v.active);
}
```

    Everstake: 10000000 stake, active: true

#### Struct Update Syntax

Create a new struct based on an existing one, changing only some fields:

```rust
struct Config {
    rpc_url: String,
    commitment: String,
    timeout: u64,
    retries: u32,
}

fn main() {
    let default_config = Config {
        rpc_url: String::from("https://api.mainnet-beta.solana.com"),
        commitment: String::from("confirmed"),
        timeout: 30,
        retries: 3,
    };

    // Create a new config, changing only rpc_url
    let devnet_config = Config {
        rpc_url: String::from("https://api.devnet.solana.com"),
        ..default_config  // Fill remaining fields from default_config
    };

    println!("Devnet RPC: {}", devnet_config.rpc_url);
    println!("Commitment: {}", devnet_config.commitment);
    println!("Timeout: {}s", devnet_config.timeout);
}
```

    Devnet RPC: https://api.devnet.solana.com
    Commitment: confirmed
    Timeout: 30s

#### Tuple Structs

Structs without named fields — useful for creating distinct types:

```rust
struct Lamports(u64);
struct Sol(f64);

fn main() {
    let balance = Lamports(5_000_000_000);
    let sol_balance = Sol(5.0);

    println!("Balance: {} lamports", balance.0);
    println!("Balance: {} SOL", sol_balance.0);

    // This is great for type safety! You can't accidentally mix them up.
}
```

    Balance: 5000000000 lamports
    Balance: 5 SOL

#### Implementing Methods with `impl`

Methods are functions attached to a struct. They're defined inside an `impl` block:

```rust
struct Account {
    address: String,
    balance: u64,
}

impl Account {
    // Associated function (like a static method / constructor)
    fn new(address: String, balance: u64) -> Account {
        Account { address, balance }
    }

    // Method: takes &self (borrows the instance immutably)
    fn display(&self) {
        println!("Account {} has {} lamports", self.address, self.balance);
    }

    // Method: takes &mut self (borrows the instance mutably)
    fn deposit(&mut self, amount: u64) {
        self.balance += amount;
        println!("Deposited {} lamports. New balance: {}", amount, self.balance);
    }

    // Method: takes &mut self
    fn withdraw(&mut self, amount: u64) -> bool {
        if amount > self.balance {
            println!("Insufficient funds!");
            return false;
        }
        self.balance -= amount;
        println!("Withdrew {} lamports. New balance: {}", amount, self.balance);
        true
    }

    // Method: returns computed value
    fn balance_in_sol(&self) -> f64 {
        self.balance as f64 / 1_000_000_000.0
    }
}

fn main() {
    // Use the associated function (constructor)
    let mut acc = Account::new(String::from("7Xhiv..."), 2_000_000_000);

    acc.display();
    println!("Balance in SOL: {:.2}\n", acc.balance_in_sol());

    acc.deposit(500_000_000);
    acc.withdraw(100_000_000);
    acc.withdraw(3_000_000_000); // Should fail

    println!("\nFinal balance: {:.4} SOL", acc.balance_in_sol());
}
```

    Account 7Xhiv... has 2000000000 lamports
    Balance in SOL: 2.00

    Deposited 500000000 lamports. New balance: 2500000000
    Withdrew 100000000 lamports. New balance: 2400000000
    Insufficient funds!

    Final balance: 2.4000 SOL

The three types of `self`:
- **`&self`** — borrows the struct immutably (read-only)
- **`&mut self`** — borrows the struct mutably (read-write)
- **`self`** — takes ownership (consumes the struct)

#### Derive Macros

Rust can automatically implement common traits for your structs using `#[derive]`:

```rust
#[derive(Debug, Clone, PartialEq)]
struct Transaction {
    from: String,
    to: String,
    amount: u64,
}

fn main() {
    let tx1 = Transaction {
        from: String::from("Alice"),
        to: String::from("Bob"),
        amount: 1_000_000,
    };

    // Debug printing (from #[derive(Debug)])
    println!("{:?}", tx1);
    println!("{:#?}", tx1);   // Pretty-printed debug

    // Clone (from #[derive(Clone)])
    let tx2 = tx1.clone();

    // PartialEq comparison (from #[derive(PartialEq)])
    println!("tx1 == tx2: {}", tx1 == tx2);
}
```

    Transaction { from: "Alice", to: "Bob", amount: 1000000 }
    Transaction {
        from: "Alice",
        to: "Bob",
        amount: 1000000,
    }
    tx1 == tx2: true

**Key Takeaway**: Structs are Rust's custom data types. They group related data, support methods via `impl` blocks, and can auto-derive common functionality. You'll see structs everywhere in Solana — `AccountInfo`, `Instruction`, `Pubkey` are all structs.

---

### 8. Enums & Pattern Matching 🎯

Enums (enumerations) let you define a type that can be one of several **variants**. Combined with `match`, they form one of Rust's most powerful features. Solana uses enums extensively for instruction types, error codes, and account states.

#### Basic Enums

```rust
#[derive(Debug)]
enum Network {
    Mainnet,
    Devnet,
    Testnet,
    Localnet,
}

fn get_rpc_url(network: &Network) -> &str {
    match network {
        Network::Mainnet => "https://api.mainnet-beta.solana.com",
        Network::Devnet => "https://api.devnet.solana.com",
        Network::Testnet => "https://api.testnet.solana.com",
        Network::Localnet => "http://localhost:8899",
    }
}

fn main() {
    let net = Network::Devnet;
    println!("Network: {:?}", net);
    println!("RPC URL: {}", get_rpc_url(&net));
}
```

    Network: Devnet
    RPC URL: https://api.devnet.solana.com

#### Enums with Data

Unlike enums in many other languages, Rust enums can **carry data** with each variant:

```rust
#[derive(Debug)]
enum Instruction {
    Transfer { from: String, to: String, amount: u64 },
    CreateAccount { address: String, space: u64 },
    CloseAccount { address: String },
    Memo(String),
}

fn process_instruction(instruction: &Instruction) {
    match instruction {
        Instruction::Transfer { from, to, amount } => {
            println!("Transfer {} lamports: {} -> {}", amount, from, to);
        }
        Instruction::CreateAccount { address, space } => {
            println!("Create account {} with {} bytes", address, space);
        }
        Instruction::CloseAccount { address } => {
            println!("Close account {}", address);
        }
        Instruction::Memo(text) => {
            println!("Memo: {}", text);
        }
    }
}

fn main() {
    let instructions = vec![
        Instruction::CreateAccount {
            address: String::from("Acc123"),
            space: 165,
        },
        Instruction::Transfer {
            from: String::from("Alice"),
            to: String::from("Bob"),
            amount: 1_000_000_000,
        },
        Instruction::Memo(String::from("Payment for services")),
        Instruction::CloseAccount {
            address: String::from("OldAcc"),
        },
    ];

    for instruction in &instructions {
        process_instruction(instruction);
    }
}
```

    Create account Acc123 with 165 bytes
    Transfer 1000000000 lamports: Alice -> Bob
    Memo: Payment for services
    Close account OldAcc

#### Option<T> — Handling the Absence of a Value

Rust has **no null**. Instead, it uses the `Option` enum to represent values that might or might not exist:

```rust
// Option is defined in the standard library like this:
// enum Option<T> {
//     Some(T),   // There is a value
//     None,      // There is no value
// }

fn find_validator(validators: &[&str], name: &str) -> Option<usize> {
    for (i, v) in validators.iter().enumerate() {
        if *v == name {
            return Some(i);
        }
    }
    None
}

fn main() {
    let validators = vec!["Alice", "Bob", "Charlie"];

    // Using match with Option
    match find_validator(&validators, "Bob") {
        Some(index) => println!("Found Bob at position {}", index),
        None => println!("Bob not found"),
    }

    match find_validator(&validators, "Diana") {
        Some(index) => println!("Found Diana at position {}", index),
        None => println!("Diana not found"),
    }

    // Using if let for concise pattern matching
    if let Some(index) = find_validator(&validators, "Charlie") {
        println!("Charlie is at position {}", index);
    }

    // Using unwrap_or for default values
    let position = find_validator(&validators, "Eve").unwrap_or(999);
    println!("Eve's position (or default): {}", position);
}
```

    Found Bob at position 1
    Diana not found
    Charlie is at position 2
    Eve's position (or default): 999

#### Result<T, E> — Handling Errors

`Result` is like `Option` but carries an **error type** when things go wrong. This is Rust's primary error-handling mechanism:

```rust
// Result is defined like this:
// enum Result<T, E> {
//     Ok(T),    // Success with value T
//     Err(E),   // Failure with error E
// }

fn parse_lamports(input: &str) -> Result<u64, String> {
    match input.parse::<u64>() {
        Ok(value) => Ok(value),
        Err(_) => Err(format!("'{}' is not a valid amount", input)),
    }
}

fn main() {
    // Handling with match
    match parse_lamports("1000000") {
        Ok(amount) => println!("Parsed: {} lamports", amount),
        Err(e) => println!("Error: {}", e),
    }

    match parse_lamports("not_a_number") {
        Ok(amount) => println!("Parsed: {} lamports", amount),
        Err(e) => println!("Error: {}", e),
    }

    // Using unwrap (panics on Err — only use in examples/tests!)
    let amount = parse_lamports("5000").unwrap();
    println!("Unwrapped: {}", amount);

    // Using unwrap_or
    let amount = parse_lamports("bad").unwrap_or(0);
    println!("With default: {}", amount);
}
```

    Parsed: 1000000 lamports
    Error: 'not_a_number' is not a valid amount
    Unwrapped: 5000
    With default: 0

#### Advanced Pattern Matching

`match` supports complex patterns beyond simple values:

```rust
fn main() {
    // Matching multiple values
    let error_code: u32 = 3;
    let message = match error_code {
        0 => "Success",
        1 | 2 => "Warning",          // Match 1 OR 2
        3..=10 => "Error",            // Match range 3 through 10
        _ => "Unknown",               // Catch-all
    };
    println!("Code {}: {}", error_code, message);

    // Matching with guards
    let balance: i64 = -50;
    let status = match balance {
        b if b < 0 => "overdrawn",
        0 => "empty",
        b if b < 1000 => "low",
        _ => "healthy",
    };
    println!("Balance {}: {}", balance, status);

    // Destructuring in match
    let point = (3, 7);
    match point {
        (0, 0) => println!("Origin"),
        (x, 0) => println!("On x-axis at {}", x),
        (0, y) => println!("On y-axis at {}", y),
        (x, y) => println!("Point at ({}, {})", x, y),
    }
}
```

    Code 3: Error
    Balance -50: overdrawn
    Point at (3, 7)

**Key Takeaway**: Enums define types with multiple variants, each optionally carrying data. `Option<T>` replaces null, `Result<T, E>` handles errors, and `match` provides exhaustive pattern matching. These are pillars of idiomatic Rust.

---

### 9. Error Handling ⚠️

Rust takes error handling seriously. There are no exceptions — instead, Rust uses `Result<T, E>` for recoverable errors and `panic!` for unrecoverable errors.

```sh
+---------------------------------------------------+
|              RUST ERROR HANDLING                   |
+---------------------------------------------------+
|                                                    |
|  Recoverable Errors        Unrecoverable Errors    |
|  ┌────────────────┐       ┌────────────────┐      |
|  │ Result<T, E>   │       │ panic!()       │      |
|  │                │       │                │      |
|  │ Ok(value)      │       │ Program stops  │      |
|  │ Err(error)     │       │ immediately    │      |
|  │                │       │                │      |
|  │ Use: I/O,      │       │ Use: bugs,     │      |
|  │ parsing, APIs  │       │ impossible     │      |
|  │                │       │ states         │      |
|  └────────────────┘       └────────────────┘      |
|                                                    |
+---------------------------------------------------+
```

#### `panic!` — Unrecoverable Errors

When something goes catastrophically wrong and your program can't continue:

```rust
fn main() {
    // Explicit panic
    // panic!("Something went terribly wrong!");

    // Implicit panics
    let v = vec![1, 2, 3];
    // v[99];  // Index out of bounds — panics!

    println!("This only runs if nothing panicked above");
}
```

    This only runs if nothing panicked above

#### The `?` Operator — Propagating Errors

The `?` operator is Rust's elegant way to propagate errors up the call stack. If a `Result` is `Err`, `?` returns the error immediately. If it's `Ok`, it unwraps the value:

```rust
use std::num::ParseIntError;

fn parse_and_double(input: &str) -> Result<u64, ParseIntError> {
    let number = input.parse::<u64>()?;  // Returns Err early if parse fails
    Ok(number * 2)
}

fn process_transaction(amount_str: &str, fee_str: &str) -> Result<u64, ParseIntError> {
    let amount = amount_str.parse::<u64>()?;
    let fee = fee_str.parse::<u64>()?;
    Ok(amount - fee)
}

fn main() {
    // Success case
    match parse_and_double("21") {
        Ok(result) => println!("21 doubled = {}", result),
        Err(e) => println!("Error: {}", e),
    }

    // Error case
    match parse_and_double("abc") {
        Ok(result) => println!("Result: {}", result),
        Err(e) => println!("Error: {}", e),
    }

    // Chained operations
    match process_transaction("1000000", "5000") {
        Ok(result) => println!("Net amount: {} lamports", result),
        Err(e) => println!("Error: {}", e),
    }
}
```

    21 doubled = 42
    Error: invalid digit found in string
    Net amount: 995000 lamports

#### Custom Error Types

For real applications, you'll want to define your own error types:

```rust
use std::fmt;

#[derive(Debug)]
enum WalletError {
    InsufficientFunds { required: u64, available: u64 },
    InvalidAddress(String),
    NetworkError(String),
}

impl fmt::Display for WalletError {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        match self {
            WalletError::InsufficientFunds { required, available } => {
                write!(f, "Insufficient funds: need {} but only have {}", required, available)
            }
            WalletError::InvalidAddress(addr) => {
                write!(f, "Invalid address: {}", addr)
            }
            WalletError::NetworkError(msg) => {
                write!(f, "Network error: {}", msg)
            }
        }
    }
}

fn transfer(balance: u64, amount: u64, to: &str) -> Result<u64, WalletError> {
    if to.is_empty() {
        return Err(WalletError::InvalidAddress(String::from("empty address")));
    }
    if amount > balance {
        return Err(WalletError::InsufficientFunds {
            required: amount,
            available: balance,
        });
    }
    Ok(balance - amount)
}

fn main() {
    match transfer(1000, 500, "Bob") {
        Ok(new_balance) => println!("Success! New balance: {}", new_balance),
        Err(e) => println!("Failed: {}", e),
    }

    match transfer(100, 500, "Alice") {
        Ok(new_balance) => println!("Success! New balance: {}", new_balance),
        Err(e) => println!("Failed: {}", e),
    }

    match transfer(1000, 500, "") {
        Ok(new_balance) => println!("Success! New balance: {}", new_balance),
        Err(e) => println!("Failed: {}", e),
    }
}
```

    Success! New balance: 500
    Failed: Insufficient funds: need 500 but only have 100
    Failed: Invalid address: empty address

#### Combining Results with `and_then` and `map`

```rust
fn main() {
    // map: transform the Ok value
    let result: Result<i32, String> = Ok(5);
    let doubled = result.map(|x| x * 2);
    println!("Mapped: {:?}", doubled);

    // and_then: chain operations that might fail
    let result: Result<&str, String> = Ok("42");
    let parsed = result
        .map(|s| s.parse::<u64>())         // Result<Result<u64, _>, String>
        .unwrap()                            // Result<u64, ParseIntError>
        .map(|n| n * 2);                    // Result<u64, ParseIntError>
    println!("Chained: {:?}", parsed);

    // unwrap_or_else: provide a fallback with access to the error
    let bad_result: Result<u64, String> = Err(String::from("parse error"));
    let value = bad_result.unwrap_or_else(|e| {
        println!("Handling error: {}", e);
        0 // default value
    });
    println!("Value: {}", value);
}
```

    Mapped: Ok(10)
    Chained: Ok(84)
    Handling error: parse error
    Value: 0

**Key Takeaway**: Rust uses `Result<T, E>` for recoverable errors and `panic!` for unrecoverable ones. The `?` operator elegantly propagates errors. Custom error types give you full control over error reporting. Solana programs use custom error enums extensively.

---

### 10. Collections 📚

Collections are data structures that can hold multiple values. Unlike arrays and tuples, most collections store data on the **heap**, so their size can grow or shrink at runtime.

```sh
+-----------------------------------------------------+
|                RUST COLLECTIONS                      |
+-----------------------------------------------------+
|                                                      |
|   Vec<T>              HashMap<K, V>     String       |
|   ┌──────────┐       ┌──────────┐     ┌──────────┐ |
|   │ [1,2,3]  │       │ key→val  │     │ "hello"  │ |
|   │ Dynamic  │       │ key→val  │     │ UTF-8    │ |
|   │ array    │       │ key→val  │     │ growable │ |
|   └──────────┘       └──────────┘     └──────────┘ |
|                                                      |
+-----------------------------------------------------+
```

#### Vec<T> — The Dynamic Array

`Vec<T>` (vector) is the most commonly used collection. It's like an array that can grow and shrink:

```rust
fn main() {
    // Creating vectors
    let mut validators: Vec<String> = Vec::new(); // Empty vector
    let numbers = vec![1, 2, 3, 4, 5];            // Using the vec! macro

    // Adding elements
    validators.push(String::from("Alice"));
    validators.push(String::from("Bob"));
    validators.push(String::from("Charlie"));
    validators.push(String::from("Diana"));

    println!("Validators: {:?}", validators);
    println!("Count: {}", validators.len());

    // Accessing elements
    println!("First: {}", validators[0]);          // Direct index (panics if out of bounds)
    println!("Safe: {:?}", validators.get(10));     // Returns Option<&T> (safe)

    // Removing elements
    let removed = validators.pop();  // Remove last element
    println!("Removed: {:?}", removed);
    println!("After pop: {:?}", validators);

    // Iterating
    println!("\nRoll call:");
    for (i, validator) in validators.iter().enumerate() {
        println!("  {}: {}", i + 1, validator);
    }

    // Iterating with mutation
    let mut balances = vec![100, 200, 300];
    for balance in balances.iter_mut() {
        *balance += 50; // Add 50 to each balance
    }
    println!("\nUpdated balances: {:?}", balances);
}
```

    Validators: ["Alice", "Bob", "Charlie", "Diana"]
    Count: 4
    First: Alice
    Safe: None
    Removed: Some("Diana")
    After pop: ["Alice", "Bob", "Charlie"]

    Roll call:
      1: Alice
      2: Bob
      3: Charlie

    Updated balances: [150, 250, 350]

#### Useful Vector Methods

```rust
fn main() {
    let mut v = vec![5, 3, 8, 1, 9, 2, 7];

    // Sorting
    v.sort();
    println!("Sorted: {:?}", v);

    // Searching
    println!("Contains 8: {}", v.contains(&8));
    println!("Position of 8: {:?}", v.iter().position(|&x| x == 8));

    // Filtering
    let evens: Vec<&i32> = v.iter().filter(|&&x| x % 2 == 0).collect();
    println!("Evens: {:?}", evens);

    // Slicing
    let first_three = &v[0..3];
    println!("First three: {:?}", first_three);

    // Reversing
    v.reverse();
    println!("Reversed: {:?}", v);

    // Retain only elements matching a condition
    v.retain(|&x| x > 3);
    println!("Only > 3: {:?}", v);

    // Dedup (remove consecutive duplicates — sort first!)
    let mut dupes = vec![1, 1, 2, 3, 3, 3, 4];
    dupes.dedup();
    println!("Deduped: {:?}", dupes);
}
```

    Sorted: [1, 2, 3, 5, 7, 8, 9]
    Contains 8: true
    Position of 8: Some(5)
    Evens: [2, 8]
    First three: [1, 2, 3]
    Reversed: [9, 8, 7, 5, 3, 2, 1]
    Only > 3: [9, 8, 7, 5]
    Deduped: [1, 2, 3, 4]

#### HashMap<K, V> — Key-Value Pairs

`HashMap` stores key-value pairs with O(1) average lookup time:

```rust
use std::collections::HashMap;

fn main() {
    // Create a HashMap
    let mut token_balances: HashMap<String, u64> = HashMap::new();

    // Insert entries
    token_balances.insert(String::from("SOL"), 5_000_000_000);
    token_balances.insert(String::from("USDC"), 1_000_000_000);
    token_balances.insert(String::from("RAY"), 500_000_000);

    // Access a value
    match token_balances.get("SOL") {
        Some(balance) => println!("SOL balance: {} lamports", balance),
        None => println!("No SOL balance found"),
    }

    // Check if key exists
    println!("Has USDC: {}", token_balances.contains_key("USDC"));
    println!("Has BTC: {}", token_balances.contains_key("BTC"));

    // Iterate over all key-value pairs
    println!("\nAll balances:");
    for (token, balance) in &token_balances {
        println!("  {}: {} lamports", token, balance);
    }

    // Update a value
    token_balances.insert(String::from("SOL"), 6_000_000_000); // Overwrites
    println!("\nUpdated SOL: {}", token_balances["SOL"]);

    // Only insert if key doesn't exist
    token_balances.entry(String::from("BONK")).or_insert(100_000);
    token_balances.entry(String::from("SOL")).or_insert(999); // Won't overwrite
    println!("BONK: {}", token_balances["BONK"]);
    println!("SOL (unchanged): {}", token_balances["SOL"]);

    // Remove an entry
    token_balances.remove("RAY");
    println!("\nAfter removing RAY: {:?}", token_balances);
}
```

    SOL balance: 5000000000 lamports
    Has USDC: true
    Has BTC: false

    All balances:
      USDC: 1000000000 lamports
      SOL: 5000000000 lamports
      RAY: 500000000 lamports

    Updated SOL: 6000000000
    BONK: 100000
    SOL (unchanged): 6000000000

    After removing RAY: {"USDC": 1000000000, "SOL": 6000000000, "BONK": 100000}

#### A Practical Example: Word Counter

```rust
use std::collections::HashMap;

fn count_words(text: &str) -> HashMap<&str, u32> {
    let mut counts = HashMap::new();
    for word in text.split_whitespace() {
        let count = counts.entry(word).or_insert(0);
        *count += 1;
    }
    counts
}

fn main() {
    let text = "solana solana rust rust rust blockchain solana web3";
    let counts = count_words(text);

    println!("Word frequencies:");
    for (word, count) in &counts {
        println!("  '{}' appears {} time(s)", word, count);
    }
}
```

    Word frequencies:
      'rust' appears 3 time(s)
      'solana' appears 3 time(s)
      'blockchain' appears 1 time(s)
      'web3' appears 1 time(s)

#### HashSet<T> — Unique Values

```rust
use std::collections::HashSet;

fn main() {
    let mut validators: HashSet<String> = HashSet::new();

    // Insert (duplicates are ignored)
    validators.insert(String::from("Alice"));
    validators.insert(String::from("Bob"));
    validators.insert(String::from("Alice")); // Duplicate — ignored!

    println!("Validators: {:?}", validators);
    println!("Count: {}", validators.len());

    // Set operations
    let team_a: HashSet<i32> = vec![1, 2, 3, 4, 5].into_iter().collect();
    let team_b: HashSet<i32> = vec![4, 5, 6, 7, 8].into_iter().collect();

    println!("Union: {:?}", team_a.union(&team_b).collect::<Vec<_>>());
    println!("Intersection: {:?}", team_a.intersection(&team_b).collect::<Vec<_>>());
    println!("Difference (A-B): {:?}", team_a.difference(&team_b).collect::<Vec<_>>());
}
```

    Validators: {"Bob", "Alice"}
    Count: 2
    Union: [1, 2, 3, 4, 5, 6, 7, 8]
    Intersection: [4, 5]
    Difference (A-B): [1, 2, 3]

**Key Takeaway**: `Vec<T>` is a growable array, `HashMap<K, V>` stores key-value pairs, and `HashSet<T>` stores unique values. These collections store data on the heap and can grow dynamically. You'll use `Vec` and `HashMap` constantly in Solana development.

---

### 11. Traits & Generics 🧬

Traits and generics are how Rust achieves **polymorphism** — writing code that works with multiple types. Traits define shared behavior (like interfaces), and generics let you write functions and types that work with any type.

#### Traits — Defining Shared Behavior

A trait defines a set of methods that a type must implement:

```rust
trait Displayable {
    fn display(&self) -> String;

    // Default implementation (types can override this)
    fn display_fancy(&self) -> String {
        format!("✨ {} ✨", self.display())
    }
}

struct Wallet {
    address: String,
    balance: u64,
}

struct Token {
    name: String,
    symbol: String,
    decimals: u8,
}

// Implement the trait for Wallet
impl Displayable for Wallet {
    fn display(&self) -> String {
        format!("Wallet({}, {} lamports)", self.address, self.balance)
    }
}

// Implement the trait for Token
impl Displayable for Token {
    fn display(&self) -> String {
        format!("{} ({})", self.name, self.symbol)
    }

    // Override the default implementation
    fn display_fancy(&self) -> String {
        format!("🪙 {} ({}) - {} decimals 🪙", self.name, self.symbol, self.decimals)
    }
}

fn main() {
    
    let wallet = Wallet {
        address: String::from("7Xhiv..."),
        balance: 1_000_000_000,
    };

    let token = Token {
        name: String::from("Solana"),
        symbol: String::from("SOL"),
        decimals: 9,
    };

    println!("{}", wallet.display());
    println!("{}", wallet.display_fancy()); // Uses default implementation

    println!("{}", token.display());
    println!("{}", token.display_fancy());  // Uses custom implementation
}
```

    Wallet(7Xhiv..., 1000000000 lamports)
    ✨ Wallet(7Xhiv..., 1000000000 lamports) ✨
    Solana (SOL)
    🪙 Solana (SOL) - 9 decimals 🪙

#### Traits as Parameters

You can write functions that accept **any type** implementing a specific trait:

```rust
trait Summary {
    fn summarize(&self) -> String;
}

struct Transaction {
    from: String,
    to: String,
    amount: u64,
}

struct Block {
    number: u64,
    transactions: u32,
}

impl Summary for Transaction {
    fn summarize(&self) -> String {
        format!("TX: {} -> {} ({} lamports)", self.from, self.to, self.amount)
    }
}

impl Summary for Block {
    fn summarize(&self) -> String {
        format!("Block #{} with {} transactions", self.number, self.transactions)
    }
}

// This function accepts ANY type that implements Summary
fn print_summary(item: &impl Summary) {
    println!("Summary: {}", item.summarize());
}

fn main() {
    let tx = Transaction {
        from: String::from("Alice"),
        to: String::from("Bob"),
        amount: 500_000,
    };

    let block = Block {
        number: 12345,
        transactions: 150,
    };

    print_summary(&tx);
    print_summary(&block);
}
```

    Summary: TX: Alice -> Bob (500000 lamports)
    Summary: Block #12345 with 150 transactions

#### Generics — Writing Code for Multiple Types

Generics let you parameterize types and functions:

```rust
// A generic function
fn largest<T: PartialOrd>(list: &[T]) -> &T {
    let mut largest = &list[0];
    for item in list {
        if item > largest {
            largest = item;
        }
    }
    largest
}

fn main() {
    let numbers = vec![34, 50, 25, 100, 65];
    println!("Largest number: {}", largest(&numbers));

    let chars = vec!['y', 'm', 'a', 'q'];
    println!("Largest char: {}", largest(&chars));
}
```

    Largest number: 100
    Largest char: y

#### Generic Structs

```rust
#[derive(Debug)]
struct Pair<T> {
    first: T,
    second: T,
}

impl<T: std::fmt::Display> Pair<T> {
    fn new(first: T, second: T) -> Pair<T> {
        Pair { first, second }
    }

    fn display(&self) {
        println!("({}, {})", self.first, self.second);
    }
}

// Structs with multiple generic types
#[derive(Debug)]
struct KeyValue<K, V> {
    key: K,
    value: V,
}

fn main() {
    let int_pair = Pair::new(1, 2);
    let str_pair = Pair::new("hello", "world");

    int_pair.display();
    str_pair.display();

    let entry = KeyValue {
        key: String::from("SOL"),
        value: 5_000_000_000u64,
    };
    println!("{:?}", entry);
}
```

    (1, 2)
    (hello, world)
    KeyValue { key: "SOL", value: 5000000000 }

#### Trait Bounds — Constraining Generics

You can require that generic types implement specific traits:

```rust
use std::fmt::Display;

// Multiple trait bounds with +
fn print_if_positive<T: Display + PartialOrd + Default>(value: T) {
    if value > T::default() {
        println!("Positive: {}", value);
    } else {
        println!("Not positive: {}", value);
    }
}

// Where clause for complex bounds (cleaner syntax)
fn process<T, U>(t: T, u: U)
where
    T: Display + Clone,
    U: Display + std::fmt::Debug,
{
    println!("T: {}, U: {:?}", t, u);
}

fn main() {
    print_if_positive(42);
    print_if_positive(-5);
    print_if_positive(0.0);
    print_if_positive(3.14);

    process("hello", vec![1, 2, 3]);
}
```

    Positive: 42
    Not positive: -5
    Not positive: 0
    Positive: 3.14
    T: hello, U: [1, 2, 3]

#### Common Standard Library Traits

These traits come up everywhere in Rust and Solana development:

| Trait | Purpose | Example |
|-------|---------|---------|
| `Display` | Human-readable string output | `println!("{}", x)` |
| `Debug` | Developer-readable debug output | `println!("{:?}", x)` |
| `Clone` | Deep copy | `let y = x.clone()` |
| `Copy` | Implicit copy for stack types | `let y = x` (no move) |
| `PartialEq` / `Eq` | Equality comparison | `x == y` |
| `PartialOrd` / `Ord` | Ordering comparison | `x > y`, sorting |
| `Default` | Default value | `T::default()` |
| `From` / `Into` | Type conversion | `String::from("hi")` |
| `Iterator` | Iteration | `for x in iter` |

**Key Takeaway**: Traits define shared behavior (like interfaces), generics enable code reuse across types, and trait bounds constrain generics. Together, they form Rust's powerful polymorphism system. Solana uses traits extensively — `Signer`, `Borsh` serialization, `AccountDeserialize`, etc.

---

### 12. Iterators & Closures 🔄

Iterators and closures are Rust's way of doing **functional programming**. They let you process collections in elegant, chainable pipelines — and they compile down to the same speed as hand-written loops.

#### Closures — Anonymous Functions

Closures are anonymous functions that can capture variables from their environment:

```rust
fn main() {
    // Basic closure syntax
    let add = |a: i32, b: i32| -> i32 { a + b };
    println!("3 + 4 = {}", add(3, 4));

    // Types can often be inferred
    let double = |x| x * 2;
    println!("Double 5 = {}", double(5));

    // Closures capture their environment
    let base_fee: u64 = 5000;
    let calculate_total = |amount: u64| amount + base_fee;
    println!("Total: {}", calculate_total(1_000_000));

    // Multi-line closures
    let classify = |balance: u64| {
        if balance > 1_000_000_000 {
            "whale"
        } else if balance > 1_000_000 {
            "standard"
        } else {
            "micro"
        }
    };

    println!("1B lamports: {}", classify(1_000_000_000));
    println!("500K lamports: {}", classify(500_000));

    // Closures that mutate captured variables
    let mut count = 0;
    let mut increment = || {
        count += 1;
        count
    };
    println!("Count: {}", increment());
    println!("Count: {}", increment());
    println!("Count: {}", increment());
}
```

    3 + 4 = 7
    Double 5 = 10
    Total: 1005000
    1B lamports: standard
    500K lamports: micro
    Count: 1
    Count: 2
    Count: 3

#### Iterators — Processing Sequences

An iterator produces a sequence of values one at a time. The core trait is:

```rust
// Simplified Iterator trait
// trait Iterator {
//     type Item;
//     fn next(&mut self) -> Option<Self::Item>;
// }

fn main() {
    let numbers = vec![1, 2, 3, 4, 5];

    // Manual iteration with next()
    let mut iter = numbers.iter();
    println!("First:  {:?}", iter.next());  // Some(1)
    println!("Second: {:?}", iter.next());  // Some(2)
    println!("Third:  {:?}", iter.next());  // Some(3)

    // for loop uses iterators under the hood
    for num in numbers.iter() {
        print!("{} ", num);
    }
    println!();
}
```

    First:  Some(1)
    Second: Some(2)
    Third:  Some(3)
    1 2 3 4 5

#### Iterator Adaptors — The Power of Chaining

Iterator adaptors transform iterators into other iterators. They're **lazy** — they do nothing until you consume them:

```rust
fn main() {
    let transactions = vec![100, 5000, 250, 10000, 50, 7500, 300];

    // map: transform each element
    let doubled: Vec<i32> = transactions.iter().map(|&x| x * 2).collect();
    println!("Doubled: {:?}", doubled);

    // filter: keep only matching elements
    let large: Vec<&i32> = transactions.iter().filter(|&&x| x > 1000).collect();
    println!("Large (>1000): {:?}", large);

    // Chain multiple adaptors together!
    let result: Vec<i32> = transactions
        .iter()
        .filter(|&&x| x > 100)      // Keep transactions > 100
        .map(|&x| x - 50)            // Subtract fee of 50
        .filter(|&x| x > 200)        // Only keep results > 200
        .collect();
    println!("Processed: {:?}", result);

    // sum: add all elements
    let total: i32 = transactions.iter().sum();
    println!("Total: {}", total);

    // min and max
    println!("Min: {:?}", transactions.iter().min());
    println!("Max: {:?}", transactions.iter().max());

    // count with filter
    let large_count = transactions.iter().filter(|&&x| x > 1000).count();
    println!("Large transactions: {}", large_count);

    // any: check if any element matches
    let has_whale = transactions.iter().any(|&x| x > 5000);
    println!("Has whale transaction: {}", has_whale);

    // all: check if all elements match
    let all_positive = transactions.iter().all(|&x| x > 0);
    println!("All positive: {}", all_positive);

    // find: get first matching element
    let first_large = transactions.iter().find(|&&x| x > 5000);
    println!("First large: {:?}", first_large);
}
```

    Doubled: [200, 10000, 500, 20000, 100, 15000, 600]
    Large (>1000): [5000, 10000, 7500]
    Processed: [4950, 9950, 7450, 250]
    Total: 23200
    Min: Some(50)
    Max: Some(10000)
    Large transactions: 3
    Has whale transaction: true
    All positive: true
    First large: Some(10000)

#### Practical Example: Processing Validator Data

```rust
#[derive(Debug)]
struct Validator {
    name: String,
    stake: u64,
    active: bool,
}

fn main() {
    let validators = vec![
        Validator { name: String::from("Alice"),   stake: 10_000, active: true },
        Validator { name: String::from("Bob"),     stake: 5_000,  active: false },
        Validator { name: String::from("Charlie"), stake: 15_000, active: true },
        Validator { name: String::from("Diana"),   stake: 8_000,  active: true },
        Validator { name: String::from("Eve"),     stake: 3_000,  active: false },
    ];

    // Get names of active validators with stake > 7000
    let qualified: Vec<&String> = validators
        .iter()
        .filter(|v| v.active && v.stake > 7_000)
        .map(|v| &v.name)
        .collect();
    println!("Qualified validators: {:?}", qualified);

    // Total stake of active validators
    let total_active_stake: u64 = validators
        .iter()
        .filter(|v| v.active)
        .map(|v| v.stake)
        .sum();
    println!("Total active stake: {}", total_active_stake);

    // Count active vs inactive
    let active_count = validators.iter().filter(|v| v.active).count();
    let inactive_count = validators.len() - active_count;
    println!("Active: {}, Inactive: {}", active_count, inactive_count);

    // Find highest-staked validator
    let top_validator = validators.iter().max_by_key(|v| v.stake);
    println!("Top validator: {:?}", top_validator);

    // Partition into two groups
    let (active, inactive): (Vec<&Validator>, Vec<&Validator>) = validators
        .iter()
        .partition(|v| v.active);
    println!("\nActive validators:");
    for v in &active {
        println!("  {} (stake: {})", v.name, v.stake);
    }
    println!("Inactive validators:");
    for v in &inactive {
        println!("  {} (stake: {})", v.name, v.stake);
    }
}
```

    Qualified validators: ["Alice", "Diana"]
    Total active stake: 33000
    Active: 3, Inactive: 2
    Top validator: Some(Validator { name: "Charlie", stake: 15000, active: true })

    Active validators:
      Alice (stake: 10000)
      Charlie (stake: 15000)
      Diana (stake: 8000)
    Inactive validators:
      Bob (stake: 5000)
      Eve (stake: 3000)

**Key Takeaway**: Closures are anonymous functions that capture their environment. Iterators process sequences lazily with chainable adaptors like `map`, `filter`, `sum`, and `collect`. This functional style is idiomatic Rust and compiles to zero-overhead machine code.

---

### 13. Lifetimes 🕐

Lifetimes are Rust's way of ensuring that **references are always valid**. Every reference in Rust has a lifetime — the scope for which that reference is valid. Most of the time, lifetimes are inferred by the compiler, but sometimes you need to annotate them explicitly.

#### Why Lifetimes?

Consider this problematic code (it won't compile):

```rust
// fn dangling_reference() -> &String {  // ERROR! What is this reference pointing to?
//     let s = String::from("hello");
//     &s  // s is dropped at end of function — reference would be dangling!
// }
```

Lifetimes prevent this class of bug entirely. The compiler tracks how long each reference lives and ensures they never outlive the data they point to.

#### Lifetime Annotations

Lifetime annotations don't change how long references live — they describe the **relationships** between lifetimes of multiple references:

```rust
// 'a is a lifetime parameter — it says: the returned reference
// lives at least as long as both input references
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}

fn main() {
    let string1 = String::from("long string");

    {
        let string2 = String::from("xyz");
        let result = longest(string1.as_str(), string2.as_str());
        println!("Longest: {}", result);
    }
}
```

    Longest: long string

#### Lifetimes in Structs

When structs hold references, they need lifetime annotations:

```rust
#[derive(Debug)]
struct AccountView<'a> {
    address: &'a str,
    balance: u64,
}

impl<'a> AccountView<'a> {
    fn display(&self) {
        println!("Account {}: {} lamports", self.address, self.balance);
    }
}

fn main() {
    let address = String::from("7XhivnMM...");
    let view = AccountView {
        address: &address,
        balance: 1_000_000_000,
    };

    view.display();
    println!("{:?}", view);
}
```

    Account 7XhivnMM...: 1000000000 lamports
    AccountView { address: "7XhivnMM...", balance: 1000000000 }

#### The `'static` Lifetime

`'static` means the reference lives for the entire duration of the program. String literals are `'static`:

```rust
fn main() {
    // String literals have a 'static lifetime — they're baked into the binary
    let s: &'static str = "I live forever!";
    println!("{}", s);
}
```

    I live forever!

#### Lifetime Elision Rules

Most of the time, you don't need to write lifetime annotations because of **elision rules** — the compiler infers them:

```rust
// These two signatures are equivalent:
// fn first_word<'a>(s: &'a str) -> &'a str { ... }
fn first_word(s: &str) -> &str {       // Lifetimes are inferred!
    let bytes = s.as_bytes();
    for (i, &byte) in bytes.iter().enumerate() {
        if byte == b' ' {
            return &s[..i];
        }
    }
    s
}

fn main() {
    let sentence = String::from("hello world blockchain");
    let word = first_word(&sentence);
    println!("First word: {}", word);
}
```

    First word: hello

The three elision rules are:
1. Each reference parameter gets its own lifetime
2. If there's exactly one input lifetime, it's assigned to all output lifetimes
3. If one of the parameters is `&self` or `&mut self`, its lifetime is assigned to all output lifetimes

**Key Takeaway**: Lifetimes ensure references are always valid. They describe relationships between reference lifetimes. The compiler infers them most of the time, but you'll need explicit annotations when working with multiple references or structs holding references.

---

### 14. Modules, Crates & Cargo 📦

As your Rust programs grow, you need to organize code into logical units. Rust provides **modules** for code organization, **crates** as compilation units, and **Cargo** as the build system and package manager.

```sh
+------------------------------------------------------+
|              RUST CODE ORGANIZATION                   |
+------------------------------------------------------+
|                                                       |
|  Crate (compilation unit)                             |
|  ├── src/                                             |
|  │   ├── main.rs (binary crate root)                  |
|  │   ├── lib.rs  (library crate root)                 |
|  │   └── modules/                                     |
|  │       ├── mod.rs                                   |
|  │       ├── accounts.rs                              |
|  │       └── transactions.rs                          |
|  ├── Cargo.toml (manifest — dependencies, metadata)   |
|  └── Cargo.lock (exact dependency versions)           |
|                                                       |
+------------------------------------------------------+
```

#### Modules — Organizing Code

Modules let you organize code within a crate into logical groups:

```rust
// Define modules
mod wallet {
    pub struct Wallet {
        pub address: String,
        balance: u64,  // private by default!
    }

    impl Wallet {
        pub fn new(address: String, balance: u64) -> Wallet {
            Wallet { address, balance }
        }

        pub fn balance(&self) -> u64 {
            self.balance
        }

        pub fn deposit(&mut self, amount: u64) {
            self.balance += amount;
        }

        // Private helper function
        fn validate_amount(amount: u64) -> bool {
            amount > 0
        }
    }

    // Nested module
    pub mod utils {
        pub fn lamports_to_sol(lamports: u64) -> f64 {
            lamports as f64 / 1_000_000_000.0
        }
    }
}

fn main() {
    // Use the module's items
    let mut w = wallet::Wallet::new(String::from("7Xhiv..."), 1_000_000_000);

    println!("Address: {}", w.address);
    println!("Balance: {} lamports", w.balance()); // Use public method

    w.deposit(500_000_000);
    println!("After deposit: {} lamports", w.balance());

    // Use nested module
    let sol = wallet::utils::lamports_to_sol(w.balance());
    println!("Balance in SOL: {:.2}", sol);
}
```

    Address: 7Xhiv...
    Balance: 1000000000 lamports
    After deposit: 1500000000 lamports
    Balance in SOL: 1.50

#### Visibility: `pub` Keyword

By default, everything in Rust is **private**. Use `pub` to make items accessible outside their module:

- `pub` — accessible from anywhere
- `pub(crate)` — accessible within the current crate only
- `pub(super)` — accessible from the parent module
- (no modifier) — private to the current module

#### `use` — Bringing Paths into Scope

```rust
// Instead of writing the full path every time:
// std::collections::HashMap::new()

// Bring it into scope:
use std::collections::HashMap;

// Multiple items from the same module
use std::collections::{BTreeMap, HashSet};

// Rename on import
use std::collections::HashMap as Map;

// Glob import (use sparingly!)
// use std::collections::*;

fn main() {
    let mut balances: HashMap<String, u64> = HashMap::new();
    balances.insert(String::from("SOL"), 1_000_000);
    println!("{:?}", balances);

    let mut ordered: BTreeMap<String, u64> = BTreeMap::new();
    ordered.insert(String::from("A"), 1);
    ordered.insert(String::from("B"), 2);
    println!("{:?}", ordered);
}
```

    {"SOL": 1000000}
    {"A": 1, "B": 2}

#### Cargo.toml — Dependency Management

`Cargo.toml` is your project's manifest. Here's what a Solana project looks like:

```toml
[package]
name = "my-solana-project"
version = "0.1.0"
edition = "2021"

[dependencies]
solana-sdk = "1.17"
solana-client = "1.17"
borsh = "0.10"
serde = { version = "1.0", features = ["derive"] }
serde_json = "1.0"
```

#### Common Cargo Commands

```sh
cargo new my_project          # Create a new project
cargo build                   # Compile the project
cargo run                     # Compile and run
cargo test                    # Run tests
cargo doc --open              # Generate and open documentation
cargo add serde               # Add a dependency
cargo update                  # Update dependencies
cargo fmt                     # Format code
cargo clippy                  # Lint code
```

**Key Takeaway**: Modules organize code with visibility controls (`pub`). Crates are the compilation unit. Cargo is the build system that handles dependencies, compilation, testing, and more. `use` brings items into scope to avoid long paths.

---

### 15. Common Standard Library Types 🧰

Rust's standard library provides several crucial types you'll encounter constantly in Solana development.

#### Box<T> — Heap Allocation

`Box<T>` puts data on the heap instead of the stack:

```rust
fn main() {
    // Stack allocation (normal)
    let x = 5;

    // Heap allocation with Box
    let y = Box::new(5);
    println!("y = {}", y); // Dereferenced automatically

    // Useful for recursive types
    #[derive(Debug)]
    enum List {
        Cons(i32, Box<List>),
        Nil,
    }

    let list = List::Cons(1,
        Box::new(List::Cons(2,
            Box::new(List::Cons(3,
                Box::new(List::Nil))))));

    println!("{:?}", list);
}
```

    y = 5
    Cons(1, Cons(2, Cons(3, Nil)))

#### Rc<T> and RefCell<T> — Shared Ownership

Sometimes you need multiple owners of the same data. `Rc<T>` (Reference Counted) enables this. `RefCell<T>` provides interior mutability:

```rust
use std::rc::Rc;
use std::cell::RefCell;

fn main() {
    // Rc: multiple owners of the same data
    let shared_data = Rc::new(String::from("shared account data"));
    let owner1 = Rc::clone(&shared_data);
    let owner2 = Rc::clone(&shared_data);

    println!("Reference count: {}", Rc::strong_count(&shared_data));
    println!("Owner 1 sees: {}", owner1);
    println!("Owner 2 sees: {}", owner2);

    // RefCell: interior mutability (mutable borrow checked at RUNTIME)
    let balance = RefCell::new(1000u64);

    // Borrow immutably
    println!("Balance: {}", balance.borrow());

    // Borrow mutably
    *balance.borrow_mut() += 500;
    println!("After deposit: {}", balance.borrow());

    // Combining Rc and RefCell for shared mutable state
    let shared_balance = Rc::new(RefCell::new(1000u64));
    let handle1 = Rc::clone(&shared_balance);
    let handle2 = Rc::clone(&shared_balance);

    *handle1.borrow_mut() += 100;
    *handle2.borrow_mut() += 200;
    println!("Shared balance: {}", shared_balance.borrow());
}
```

    Reference count: 3
    Owner 1 sees: shared account data
    Owner 2 sees: shared account data
    Balance: 1000
    After deposit: 1500
    Shared balance: 1300

**Why this matters for Solana**: In Solana's `AccountInfo`, you'll see `Rc<RefCell<&mut [u8]>>` for account data and `Rc<RefCell<&mut u64>>` for lamports — this is exactly the `Rc` + `RefCell` pattern! It allows multiple parts of the program to access and modify account data safely.

#### Type Aliases

```rust
type Lamports = u64;
type Address = String;
type AccountResult<T> = Result<T, String>;

fn get_balance(address: &Address) -> AccountResult<Lamports> {
    if address.is_empty() {
        Err(String::from("Invalid address"))
    } else {
        Ok(1_000_000_000)
    }
}

fn main() {
    let addr: Address = String::from("7Xhiv...");
    match get_balance(&addr) {
        Ok(balance) => println!("Balance: {} lamports", balance),
        Err(e) => println!("Error: {}", e),
    }
}
```

    Balance: 1000000000 lamports

**Key Takeaway**: `Box<T>` enables heap allocation, `Rc<T>` allows shared ownership through reference counting, and `RefCell<T>` provides interior mutability with runtime borrow checking. You'll encounter `Rc<RefCell<T>>` directly in Solana's `AccountInfo` struct.

---

### 16. Macros 🪄

Macros are code that writes code — they expand at compile time into regular Rust code. You've already been using macros: `println!`, `vec!`, `format!`. Understanding macros is important because Solana frameworks like [**Anchor**](https://www.anchor-lang.com/) use them heavily.

#### Why Macros?

```sh
+---------------------------------------------------+
|              FUNCTIONS vs MACROS                   |
+---------------------------------------------------+
|                                                    |
|  Functions                 Macros                  |
|  ┌──────────────────┐    ┌──────────────────┐     |
|  │ Fixed parameters  │    │ Variable args    │     |
|  │ Fixed return type │    │ Generate code    │     |
|  │ Runtime execution │    │ Compile-time     │     |
|  │ No code gen       │    │ expansion        │     |
|  └──────────────────┘    └──────────────────┘     |
|                                                    |
|  Use functions by default.                         |
|  Use macros when functions can't do the job.       |
+---------------------------------------------------+
```

#### Declarative Macros with `macro_rules!`

Declarative macros use pattern matching to generate code:

```rust
// A simple macro that creates a Vec with debug printing
macro_rules! debug_vec {
    ( $( $x:expr ),* ) => {
        {
            let mut temp_vec = Vec::new();
            $(
                println!("Adding: {:?}", $x);
                temp_vec.push($x);
            )*
            temp_vec
        }
    };
}

fn main() {
    let v = debug_vec![1, 2, 3];
    println!("Result: {:?}", v);
}
```

    Adding: 1
    Adding: 2
    Adding: 3
    Result: [1, 2, 3]

#### Practical Macro: Quick HashMap Creation

```rust
macro_rules! hashmap {
    ( $( $key:expr => $value:expr ),* $(,)? ) => {
        {
            let mut map = std::collections::HashMap::new();
            $( map.insert($key, $value); )*
            map
        }
    };
}

fn main() {
    let balances = hashmap! {
        "SOL" => 5_000_000_000u64,
        "USDC" => 1_000_000u64,
        "RAY" => 500_000u64,
    };

    for (token, balance) in &balances {
        println!("{}: {} lamports", token, balance);
    }
}
```

    SOL: 5000000000 lamports
    RAY: 500000 lamports
    USDC: 1000000 lamports

#### Common Built-in Macros

```rust
fn main() {
    // println! / print! — formatted output
    println!("Hello, {}!", "world");
    println!("Debug: {:?}", vec![1, 2, 3]);
    println!("Padded: {:>10}", "right");
    println!("Hex: {:x}", 255);
    println!("Binary: {:b}", 10);

    // format! — returns a String instead of printing
    let msg = format!("{} has {} SOL", "Alice", 5.0);
    println!("{}", msg);

    // vec! — creates a vector
    let v = vec![0; 5]; // Five zeros
    println!("Vec: {:?}", v);

    // dbg! — debug print that shows expression AND value
    let x = 5;
    dbg!(x * 2);  // Prints: [src/main.rs:XX] x * 2 = 10

    // todo! — marks unfinished code (panics at runtime)
    // todo!("implement this later");

    // assert! / assert_eq! / assert_ne! — testing assertions
    assert!(1 + 1 == 2);
    assert_eq!(4, 2 + 2);
    assert_ne!(3, 2 + 2);
    println!("All assertions passed!");

    // include_str! — include file contents as a string at compile time
    // let config = include_str!("config.json");

    // cfg! — conditional compilation
    if cfg!(target_os = "macos") {
        println!("Running on macOS");
    }
}
```

    Hello, world!
    Debug: [1, 2, 3]
    Padded:      right
    Hex: ff
    Binary: 1010
    Alice has 5 SOL
    Vec: [0, 0, 0, 0, 0]
    [src/main.rs:XX] x * 2 = 10
    All assertions passed!
    Running on macOS

#### Derive Macros in Solana

In Solana/Anchor development, you'll see derive macros everywhere:

```rust
// Example of what Solana/Anchor code looks like:
// (This won't compile without the Anchor framework, but shows the pattern)

// use anchor_lang::prelude::*;
//
// #[derive(AnchorSerialize, AnchorDeserialize, Clone, Debug)]
// pub struct TransferArgs {
//     pub amount: u64,
//     pub memo: String,
// }
//
// #[program]
// pub mod my_program {
//     use super::*;
//
//     pub fn transfer(ctx: Context<Transfer>, args: TransferArgs) -> Result<()> {
//         // Program logic here
//         Ok(())
//     }
// }

// For now, here's a simpler derive example you can run:
use std::fmt;

#[derive(Debug, Clone, PartialEq)]
struct TokenAccount {
    mint: String,
    owner: String,
    amount: u64,
}

impl fmt::Display for TokenAccount {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "TokenAccount({}: {} owned by {})", self.mint, self.amount, self.owner)
    }
}

fn main() {
    let account = TokenAccount {
        mint: String::from("SOL"),
        owner: String::from("Alice"),
        amount: 1_000_000_000,
    };

    // Debug (from #[derive(Debug)])
    println!("{:?}", account);

    // Display (from manual impl)
    println!("{}", account);

    // Clone (from #[derive(Clone)])
    let account2 = account.clone();
    println!("Cloned: {}", account2);

    // PartialEq (from #[derive(PartialEq)])
    println!("Equal: {}", account == account2);
}
```

    TokenAccount { mint: "SOL", owner: "Alice", amount: 1000000000 }
    TokenAccount(SOL: 1000000000 owned by Alice)
    Cloned: TokenAccount(SOL: 1000000000 owned by Alice)
    Equal: true

**Key Takeaway**: Macros generate code at compile time. Declarative macros (`macro_rules!`) use pattern matching, while derive macros auto-implement traits. Solana frameworks like Anchor rely heavily on macros for boilerplate reduction. You don't need to write macros from scratch, but understanding how they work will help you read Solana code.

---

## Conclusion

Congratulations! 🎉 You've just completed a comprehensive Rust bootcamp from the ground up. Let's recap what you've learned:

```sh
+-------------------------------------------------------------------+
|                    YOUR RUST TOOLKIT                               |
+-------------------------------------------------------------------+
|                                                                    |
|  ✅ Variables, mutability, and shadowing                          |
|  ✅ All data types: integers, floats, bools, chars, tuples,      |
|     arrays, strings                                                |
|  ✅ Functions with parameters and return values                   |
|  ✅ Control flow: if/else, loop, while, for, match               |
|  ✅ Ownership, borrowing, and references (THE core concept)       |
|  ✅ Structs with methods and derive macros                        |
|  ✅ Enums, Option<T>, Result<T,E>, and pattern matching           |
|  ✅ Error handling with ? operator and custom errors              |
|  ✅ Collections: Vec, HashMap, HashSet                            |
|  ✅ Traits and generics for polymorphism                          |
|  ✅ Iterators and closures for functional programming             |
|  ✅ Lifetimes for reference safety                                |
|  ✅ Modules, crates, and Cargo                                    |
|  ✅ Standard library types: Box, Rc, RefCell                      |
|  ✅ Macros: declarative and derive                                |
|                                                                    |
+-------------------------------------------------------------------+
```

With this solid Rust foundation, you're fully prepared to dive into **Chapter 1** and begin your Solana development journey. The ownership model you learned here will make Solana's account system intuitive. The `Result` and `Option` types will feel natural in program error handling. And the structs, enums, and traits you practiced are the exact building blocks of Solana programs.

Remember: Rust's compiler is your **best friend**, not your enemy. Those error messages that seem annoying are actually catching bugs that would have been nightmares in production. Embrace the borrow checker — it's making you a better developer.

Now, onwards to **Chapter 1: Web3 & Solana Basics**! 🚀

---
---
