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

### Auto Layout

---

Auto Layout is used to automatically format layout of our application, and handle screen orientation.

**Things we will learn**

- [Size Classes and Orientation](#size-classes-and-orientation)
- Understand Constraints
- Learn about Alignment and Pinning
- Use Containers for more fine grained control.
- Learn about StackViews

## Size Classes and Orientation

Size classes and device orientation are important concepts in iOS development, particularly when working with Auto Layout to create adaptive user interfaces that look good on various screen sizes and orientations.


### Size Classes

> Size classes are a way of categorizing different screen sizes into compact and regular variations for both width and height.