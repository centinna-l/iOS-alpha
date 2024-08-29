# Swift Basics

## Topics Covered

- [Swift Basics](#swift-basics)
  - [Topics Covered](#topics-covered)
  - [Variables](#variables)
  - [Strings](#strings)
  - [Logical Operators](#logical-operators)
  - [Operations](#operations)
  - [Conditional](#conditional)
    - [if statement](#if-statement)
    - [Switch Statements](#switch-statements)
    - [fallthrough in switch](#fallthrough-in-switch)
  - [Guard statement](#guard-statement)
  - [Looping](#looping)
  - [Arrays](#arrays)
  - [Dictionary](#dictionary)
  - [Functions](#functions)
    - [External Parameter Name](#external-parameter-name)
    - [Internal Parameter Name](#internal-parameter-name)
  - [Closures](#closures)
    - [Syntax](#syntax)
  - [Null Safety](#null-safety)
  - [Type Casting](#type-casting)
  - [Optional Chaining (?)](#optional-chaining-)
  - [Force Unwrapped with (!)](#force-unwrapped-with-)
    - [When to use each](#when-to-use-each)
      - [Use ? when:](#use--when)
      - [Use ! when:](#use--when-1)
      - [Caution (Read this!)](#caution-read-this)
  - [Struct](#struct)
    - [Difference b/w struct and classes](#difference-bw-struct-and-classes)
  - [Essential Functions](#essential-functions)
    - [Random](#random)
    - [Play Audio](#play-audio)
    - [Timer](#timer)
  - [Practice Questions](#practice-questions)
    - [Basic Swift Programming questions](#basic-swift-programming-questions)
    - [Struct Practice Questions](#struct-practice-questions)

## Variables

**Naming Conventions**

> We use camel casing. ex. imageName, buttonName.

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

**Difference b/w var and let**

| **var**                                                                                | **let**                                                                                                            |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Variables declared using var are mutable.                                              | Constants declared using let are immutable.                                                                        |
| You use var when you need a value that might change during the course of your program. | You use let when you have a value that should not (or cannot) be changed throughout the execution of your program. |

**Choosing Between var and let**

**Use var when:**

> You expect the value to change or be modified during the execution of your program.
> You are working with variables that represent mutable state.

**Use let when:**

> You want to ensure that the value remains constant and does not change.
> You are working with constants that represent unchanging values.

## Strings

```swift
let greeting = "Hello, World!"
print(greeting)


// String Interpolation
let name = "Jerry"
let age = 25
let message = "My name is \(name) and I am \(age) years old."
print(message)

// Different Methods
print(message.contains("p"))
print(message.count)
print(message.isEmpty)
print(message.split(separator: ",", omittingEmptySubsequences: false))



// Formatting with decimal
let price = 9.99
let formattedPrice = String(format: "The price is $%.2f", price)
print(formattedPrice)
```

## Logical Operators

```swift
// Logical Operators.
// 1. An example of how we check if the user can pay or not?
// Logic: For this to happen, the user should be logged In and
//        should have card details

var isLoggedIn: Bool = false

isLoggedIn = !isLoggedIn

var cardDetails = true

var canPay = isLoggedIn && cardDetails
print(canPay)

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

## Conditional

### if statement

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

### fallthrough in switch

---

```swift
let grade = 75

switch grade {
case 0..<60: // in range questions
    print("Fail")
case 60..<70:
    print("D")
case 70..<80:
    print("C")
case 80..<90:
    print("B")
case 90...100:
    print("A")
default:
    print("Invalid grade")
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

repeat-while Loop:

---

**Ex.**

```swift
// Example: Repeat-while loop
var countdown = 5
repeat {
    print("Countdown: \(countdown)")
    countdown -= 1
} while countdown > 0
```

## Arrays

---

An Array is used to store data in a list.

**Ex.**

```swift
var array = [1,2,3,4,5]
// Note: give symmetrical spaces
// " = " -> symmetrical space

var marvelHeros: [String] = ["Iron Man", "Spider-Man", "Capt. America"]

// Another way
var dcHeros: Array<String> = Array<String>()

// Different Methods available
marvelHeros.count
marvelHeros.isEmpty

marvelHeros[0]
marvelHeros[0] = "Thor"
print(marvelHeros)

marvelHeros.append("Wanda") // at the end of it.

marvelHeros.insert("DeadPool", at: 0)

marvelHeros.sort() // makes a copy and stores it
marvelHeros.reverse() // makes a copy and stores it
marvelHeros.sorted() // op done in the same array
marvelHeros.reversed() // op done in same array
```

## Dictionary

---

A dictionary is a collection type that allows you to store key-value pairs. Each key must be unique within the dictionary, and it maps to a specific value. Here's an example of using dictionaries in Swift

**Ex.**

```swift
var ages = ["Alice": 28, "Bob": 32, "Charlie": 25, "David": 30]

// Accessing values using keys
let aliceAge = ages["Alice"]  // 28

var youtubeVideos: [String: Int] = [
    "react_couse": 1122,
    "angular_course": 3344,
    "node_js_course": 5566
]

var angularVideo = youtubeVideos["angular_course"]

var keys = [String](youtubeVideos.keys)

// Modifying values
ages["Bob"] = 33

// Another way
var nodejsId = youtubeVideos.updateValue(4565, forKey: "node_js_course") // will return the old value.

// Adding a new key-value pair
ages["Eve"] = 22

// Removing a key-value pair
ages["David"] = nil

// Iterating over key-value pairs
for (name, age) in ages {
    print("\(name) is \(age) years old")
}

// Checking if a key exists
if let charlieAge = ages["Charlie"] {
    print("Charlie's age is \(charlieAge)")
} else {
    print("Charlie's age is unknown")
}
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


// return multiple elements
func avengersMovie() -> (String, String) {
    return ("Ironman", "Spiderman")
}

print(avengersMovie()) // ("Ironman", "Spiderman")

print(avengersMovie().0) // Ironman
print(avengersMovie().1) // Spiderman

// Use function as a variable type
// It is a type of closure.
func add(a: Int, b:Int) -> Int {
    return a+b
}

var addition: (Int, Int) -> Int = add


print("10 + 90 = \(addition(10,90))")

```

### External Parameter Name

**Definition:** The name used when calling the function.
**Purpose:** It enhances readability and provides context when calling the function.
**Default:** If not explicitly provided, the external name is the same as the internal name (except when using an underscore \_).

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

## Closures

Closures are self-contained blocks of functionality that can be assigned to variables, passed as parameters to functions, and returned from functions in Swift. They are similar to functions but have a more concise syntax. Closures capture and store references to variables and constants from the surrounding context in which they are defined, allowing them to access and modify these values even if they are no longer in scope.

### Syntax

```swift
let myClosure: (Parameters) -> ReturnType = { /* code */ }

// A Basic Example
let addClosure: (Int, Int) -> Int = { (a, b) in
    return a + b
}

let result = addClosure(3, 5)  // result is 8
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
// Optional
var userCity: String? // may be nil
var accountActive: Bool? // may be nil

// Forced Unwrapping

print(userCity!) // we use ! for forcefully unwrapping.


// Optional Binding

var username: String? = "Jerry"

if let unwrappedUsername = username {
    print("Hello, \(unwrappedUsername)!")
} else {
    print("Username is nil.")
}

let optionalNumber: Int? = 42

// Forcefully unwrapping the optional (assuming we are sure it's not nil)
let unwrappedNumber = optionalNumber!
```

### When to use each

#### Use ? when:

- You want to safely handle optionals without crashing if they are nil.
- You are chaining multiple optional values, and you want the chain to gracefully handle nil values.

#### Use ! when:

- You are certain that the optional contains a value, and you want to forcefully unwrap it.
- You've performed necessary checks elsewhere in your code to ensure that the optional is not nil.

> Note: It is recommened to use this as a last resort, or unless you know there will be some specified data.

#### Caution (Read this!)

> Using ! to force unwrap an optional without proper checks can lead to runtime crashes. It's generally safer to use ? and handle optionals safely, or to use conditional unwrapping with if let or guard let when you can.

```swift
// Optional Binding
if let unwrappedNumber = optionalNumber {
    // Use unwrappedNumber safely
} else {
    // Handle the case where optionalNumber is nil
}
```

## Struct

A struct (short for structure) is a user-defined data type that encapsulates related properties and behaviors. It's similar to a class but with some key differences, such as value semantics instead of reference semantics.

```swift
import foundation

// Define a struct named "Person" to represent a person
struct Person {
    var name: String
    var age: Int
    var email: String?

    // Example method to greet the person
    func greet() {
        print("Hello, my name is \(name). I am \(age) years old.")
    }
}

// Implementation
// Create an instance of the Person struct
var person1 = Person(name: "John", age: 30, email: "john@example.com")

// Accessing properties of the struct instance
print("Name: \(person1.name)")
print("Age: \(person1.age)")
if let email = person1.email {
    print("Email: \(email)")
} else {
    print("No email provided.")
}

// Calling a method of the struct instance
person1.greet()

// Update properties of the struct instance
person1.age = 35
print("Updated age: \(person1.age)")
```

> Below you will find a complicated example of struct and its implementation

```swift
import foundation

// Define a struct named "Contact" to represent a contact with multiple properties
struct Contact {
    var firstName: String
    var lastName: String
    var email: String?
    var phoneNumber: String

    // Computed property to get the full name of the contact
    var fullName: String {
        return "\(firstName) \(lastName)"
    }

    // Method to display contact details
    func displayDetails() {
        print("Name: \(fullName)")
        print("Email: \(email ?? "N/A")")
        print("Phone Number: \(phoneNumber)")
    }

    // Method to send an email to the contact
    func sendEmail(subject: String, message: String) {
        if let email = email {
            print("Sending email to \(fullName) at \(email)")
            // Code to send email
        } else {
            print("No email address available for \(fullName)")
        }
    }
}

// Create an instance of the Contact struct
var contact1 = Contact(firstName: "John", lastName: "Doe", email: "john@example.com", phoneNumber: "123-456-7890")

// Access and print properties of the contact instance
print("Full Name: \(contact1.fullName)")
contact1.displayDetails()

// Update properties of the contact instance
contact1.email = "john.doe@example.com"
contact1.phoneNumber = "987-654-3210"
contact1.displayDetails()

// Call the sendEmail method
contact1.sendEmail(subject: "Hello", message: "How are you?")

```

### Difference b/w struct and classes

we will discuss classes later ...

| **class**                                                                                                                                                                 | **struct**                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| Classes support Inheritance                                                                                                                                               | Structures do not support Inheritance                                            |
| Classes are reference types                                                                                                                                               | Structures are value types                                                       |
| Properties of a class instance can be modified even if the class instance is declared as a constant (using let).                                                          | struct instance as a constant means that the entire instance is immutable.       |
| Classes can inherit initializers from their superclass, allowing for convenient initialization of subclasses.                                                             | Structures do not inherit initializers from any other type.                      |
| Classes support both upcasting and downcasting, allowing you to treat an instance of a subclass as an instance of its superclass (upcasting) or vice versa (downcasting). | Structures do not support inheritance, so typecasting is not applicable to them. |

## Essential Functions

---

> Here are some of the most essential functions used in Swift, for iOS App Development.

### Random

---

This function is used to generate random numbers from a range

**Ex.**

```swift
//   variable      type function lower...upper
var randomNumber = Int.random(in: 0...10) // will generate a number b/w 0 to 10, with 0 and 10 inclusive

var randomNumerOne = Int.random(in: 0..< 10) // between 0 and 10, with excluding 10

// Getting float.
var randomFloatNumber = Float.random(in: 0...10) // generate a random float number between 0 and 10.

```

### Play Audio

---

A example to show how to play audio files in ios.

```swift
import AVFoundation


// Rest of the code.

 func playSound(title: String?) {
        let url = Bundle.main.url(forResource: title, withExtension: "wav")

                player = try! AVAudioPlayer(contentsOf: url!)

                player?.play()


    }

playSound(title: "alarm_sound")
```

### Timer

---

An example to create a count down timer in swift.

```swift
var timer = Times()

// rest of the code ...


timer = Timer.scheduledTimer(withTimeInterval: 0.2, repeats: false){ (Timer) in

// Do Something here....

}

```

## Practice Questions

**You can use any input.**

### Basic Swift Programming questions

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

### Struct Practice Questions

1. Create a struct called Rectangle that represents a rectangle with properties width and height. Implement a method to calculate the area of the rectangle.

```swift
struct Rectangle {
    var width: Double
    var height: Double

    func calculateArea() -> Double {
        return width * height
    }
}

// Usage
let rectangle = Rectangle(width: 5.0, height: 3.0)
let area = rectangle.calculateArea()
print("Area of the rectangle: \(area)")

```

2. Define a struct called Song to represent a song with properties title, artist, and durationInSeconds. Implement a method to convert the duration to a readable format (e.g., "3:45" for 3 minutes and 45 seconds).

```swift
struct Song {
    var title: String
    var artist: String
    var durationInSeconds: Int

    func readableDuration() -> String {
        let minutes = durationInSeconds / 60
        let seconds = durationInSeconds % 60
        return "\(minutes):\(String(format: "%02d", seconds))"
    }
}

// Usage
let song = Song(title: "Bohemian Rhapsody", artist: "Queen", durationInSeconds: 345)
let readableDuration = song.readableDuration()
print("Readble duration: \(readableDuration)")
```

3. Create a struct called Temperature to represent a temperature with properties value and unit (e.g., Celsius or Fahrenheit). Implement methods to convert the temperature from Celsius to Fahrenheit and vice versa.

```swift
struct Temperature {
    var value: Double
    var unit: String

    func convertToFahrenheit() -> Double {
        if unit.lowercased() == "celsius" {
            return (value * 9/5) + 32
        }
        return value
    }

    func convertToCelsius() -> Double {
        if unit.lowercased() == "fahrenheit" {
            return (value - 32) * 5/9
        }
        return value
    }
}

// Usage
let temperature = Temperature(value: 20, unit: "celsius")
let fahrenheitValue = temperature.convertToFahrenheit()
print("Temperature in Fahrenheit: \(fahrenheitValue)")
```

4. Define a struct called Student with properties name, age, and grade. Implement a method to check if the student is eligible for graduation based on their age and grade (e.g., age >= 18 and grade >= 10).

```swift
struct Student {
    var name: String
    var age: Int
    var grade: Int

    func isEligibleForGraduation() -> Bool {
        return age >= 18 && grade >= 10
    }
}

// Usage
let student = Student(name: "John", age: 18, grade: 10)
let isEligible = student.isEligibleForGraduation()
print("Is student eligible for graduation? \(isEligible)")

```

5. Create a struct called Car to represent a car with properties make, model, and year. Implement a method to check if the car is a vintage car (i.e., over 25 years old).

```swift

struct Car {
    var make: String
    var model: String
    var year: Int

    func isVintageCar(currentYear: Int) -> Bool {
        return currentYear - year > 25
    }
}

// Usage
let car = Car(make: "BMW", model: "X1", year: 2021)
let currentYear = 2022
let isVintage = car.isVintageCar(currentYear: currentYear)
print("Is the car a vintage car? \(isVintage)")

```

6. Define a struct called BankAccount with properties accountNumber, accountHolder, balance, and transactionHistory. Implement methods to deposit, withdraw, and transfer funds between bank accounts.
   > BankAccount Struct:
   > Properties: The BankAccount struct has four properties: accountNumber, accountHolder, balance, and transactionHistory.
   > Methods:
   > deposit(amount: Double): Adds the specified amount to the account balance and records the transaction in the transaction history.
   > withdraw(amount: Double): Subtracts the specified amount from the account balance if sufficient funds are available and records the transaction.
   > transfer(amount: Double, to account: BankAccount): Transfers the specified amount from the current account to another account if sufficient funds are available, updating both account balances and recording the transactions.

```swift
struct BankAccount {
    var accountNumber: String
    var accountHolder: String
    var balance: Double
    var transactionHistory: [String]

    mutating func deposit(amount: Double) {
        balance += amount
        transactionHistory.append("Deposit: \(amount)")
    }

    mutating func withdraw(amount: Double) {
        if amount <= balance {
            balance -= amount
            transactionHistory.append("Withdrawal: \(amount)")
        } else {
            print("Insufficient funds.")
        }
    }

    mutating func transfer(amount: Double, to account: inout BankAccount) {
        if amount <= balance {
            balance -= amount
            account.balance += amount
            transactionHistory.append("Transfer: \(amount) to \(account.accountHolder)")
            account.transactionHistory.append("Transfer: \(amount) from \(accountHolder)")
        } else {
            print("Insufficient funds.")
        }
    }
}

// Usage
var account1 = BankAccount(accountNumber: "123456", accountHolder: "John", balance: 1000, transactionHistory: [])
var account2 = BankAccount(accountNumber: "789012", accountHolder: "Alice", balance: 500, transactionHistory: [])

account1.transfer(amount: 200, to: &account2)
print("Account 1 balance: \(account1.balance)")
print("Account 2 balance: \(account2.balance)")

```

7. Create a struct called Employee to represent an employee with properties name, position, salary, and employmentHistory. Implement methods to give a raise, change the employee's position, and track employment history.
   > Employee Struct:
   > Properties: The Employee struct represents an employee with properties such as name, position, salary, and employmentHistory.
   > Methods:
   > giveRaise(amount: Double): Increases the employee's salary by the specified amount and records the raise in the employment history.
   > changePosition(newPosition: String): Updates the employee's position to the specified new position and records the change in the employment history.
8. Define a struct called Flight to represent a flight with properties flightNumber, departureAirport, arrivalAirport, departureTime, and arrivalTime. Implement methods to calculate the duration of the flight and check if the flight is delayed.
   > Flight Struct:
   > Properties: The Flight struct represents a flight with properties such as flightNumber, departureAirport, arrivalAirport, departureTime, and arrivalTime.
   > Methods:
   > calculateDuration(): Calculates the duration of the flight based on the departure and arrival times.
   > isDelayed(currentTime: Date): Checks if the flight is delayed based on the current time compared to the scheduled departure time.
9. Create a struct called Recipe to represent a recipe with properties title, ingredients, instructions, and rating. Implement methods to add, remove, and update ingredients, as well as to rate the recipe.
   > Recipe Struct:
   > Properties: The Recipe struct represents a recipe with properties such as title, ingredients, instructions, and rating.
   > Methods:
   > addIngredient(ingredient: String): Adds a new ingredient to the recipe's list of ingredients.
   > removeIngredient(ingredient: String): Removes an ingredient from the recipe's list of ingredients.
   > updateInstructions(newInstructions: String): Updates the recipe's instructions with the specified new instructions.
   > rateRecipe(rating: Int): Records the user's rating for the recipe.
10. Define a struct called Movie to represent a movie with properties title, director, actors, genre, and releaseYear. Implement methods to add and remove actors, change the genre, and calculate the age of the movie.
    > Movie Struct:
    > Properties: The Movie struct represents a movie with properties such as title, director, actors, genre, and releaseYear.
    > Methods:
    > addActor(actor: String): Adds a new actor to the movie's list of actors.
    > removeActor(actor: String): Removes an actor from the movie's list of actors.
    > changeGenre(newGenre: String): Updates the movie's genre to the specified new genre.
    > calculateAge(currentYear: Int): Calculates the age of the movie based on the release year and the current year.
