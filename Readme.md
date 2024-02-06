# IOS App Development

> Under development

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
