#rust/enum 
[[_0 spis]]

>[!info] enum
>An enum us a type that represents a set of possible values.
>Each possible value is called a variant.


```rust

#[derive(Debug)]
enum CardSuit{
    Hearts,
    Diamonds,
    Spades,
    Clubs
}

fn main(){
    let first_card: CardSuit = CardSuit::Hearts;
    let mut second_card: CardSuit = CardSuit::Diamonds;
    second_card = CardSuit::Clubs;
    println!("{:?}", second_card) ;
    
    let card_suits: [CardSuit; 3] = [
        CardSuit::Diamonds, 
        CardSuit::Spades, 
        CardSuit::Clubs
    ] ;

    
}
```


--------
# Enum with Associated Values

```rust
#[derive(Debug)]
enum PaymentMethodType{
    CreditCard(String),
    DebitCard(String),
    PayPal
}

fn main(){
    let visa: PaymentMethodType = PaymentMethodType::CreditCard(String::from("003-212")) ;
    
    let mastercard: PaymentMethodType = PaymentMethodType::CreditCard(String::from("987212")) ;
    
    println!("{:?}", mastercard) ;// CreditCard("987212")
    
    let pp: PaymentMethodType = PaymentMethodType::PayPal;
    println!("{:?}", pp) ; // PayPal
    
}
```


```rust
#[derive(Debug)]
enum PaymentMethodType{
    CreditCard(String),
    DebitCard(String),
    PayPal(String, String)
}

fn main(){
    let mut my_payment_method: PaymentMethodType = PaymentMethodType::CreditCard(String::from("003-212")) ;
    
    my_payment_method = PaymentMethodType::PayPal(String::from("003-212"), String::from("password")) ;
    
    println!("{my_payment_method:?}") ; // PayPal("003-212", "password")
}

```


>[!danger] Enum in memory
> ==Rust chooses the enum memory allocation based on what the largest variant requires==


# Struct Variants

#rust/struct_variant

>[!note] struct variant
>- A struct variant stores associated data in fields rather than by position.
>- Each piece of data has an associated name.

A pattern
```rust
#[derive(Debug)]
struct Credentials{
    username: String,
    password: String,
}


#[derive(Debug)]
enum PaymentMethodType{
    CreditCard(String),
    DebitCard(String),
    PayPal(Credentials)
}

fn main(){
    
    let user_paypal_credentials: Credentials = Credentials{
        username: String::from("tom@gmail.com"),
        password: String::from("password"),
    };
    
    let mut my_payment_method: PaymentMethodType = PaymentMethodType::PayPal(user_paypal_credentials) ;
    println!("{:#?}",my_payment_method );
    /*
    PayPal(
    Credentials {
        username: "tom@gmail.com",
        password: "password",
    },
)
*/
    
}
```

**a struct variant**
```rust
#[derive(Debug)]
enum PaymentMethodType{
    CreditCard(String),
    DebitCard(String), // like tuple
    PayPal{
        username: String,
        password: String,
        
    }, // like struct
}

fn main(){
    let mut my_payment_method: PaymentMethodType = PaymentMethodType::PayPal{ 
        username: String::from("tom@gmail.com"),
        password: String::from("password"),
        
    };
    println!("{:#?}",my_payment_method );
    /*
    PayPal {
    username: "tom@gmail.com",
    password: "password",
    }

    */
    
}


```

# Nesting Enums in Enums
```rust

#[derive(Debug)]
enum Meat{
    Chicken,
    Steak,
}


#[derive(Debug)]
enum RestaurantItem{
    Burrito(Meat),
    Bowl(Meat),
    VeganPlate,
}

fn main(){
    let lunch: RestaurantItem = RestaurantItem::Burrito(Meat::Steak);
    let dinner: RestaurantItem = RestaurantItem::Bowl(Meat::Chicken);
    let no_meat: RestaurantItem = RestaurantItem::VeganPlate;

    println!("{lunch:?}") ;   // Burrito(Steak)
    println!("{dinner:?}") ;  // Bowl(Chicken)
    println!("{no_meat:?}") ; // VeganPlate
    

}
```

```rust

#[derive(Debug)]
enum Beans{
    Pinto,
    Black,
}


#[derive(Debug)]
enum Meat{
    Chicken,
    Steak,
}


#[derive(Debug)]
enum RestaurantItem{
    Burrito{
        meat: Meat,
        beans: Beans
    },
    Bowl(Meat),
    VeganPlate,
}

fn main(){
    let lunch: RestaurantItem = RestaurantItem::Burrito{
        meat: Meat::Steak,
        beans: Beans::Pinto,
    };
    let dinner: RestaurantItem = RestaurantItem::Bowl(Meat::Chicken);
    let no_meat: RestaurantItem = RestaurantItem::VeganPlate;

    println!("{lunch:?}") ;   // Burrito { meat: Steak, beans: Pinto }
    println!("{dinner:?}") ;  // Bowl(Chicken)
    println!("{no_meat:?}") ; // VeganPlate
    

}

```










