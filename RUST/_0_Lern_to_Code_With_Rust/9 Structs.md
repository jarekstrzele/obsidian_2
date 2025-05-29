[[_0 spis]]
#rust/struct 

# Define a Struct
>[!success] `struct`
> A `struct` (structure) is a container for related pieces of data.
>
> Rust Has 3 kinds of structs:
> - named Field Structs
> - Tuple-like Structs
> - Unit-Like Structs
>


## named Field Structs
- a struct can store multiple pieces of data of different types
- each piece of data has an associated name - (FIELD, MEMBER of the struct)
- field is a variable living inside the struct, it is a name for a corresponding value
- the order of these fields is irrelevant
-  ==A struct is the owner of its fields==
- ==a field in turn owns its value==
- 

```rust
fn main() {
    struct Coffee{
        price: f64,
        name: String,
        is_hot: bool
    }
}
```


# Create a Struct instance
>[!success] instance
>An **instance** us the concrete value made from a type 

```rust
fn main() {
    struct Coffee{
        price: f64,
        name: String,
        is_hot: bool
    }
    
    let mocha: Coffee = Coffee{
        is_hot: true,
        name: String::from("Mocha"),
        price: 44.90,
    } ;
    
   
}
```


# Access Struct Fields `struct.field`
`mocha` is the owner of:
- `price`
	- it is the owner of `44.90`
- `name`
	- it is the owner of `Mocha`
- `is_hot`
	- it is the owner of `true`


```rust

fn main() {
    struct Coffee{
        price: f64,
        name: String,
        is_hot: bool
    }
    
    let mocha: Coffee = Coffee{
        is_hot: true,
        name: String::from("Mocha"),
        price: 44.90,
    } ;
    
    println!("My {} cost {}, it is {} that it was hot", mocha.name, mocha.price, mocha.is_hot) ;
    // output:
    // My Mocha cost 44.9, it is true that it was hot
    
    
    let favorite_coffee: String = mocha.name ; // that moves the ownershipt from macha.name to favorite_coffee
    let price: f64 = mocha.price ; //that copies a value 44.90 
    println!("favorite coffee {favorite_coffee}") ; // favorite coffee Mocha
    
    println!("mocha.name {}", mocha.name) ; // error
    // et favorite_coffee: String = mocha.name ; 
    // that moves the ownershipt from macha.name to favorite_coffee
   |//                                   ---------- value moved here
}

```


# Overwrite Struct Field
```rust
fn main() {
    struct Coffee{
        price: f64,
        name: String,
        is_hot: bool
    }
    
    let mut beverage: Coffee = Coffee{
        is_hot: true,
        name: String::from("Mocha"),
        price: 44.90,
    } ;
    
    beverage.name = String::from("BEVERAGE");
    beverage.price = 6.99;
    beverage.is_hot = false ;
    println!("My {} cost {}, it is {} that it was hot",
    beverage.name, beverage.price, beverage.is_hot) ;
    // output
    // My BEVERAGE cost 6.99, it is false that it was hot
    
}
```


# Create Structs in a Function
```rust
// struct at the file level
struct Coffee{
        price: f64,
        name: String,
        is_hot: bool,
}
    

fn main() {
    let name: String = String::from("Latte");
    let coffee: Coffee = make_coffee(name, 4.99, false) ;// "name" is pass in, so ownership is moved
    // Ownership is moves from the parameter to the name field and all these
    // three fields are captured within the "Coffee" instance
   
    println!(
        "My {}, costs {}, It is {} that it was hot",
        coffee.name, coffee.price, coffee.is_hot
    );
}

```

shortcut
```rust
struct Coffee{
        price: f64,
        name: String,
        is_hot: bool,
}
    

fn main(){
	let name: String = String::from("Mocha") ;
    let price: f64 = 3.22;
    let is_hot: bool = true;
    let mocha:Coffee= Coffee{
        name, 
        price,
        is_hot
    };
}

fn make_coffee(name: String, price: f64, is_hot:bool) -> Coffee{
    //shortcut
    Coffee{
        name,
        price,
        is_hot
    }
}
```

---
# Struct Update Syntax (destructurisation)

```rust
struct Coffee{
        price: f64,
        name: String,
        is_hot: bool,
}
    


fn main(){
	let name: String = String::from("Mocha") ;
    let price: f64 = 3.22;
    let is_hot: bool = true;
    let mocha:Coffee= Coffee{
        name, 
        price,
        is_hot
    };
    
    // STRUCT UPDATE SYNTAX
    let mocha2: Coffee = Coffee{
        /*
        name: mocha.name,     // move ownership NOT COPY
        price: mocha.price,   // copy
        is_hot: mocha.is_hot, // copy
        */
        ..mocha
    };
    
    
    // println!("mocha.name {}", mocha.name) ; //  = note: move occurs because `mocha.name` 
    // has type `String`, which does not implement the `Copy` trait
    
    let mocha3: Coffee = Coffee{
        name: mocha2.name.clone(),
        ..mocha2
    };
    println!("Moch2 {}", mocha2.name) ; // Moch2 Mocha
    println!("Mocha3 {}", mocha3.name); // Mocha3 Mocha
    
}

fn make_coffee(name: String, price: f64, is_hot:bool) -> Coffee{
    //shortcut
    Coffee{
        name,
        price,
        is_hot
    }
}
```


# Passing Structs to Functions
## Passing an instance (moving ownership)
### immutable  way
```rust
struct Coffee{
        price: f64,
        name: String,
        is_hot: bool,
}
    


fn main(){
	let name: String = String::from("Mocha") ;
    let price: f64 = 3.22;
    let is_hot: bool = true;
    let mocha:Coffee= Coffee{
        name, 
        price,
        is_hot
    };
    
    drink_coffee(mocha) ; // Dinking my delicious Mocha
    //println!("mocha.name {}", mocha.name) ; //  borrow of moved value: `mocha`
    
   
}

// "coffee" will be a new owner
// after that function "coffee" is done, no longer exists in memory
// "coffee" is immutable
fn drink_coffee(coffee: Coffee){
    println!("Dinking my delicious {}", coffee.name)
}
```


### mutable way
```rust


// "coffee" will be a new owner
// after that function "coffee" is done, no longer exists in memory
// "coffee" is immutable
fn drink_coffee(mut coffee: Coffee){
    coffee.is_hot = false;
    println!("Dinking my delicious {} that is hot: {}", coffee.name, coffee.is_hot) ; // Dinking my delicious Mocha that is hot: false
    
}
```



## Passing  a reference
### immutable way
```rust

fn main(){
	let name: String = String::from("Mocha") ;
    let price: f64 = 3.22;
    let is_hot: bool = true;
    let mocha:Coffee= Coffee{
        name, 
        price,
        is_hot
    };
    
    drink_coffee(&mocha) ; // Dinking my delicious Mocha that is hot: true
    println!("mocha.name {}", mocha.name) ; //  mocha.name Mocha

    
   
}

// passing a reference
fn drink_coffee(coffee: &Coffee){
   // coffee.is_hot = false;
    println!("Dinking my delicious {} that is hot: {}", 
                    coffee.name, // Rust automatically dereferences 
                    coffee.is_hot) ; // Dinking my delicious Mocha that is hot: true
    
}
```



### mutable way
```rust
struct Coffee{
        price: f64,
        name: String,
        is_hot: bool,
}
    


fn main(){
	let name: String = String::from("Mocha") ;
    let price: f64 = 3.22;
    let is_hot: bool = true;

	// mutable
    let mut mocha:Coffee= Coffee{
        name, 
        price,
        is_hot
    };
    
    drink_coffee(&mut mocha) ; // Dinking my delicious Mocha that is hot: true
    println!("mocha.name {}", mocha.name) ; //  mocha.name Mocha

    
   
}

// passing a reference
fn drink_coffee(coffee: &mut Coffee){
    coffee.is_hot = false;
    println!("Dinking my delicious {} that is hot: {}", 
                    coffee.name, // Rust automatically dereferences 
                    coffee.is_hot) ; // Dinking my delicious Mocha that is hot: false
    
}


fn make_coffee(name: String, price: f64, is_hot:bool) -> Coffee{
    //shortcut
    Coffee{
        name,
        price,
        is_hot
    }
}
```


------
# Deriving Debug Trait for Struct (`#[]`)
#rust/attribute 
>[!info] attribute
>- An attribute is a directive to the compile.
>- It is metadata on the line above a construct that customizes how the compiler parses the code



**derive** means "to infer" or "to deduce" or "to figure out"

#rust/trait/debug 
>[!info] trait
>a trait is a contract that mandates that a type will implement some methods

>[!info] Display, Debug - traits
>A type that implements either the Display or Debug trait promises that it can be represented as a string

```rust
let values: [&str; 3] = ["ala", "ma", "kota" ] ;
    // println!("values: {}", values) ; // `[&str; 3]` doesn't implement `std::fmt::Display`
    
    // str implements Debug trait
    println!("{:?}", values) ; //  ["ala", "ma", "kota"]
    println!("{:#?}", values) ;
    /*
    [
    "ala",
    "ma",
    "kota",
    ]
    */
```


`struct` **does not implement**:
- debug
- display


```rust

#[derive(Debug)]
struct Coffee{
        price: f64,
        name: String,
        is_hot: bool,
}
    


fn main(){
	let name: String = String::from("Mocha") ;
    let price: f64 = 3.22;
    let is_hot: bool = true;
    let mut mocha:Coffee= Coffee{
        name, 
        price,
        is_hot
    };
    
    println!("{:?}", mocha) ; // Coffee { price: 3.22, name: "Mocha", is_hot: true }

    println!("{:#?}", mocha) ;
    /*
	Coffee {
	    price: 3.22,
	    name: "Mocha",
	    is_hot: true,
	}
	*/
}
```

------

# Defining Struct Methods
#rust/method

>[!info] method
>- a method is a function that belongs to an instance
>- `value.method()`


## `self` parameter as immutable struct instance

```rust

#[derive(Debug)]
struct TaylorSwiftSong{
    title: String,
    release_year: u32,
    duration_secs: u32,
}
    
impl TaylorSwiftSong{
    fn display_song_info(self){
        // self - immutable struct value (self parameter takes ownership)
            // (self: TaylorSwiftSong) == (self: Self)
        println!("Release Year: {}", self.release_year);
        println!("Duration: {}", self.duration_secs) ;

    }
}

fn main(){
    let song: TaylorSwiftSong = TaylorSwiftSong{
        title: String::from("Blank Space"),
        release_year: 2014,
        duration_secs: 231,
    };
    song.display_song_info(); //    Release Year: 2014
                              //    Duration: 231
                              
   // println!("song {:?}", song) ; //error[E0382]: borrow of moved value: `song`

}
```


## `self` parameter as mutable struct instance

```rust

#[derive(Debug)]
struct TaylorSwiftSong{
    title: String,
    release_year: u32,
    duration_secs: u32,
}
    
impl TaylorSwiftSong{
    fn display_song_info(self: Self){
        // self - immutable struct value (self parameter takes ownership)
            // (self: TaylorSwiftSong) == (self: Self)
        println!("Release Year: {}", self.release_year);
        println!("Duration: {}", self.duration_secs) ;

    }
    
    // a mutable instance
    fn double_length(mut self: Self){
        self.duration_secs = self.duration_secs *2 ;
        println!("{:?}", self) ;
    }
    
}

fn main(){
    let song: TaylorSwiftSong = TaylorSwiftSong{
        title: String::from("Blank Space"),
        release_year: 2014,
        duration_secs: 231,
        
    };
        
    song.double_length(); //TaylorSwiftSong { title: "Blank Space", release_year: 2014, duration_secs: 462 }
}
```

## `self` parameter as immutable and mutable reference

```rust

#[derive(Debug)]
struct TaylorSwiftSong{
    title: String,
    release_year: u32,
    duration_secs: u32,
}
    
impl TaylorSwiftSong{
    fn display_song_info(&self){
        // self: &Self - immutable reference (self no ownership moved)
        // or &self
        println!("Release Year: {}", self.release_year);
        println!("Duration: {}", self.duration_secs) ;

    }
    
    // a mutable reference
    fn double_length(self: &mut Self){
    // or (&mut self)
        self.duration_secs = self.duration_secs *2 ; // rust Rust automatically will derefence
        // so self.duration_secs *2 will be (*self).duration_secs *2
        println!("{:?}", self) ;
    }
    
}

fn main(){
    let mut song: TaylorSwiftSong = TaylorSwiftSong{
        title: String::from("Blank Space"),
        release_year: 2014,
        duration_secs: 231,
        
    };

    song.display_song_info(); //    Release Year: 2014
                              //    Duration: 231
    song.double_length(); //TaylorSwiftSong { title: "Blank Space", release_year: 2014, duration_secs: 462 }
    println!("song {:?}", song) ; // song TaylorSwiftSong { title: "Blank Space", release_year: 2014, duration_secs: 462 }

}
```



---
# Methods with Multiple Parameters

```rust

#[derive(Debug)]
struct TaylorSwiftSong{
    title: String,
    release_year: u32,
    duration_secs: u32,
}
    
impl TaylorSwiftSong{
    fn display_song_info(&self){
        // self: &Self - immutable reference (self no ownership moved)
        // or &self
        println!("Release Year: {}", self.release_year);
        println!("Duration: {}", self.duration_secs) ;

    }
    
    // a mutable reference
    fn double_length(self: &mut Self){
    // or (&mut self)
        self.duration_secs = self.duration_secs *2 ; // rust Rust automatically will derefence
        // so self.duration_secs *2 will be (*self).duration_secs *2
        println!("{:?}", self) ;
    }
    
    
    fn is_longer_than(&self, other: &Self ) -> bool {
        self.duration_secs > other.duration_secs
    }
    
}

fn main(){
    let mut song: TaylorSwiftSong = TaylorSwiftSong{
        title: String::from("Blank Space"),
        release_year: 2014,
        duration_secs: 231,
        
    };
    
    let all_too_well: TaylorSwiftSong = TaylorSwiftSong{
        title: String::from("All Too Well"),
        release_year: 2012,
        duration_secs: 327,
    
    };
    
    
    if (song.is_longer_than(&all_too_well)){
        println!(
            "{} is longer than {}",
            song.title, all_too_well.title
        )
    } else {
        println!(
            "{} is longer than {}",
            all_too_well.title, song.title
        )
    }; // All Too Well is longer than Blank Space
    

    // song.display_song_info(); //    Release Year: 2014
    //                           //    Duration: 231
    // song.double_length(); //TaylorSwiftSong { title: "Blank Space", release_year: 2014, duration_secs: 462 }
    // println!("song {:?}", song) ; // song TaylorSwiftSong { title: "Blank Space", release_year: 2014, duration_secs: 462 }

}
```


----

# Associated Functions `::`

>[!info] associated functions
>- Associated functions are functions that are attached to a type.
>- `String::new()` it lives on the String type, not a specific String intance or String value
>- we often use associated functions for constructors


>[!success] constructor
>A constructor is a function that returns a new instance of a type.

```rust

impl TaylorSwiftSong{

    // associated function has no self
    fn new(title: String, release_year: u32, duration_secs: u32)-> Self{
        Self{
            title,
            release_year,
            duration_secs,
        }
    }
}

fn main(){

    let mut song: TaylorSwiftSong = TaylorSwiftSong::new(
        String::from("Blank Space"),
        2014,
        231,
        
    );
}
```

# Multiple Imp Blocks
```rust

struct Abc{
	//...
}

impl Abc{
	fn foo(){
		//....
	}
}

impl Abc {
	fn xzc(){
		//...
	}
}
```

# Builder Pattern

>[!danger] design pattern
>A design pattern is a recommended way to write or structure code to solve specific problems.

>[!note] builder pattern
>- a method that returns the instance itself (or reference to the instance)
>- it allows us to chain multiple methods in sequence in a very elegant manner

old way
```rust

impl Computer{
    fn new(cpu: String, memory: u32, hard_drive_capacity: u32)-> Self{
        Self{
            cpu,
            memory,
            hard_drive_capacity,
        }
    }
    
    
    fn upgrade_cpu(&mut self, new_cpu: String){
        self.cpu = new_cpu;
    }
    
     fn upgrade_memory(&mut self, new_memory: u32){
        self.memory = new_memory;
    }
    
     fn upgrade_hard_drive_capacity(&mut self, new_capacity: u32){
        self.hard_drive_capacity = new_capacity;
    }
}


fn main(){
    let mut computer = Computer::new(
        String::from("M3 Max"), 64, 123
    );
    
    computer.upgrade_cpu(String::from("M4 MaxPro"));
    computer.upgrade_memory(123) ;
    computer.upgrade_hard_drive_capacity(1024) ;
    
    println!("My new computer {computer:#?}") ;
    /*
    My new computer Computer {
    cpu: "M4 MaxPro",
    memory: 123,
    hard_drive_capacity: 1024,
    }

    */
}
```

You have to repeat `computer.`   !!!!

**builder pattern**
```rust

#[derive(Debug)]
struct Computer{
    cpu: String,
    memory: u32,
    hard_drive_capacity: u32,
}

impl Computer{
    fn new(cpu: String, memory: u32, hard_drive_capacity: u32)-> Self{
        Self{
            cpu,
            memory,
            hard_drive_capacity,
        }
    }
    
    
    fn upgrade_cpu(&mut self, new_cpu: String)->&mut Self{
        self.cpu = new_cpu;
        
        self
    }
    
     fn upgrade_memory(&mut self, new_memory: u32)-> &mut Self{
        self.memory = new_memory;
        
        self
    }
    
     fn upgrade_hard_drive_capacity(&mut self, new_capacity: u32)->&mut Self{
        self.hard_drive_capacity = new_capacity;
        
        self
    }
}


fn main(){
    let mut computer = Computer::new(
        String::from("M3 Max"), 64, 123
    );
    
    computer.upgrade_cpu(String::from("M4 MaxPro"))
        .upgrade_memory(123) 
        .upgrade_hard_drive_capacity(1024) ;
    
    println!("My new computer {computer:#?}") ;
    /*
    My new computer Computer {
    cpu: "M4 MaxPro",
    memory: 123,
    hard_drive_capacity: 1024,
    }

    */
}


```


---------
#rust/tuple 

# Tuple Structs

>[!info] tuple struct
>a tuple struct is a struct that assigns each piece of data an order in line rather than a name.
>a position is like a name


```rust

// hours, minutes
struct ShortDuration(u32,u32) ;

// years, months
struct LongDuration(u32, u32) ;


fn main(){
    let work_shit = ShortDuration(8, 0);
    println!("{} hours, {} minutes", work_shit.0, work_shit.1) ; //8 hours, 0 minutes

}


```


---
# Unit-Like Structs

>[!info] unit `()`
>A unit is an empty tuple, a tuple without values
>

**unit-like** struct is a struct without any fields (data), but can have methdods

```rust
struct Empty;

fn main(){
	let my_empty_struct: Empty = Empty;
}
```















































































