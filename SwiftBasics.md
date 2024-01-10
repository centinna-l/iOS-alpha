# Swift Basics

## Variables

```swift
// Variable declaration with type inference
var age = 25

// Explicitly specifying the type
var name: String = "John"

// Constants (let)
let pi = 3.14
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

## Practice Questions

1. Write a function that takes an array of integers and returns the sum of all even numbers.
2. Write a function to calculate the factorial of a given number.
3. Write a function to check if a given string is a palindrome.
4. Write a function to check if a given number is prime.
5. Write a function to reverse a given string.
6. Write a function that takes an array of integers and returns the maximum number.
7. Write a function that counts the occurrences of each element in an array.