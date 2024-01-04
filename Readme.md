# IOS App Development
**IOS App Development** Course. You will be making real-world applications and solving complex problems.

## Swift Basics


**Naming Conventions**

> We use camel casing. ex. imageName, buttonName.

___

### Creating a Variable

```swift
var myVariable = 42
let myConstant = 11
var typedVariable: Type
let typedConstant: Type
```

---

**Difference b/w var and let**

|**var**|**let**|
|-------|-------|
|Variables declared using var are mutable.|Constants declared using let are immutable.|
|You use var when you need a value that might change during the course of your program.|You use let when you have a value that should not (or cannot) be changed throughout the execution of your program.|

**Choosing Between var and let**

**Use var when:**
> You expect the value to change or be modified during the execution of your program.
You are working with variables that represent mutable state.

**Use let when:**
>You want to ensure that the value remains constant and does not change.
You are working with constants that represent unchanging values.


### Arrays

---

An Array is used to store data in a list.

**Ex.**
```swift
var array = [1,2,3,4,5]
// Note: give symmetrical spaces
// " = " -> symmetrical space 
```


### Dictionary

---

A dictionary is a collection type that allows you to store key-value pairs. Each key must be unique within the dictionary, and it maps to a specific value. Here's an example of using dictionaries in Swift

**Ex.**

```swift
var ages = ["Alice": 28, "Bob": 32, "Charlie": 25, "David": 30]

// Accessing values using keys
let aliceAge = ages["Alice"]  // 28

// Modifying values
ages["Bob"] = 33

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

## Looping

---


In Swift, there are several ways to perform looping, including for-in loops, while loops, and repeat-while loops. Here are examples of each

### for-in Loop

--- 

**Ex.**

```swift
// Example 1: Loop over a range
for i in 1...5 {
    print(i)
}

// Example 2: Loop over an array
let fruits = ["Apple", "Banana", "Orange"]
for fruit in fruits {
    print(fruit)
}

// Example 3: Loop with stride
for i in stride(from: 0, to: 10, by: 2) {
    print(i)
}
```

### while Loop

---

**Ex.**

```swift
// Example 1: Basic while loop
var counter = 0
while counter < 5 {
    print(counter)
    counter += 1
}

// Example 2: Loop with a condition at the end
var temperature = 20
repeat {
    print("Temperature is \(temperature) degrees Celsius")
    temperature -= 2
} while temperature > 0
```


### repeat-while Loop:

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

### Loop Control Statements

---

Swift provides loop control statements like **break** and **continue** to control the flow of loops:

**Ex.**

```swift
// Example: Using break to exit a loop
for i in 1...10 {
    if i == 5 {
        break
    }
    print(i)
}

// Example: Using continue to skip an iteration
for i in 1...5 {
    if i == 3 {
        continue
    }
    print(i)
}
```

## Control Flow Statements

---

### if statements

---

```swift
let temperature = 25

if temperature > 30 {
    print("It's a hot day!")
} else if temperature < 10 {
    print("It's a cold day!")
} else {
    print("The weather is moderate.")
}
```

### switch statements

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
## Closures

---

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

## Storyboard Terminologies

---

### IBOutlet

---

IBOutlet is a keyword used in the source code to declare a property that connects an object in the Interface Builder to the code. It is specifically used for linking user interface elements (such as buttons, labels, text fields, etc.) defined in a storyboard or XIB file to the corresponding code in Swift 

**Ex.**

``` swift
@IBOutlet weak var myLabel: UILabel!
```


### IBAction

---

IBAction is a keyword used to declare a method in the source code that can be connected to a specific user interface element's action, such as a button press or a slider value change. It allows you to define the code that should be executed when the user interacts with that UI element.

**Ex.**
```swift
@IBAction func buttonTapped(_ sender: UIButton) {
    // Code to be executed when the button is tapped
}

```
To manipulate an element, we use the syntax shown below.
> Who.What = Value  

Ex. 
> imageView.image = value.

The Example shown above is used to change the image of an imageView.

**Actual Implementation Shown below.**  

#### Playing with Image

---

``` swift
// who     what    value
imageName.image = UIImage(named:"resouceName") // Method 1


imageName.image = #imageLiteral() // Method 2 (Depricated)

// to change the alpha
imageName.alpha = 0.5

// to change the opacity
imageName.layer.opacity = 0.5 

// Using image from a list of UIImage
imageView.image = [
         UIImage(named: "DiceOne"),
         UIImage(named: "DiceTwo"),
         UIImage(named: "DiceThree"),
         UIImage(named: "DiceFour"),
         UIImage(named: "DiceFive"),
         UIImage(named: "DiceSix")]


```




Link multiple Elements to single IBAction.


Optionals (!)


label.text = "Message"


Progress View

calculate progress 
 0.0 to 1.0 (Type Float)

 percentageProgress = secondsPassed / totalTime



Using 2D Array


struct 

```swift
struct Town {
    
    // Properties
    let name : String
    var citizens : [String]
    var rescourses : [String: Int]
    
    // Init
    init(name: String, citizens: [String], rescourses: [String : Int]) {
        self.name = name
        self.citizens = citizens
        self.rescourses = rescourses
    }
    // Behaviors (Functions) or functions
    
    func fortify( ){
        print("Defences Increased!")
    }
}

// A struct is like a Blueprint (In C# or java it is called a class)

var anotherTown = Town(name: "Nameless Island", citizens: ["Tom Hanks"], rescourses: ["Coconuts": 100])


anotherTown.citizens.append("Wilson")
print(anotherTown.citizens)

var ghostTown = Town(name: "Ghost Town", citizens: [], rescourses: ["Weed":1])
print(ghostTown.rescourses)

```




MVC (Model - View - Controller)

mutating.


SceneViewDelegateController

cocoapods

sudo gem install cocoapods - will fail on apple silicon


brew install cocoapods - use this instead.

swift package manager.

we can use cocoapods or swift package manager.
but industry uses cocoapods heavily

if you add view controller, we need to change values at the source.

user persistance.image
