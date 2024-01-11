# Swift Basics

## Variables

```swift
// Variable declaration with type inference
var age = 25

// Explicitly specifying the type
var name: String = "John"

// Constants (let)
let pi = 3.14

let integerValue: Int = 42
let unsignedIntValue: UInt = 42

let doubleValue: Double = 3.14
let floatValue: Float = 2.718

let greeting: String = "Hello, Swift!"

let isTrue: Bool = true
let isFalse: Bool = false

// Collections

// Arrays
let numbers: [Int] = [1, 2, 3, 4, 5]

// Dictionaries
let person: [String: Any] = ["name": "John", "age": 25, "isStudent": true]

// Optionals
var optionalValue: Int? = 42

let firstLetter: Character = "A"

// Any or Any Object
var anyValue: Any = 42
var anyObjectValue: AnyObject = "Hello, World!"
```

## Operations

```swift
// Arithmetic operations
let sum = 5 + 3
let difference = 7 - 2
let product = 4 * 6
let quotient = 8 / 2

// Modulo operator
let remainder = 9 % 4
```

## Functions

```swift
// Function with no parameters and no return value
func greet() {
    print("Hello!")
}

// Function with parameters and a return value
func add(_ a: Int, _ b: Int) -> Int {
    return a + b
}

// Function with external and internal parameter names
func greet(person name: String) {
    print("Hello, \(name)!")
}

// Calling functions
greet()
let sum = add(3, 5)
greet(person: "Alice")
```

### External Parameter Name

**Definition:** The name used when calling the function.
**Purpose:** It enhances readability and provides context when calling the function.
**Default:** If not explicitly provided, the external name is the same as the internal name (except when using an underscore _).

### Internal Parameter Name

**Definition:** The name used for a parameter within the function body.
**Purpose:** It's used for reference and manipulation of the parameter's value within the function.
**Default:** If no external name is provided, the internal name is also used as the external name.

```swift
// Internal
func calculateSum(of numbers: [Int]) -> Int {
    return numbers.reduce(0, +)
}
// In this example, numbers is the internal parameter name. It's used within the function body to refer to the array of integers.

// External

let numbers = [1, 2, 3, 4, 5]
let sum = calculateSum(of: numbers)

// In this example, of is the external parameter name. It provides clarity when calling the function and makes the purpose of the parameter more evident.

// Using explicitly
// Using external names explicitly
func greet(person name: String, from city: String) {
    print("Hello, \(name) from \(city)!")
}

greet(person: "Alice", from: "New York")

// Default Behaviour
// no external name is provided
func printMessage(_ message: String) {
    print(message)
}

printMessage("Hello, World!")

// In this example, _ is used as the external name, meaning that when calling the function, you don't need to specify a name for the parameter:


```


## Conditional

```swift
let temperature = 25

// if statement
if temperature > 30 {
    print("It's a hot day!")
} else if temperature < 10 {
    print("It's a cold day!")
} else {
    print("The weather is moderate.")
}
```

### Switch Statements

---

```swift
let day = "Monday"

switch day {
case "Monday", "Tuesday", "Wednesday", "Thursday", "Friday":
    print("It's a weekday.")
case "Saturday", "Sunday":
    print("It's a weekend.")
default:
    print("Invalid day.")
}
```


## Looping

```swift
// for-in loop
for i in 1...5 {
    print(i)
}

// while loop
var counter = 0
while counter < 5 {
    print(counter)
    counter += 1
}

// Nested Looping
for i in 1...3 {
    for j in 1...2 {
        print("(\(i), \(j))")
    }
}

// Looping through Arrays
let fruits = ["Apple", "Banana", "Orange"]

for fruit in fruits {
    print(fruit)
}

// Enumerated Loops
let weekdays = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"]

for (index, day) in weekdays.enumerated() {
    print("\(index + 1). \(day)")
}
```


## Null Safety

```swift
// Optional type
var optionalName: String? = "John"

// Force unwrapping (use with caution)
if let unwrappedName = optionalName {
    print("Hello, \(unwrappedName)!")
} else {
    print("Name is nil.")
}

// Nil coalescing operator
let finalName = optionalName ?? "Default"
```

## Type Casting

```swift
// Type casting with 'as'
let intValue = 42
let doubleValue = Double(intValue)

// Type casting with 'as?' (conditional)
let stringValue: Any = "123"
let optionalInt = stringValue as? Int
```


## Optional Chaining (?)

**Purpose:** Used to safely unwrap optionals and to chain multiple optional values.
**Effect:** If the optional is nil, the entire chain evaluates to nil without causing a runtime crash.

```swift
let optionalString: String? = "Hello, Swift!"

// Using optional chaining to safely access the count property
let count = optionalString?.count
```

## Force Unwrapped with (!)

**Purpose:** Used to forcefully unwrap an optional when the programmer is certain that the optional contains a value.
**Effect:** If the optional is nil and you force unwrap it with !, a runtime crash will occur.

```swift
let optionalNumber: Int? = 42

// Forcefully unwrapping the optional (assuming we are sure it's not nil)
let unwrappedNumber = optionalNumber!
```

## When to use each

### Use ? when:

- You want to safely handle optionals without crashing if they are nil.
- You are chaining multiple optional values, and you want the chain to gracefully handle nil values.

### Use ! when:

- You are certain that the optional contains a value, and you want to forcefully unwrap it.
- You've performed necessary checks elsewhere in your code to ensure that the optional is not nil.

### Caution (Read this!)

> Using ! to force unwrap an optional without proper checks can lead to runtime crashes. It's generally safer to use ? and handle optionals safely, or to use conditional unwrapping with if let or guard let when you can.


```swift
if let unwrappedNumber = optionalNumber {
    // Use unwrappedNumber safely
} else {
    // Handle the case where optionalNumber is nil
}
```

## Practice Questions

**You can use any input.**

1. Write a function that takes an array of integers and returns the sum of all even numbers.
2. Write a function to calculate the factorial of a given number.
3. Write a function to check if a given string is a palindrome.
4. Write a function to check if a given number is prime.
5. Write a function to reverse a given string.
6. Write a function that takes an array of integers and returns the maximum number.
7. Write a function that counts the occurrences of each element in an array.