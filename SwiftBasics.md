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

## Guard statement

> `guard` is a control flow statement in Swift that is used to transfer program control out of a scope if a condition is not met. It's particularly useful for improving code readability and reducing the need for nested conditionals.

**Example**

```swift
guard condition else {
    // Code to execute if the condition is not met
    // Must include a transfer of control (return, break, continue, throw, or fatalError)
}
// Code to execute if the condition is met

```

**More Examples**

```swift
func processInput(_ input: Int) {
    guard input > 0 else {
        print("Input must be a positive number.")
        return
    }
    
    // Code to process the input when it's greater than 0
    print("Processing input: \(input)")
}

processInput(10)  // Will process the input
processInput(-5)  // Will print an error message and return early

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
```swift
let evenOrOdd: (Int) -> Bool = { ( num) in
    return num % 2 == 0 ? true : false
} // This is an example of closure.

func sumOfEvenNumbers(_ numbers: [Int]) -> Int {
    //Method 1
    //return numbers.filter { $0 % 2 == 0 }.reduce(0, +)
    //Method 2
    func sumOfEvenNumbers(_ numbers: [Int]) -> Int {
    var sum = 0
    
    for number in numbers {
        if evenOrOdd(number) {
            sum += number
        }
    }
    
    return sum
}
}

let numbersArray = [2, 5, 8, 11, 4, 7, 10]
let result = sumOfEvenNumbers(numbersArray)
print("Sum of even numbers: \(result)")
```
2. Write a function to calculate the factorial of a given number.
```swift
func factorial(_ n: Int) -> Int {
    if n == 0 || n == 1 {
        return 1
    } else {
        return n * factorial(n - 1)
    }
}

let n = 5
let result = factorial(n)
print("Factorial of \(n): \(result)")
```
3. Write a function to check if a given string is a palindrome.
```swift
func reverseString(_ input: String) -> String {
    var reversed = ""
    
    for char in input.lowercased() {
        reversed = String(char) + reversed
    }
    
    return reversed
}
func isPalindrome(_ str: String) -> Bool {
    let reversed = reverseString(str)
    return str.lowercased() == reversed.lowercased()
}

let word = "level"
let isPalindromeResult = isPalindrome(word)
print("\(word) is a palindrome: \(isPalindromeResult)")
```
4. Write a function to check if a given number is prime.
```swift

func isPrime(_ number: Int) -> Bool {
    if number < 2 {
        return false
    }
    for i in 2..<number {
        if number % i == 0 {
            return false
        }
    }
    return true
}

let num = 13
let isPrimeResult = isPrime(num)
print("\(num) is a prime number: \(isPrimeResult)")
```


5. Write a function to reverse a given string.
```swift
func reverseString(_ input: String) -> String {
    var reversed = ""
    
    for char in input.lowercased() {
        reversed = String(char) + reversed
    }
    
    return reversed
}

let originalString = "Swift Programming"
let reversedString = reverseString(originalString)
print("Original: \(originalString)\nReversed: \(reversedString)")
```
6. Write a function that takes an array of integers and returns the maximum number.
```swift
func findMaxNumber(_ numbers: [Int]) -> Int? {
    return numbers.max()
}

let numbersArray = [12, 5, 8, 21, 15]
if let maxNumber = findMaxNumber(numbersArray) {
    print("Maximum number: \(maxNumber)")
} else {
    print("The array is empty.")
}
```
7. Write a function that counts the occurrences of each element in an array.
```swift
func countOccurrences(_ array: [String]) -> [String: Int] {
    var counts: [String: Int] = [:]

    for element in array {
        counts[element, default: 0] += 1
    }

    return counts
}

let elements = ["apple", "banana", "orange", "apple", "banana", "apple"]
let occurrences = countOccurrences(elements)
print("Element occurrences: \(occurrences)")
```

8. Two Number Sum Problem
```swift
let array = [3,5,-4,8,11,1,-1,6]

func twoNumberSum(array: [Int], targetSum: Int) -> [Int] {
    var sortedArray = array // make the copy, as array is an constant
    sortedArray.sort()
    var lp = 0;
    var rp = sortedArray.count - 1
    while lp < rp {
        var currentSum = sortedArray[lp] + sortedArray[rp]
        if currentSum == targetSum {
            return [sortedArray[lp], sortedArray[rp]]
        }else if currentSum > targetSum {
            rp -= 1
        }else if currentSum < targetSum {
            lp += 1
        }
    }
    return []
}

print(twoNumberSum(array: array, targetSum: 10))

```