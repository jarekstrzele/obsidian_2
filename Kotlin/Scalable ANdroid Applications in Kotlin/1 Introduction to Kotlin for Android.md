[[_ 0 Spis]]

# Key differences between Kotlin and Java

## Null safety
In Kotlin:
- every variable has a type:
	- nullable - is denoted by `?` symbole at the end of the type - `String?` ->:
		- a developer is forced to handle
		- the developer has to use a **safe call operator** `?.` or **elvis operator** `?:` to avoid a NullPointerException at runtime.
			- **safe call operator**  is used to safely access properties or methods on nullable variables
				- if the variable is null, the expression will return null
			- **elvis operator** it provide  a default value for a nullable variable if it is null
		- `!!` **a non-null assertion operator** - it telss the compiler that a nullable variable is not null
	- non-null - `String`


## Type inferene
The compiler will automatically determine the type of a variable or expression based on the context
- `val name = "John" `// Compiler infers the type as String
- `val age = 25` // Compiler infers the type as Int
- `val numbers = listOf(1, 2, 3) `// Infers the type `List<Int>`



## Functional programming


## Immutablitity `val` read-only variable
`var` - full mutablility
- variable
- immutable collection" `listOf`, `setOf`, `mapOf`


## First-class functions and variables


## Lambdas

```kotlin
//The Kotlin alternative is somewhat more concise:
val nums = listOf(1, 2, 3, 4, 5)
val evenNums = nums.filter { it % 2 == 0 }

```

## Extension functions
They are a powerful features in Kotlin that allows developers to add new functions to existing classes without modifying their source code

Extension functions are defined outside the class they extend
For example
```kotlin
fun MyClass.functionName(){
	// ....
}


```

Other example
```rust
fun String.addExlamationMark(): String{
	return "$this!"
}


fun myFun(){
	val text = "Hello"
	val miodfiedText = text.addExclamationMark()
	println(modifiedText) // Hello!
}
```



### `let` extension function
- executes a block of code on non-null object and returns the result of the las expression within in the block
- it is most useful for executing a lambda on non-null objects

with nullable value
```kotlin
val name: String? = "Jarek"

name?.let {
    println("Długość imienia: ${it.length}")
}

```

operation and result
```kotlin
val wynik = "123".let {
    it.toInt() + 5
}
println(wynik) // 128


```


other
```kotlin
val wynik = listOf(1, 2, 3).let { lista ->
    val suma = lista.sum()
    "Suma to $suma"
}
println(wynik) // Suma to 6

```

### `run`
- the non-null object is provided in the block as the scope 
```kotlin
data class Person(
	val name: String, val surname: String, val address: String
)

val totalLength = person?.run{
	name.length + surname.length + address.lendth
} ?: 0
```


```kotlin
val s = "Kotlin"

val wynik: Int = s.run {
    println("Pracuję na: $this")
    length * 2        // wynik run to 12
}
println(wynik)

```


```kotlin
val result = run {
    val x = 10
    val y = 20
    x + y            // to zwróci run = 30
}
println(result)

```

- Nie operujemy na żadnym zewnętrznym obiekcie,
    
- Tworzymy lokalny scope dla zmiennych `x`, `y`.


### apply
- executes a block of code on an object  and returns the object itself
- often use for initializing properties of an object 
```kotlin
data class Person(var name: String = "", var age: Int = 0)

val person = Person().apply {
    name = "Ania"
    age  = 30
}
// po apply: person.name == "Ania", person.age == 30

```


## Built-in collection class extensions
`map`
`filter`
`sorted`
...

## Getters and setters
In Kotlin, you can define a property directly in the class body, and Kotlin automatically generates the default getter and setter 

```kotlin
- class Person {
- var name: String = ""
- get() {
- // Custom getter logic
- return field
- }
- set(value) {
- // Custom setter logic
- field = value
- }
- }
```












