# Struct Examples

```swift
// Struct
// A User defined datatype
// Person -> name, age, email
struct Person {
    var name: String
    var age: Int
    var email: String? // optional

    // function to printout a greeting message.
    func greet() {
        print("Hello, my name is \(name), and i am \(age)yrs old. My email is \(email ?? "test@test.com")")
    }
}

// implmention

var person = Person(name: "Jerry", age: 100)
//person.greet()

var person1 = Person(name: "Jerry (With Email)", age: 100, email: "jerry@test.com")
//person1.greet()

person.name = "Some new Name" // modify a value.
//person.greet()

// Mutating Methods.

// struct -> move (x,y) coordinated.

struct Point {
    var x: Int // immutable
    var y: Int // immutable
    // external and internal parameter
    mutating func moveBy(x deltaX: Int, y deltaY: Int){
        x += deltaX
        y += deltaY
    }
}

var point = Point(x: 0, y: 0)
print("x: \(point.x), y: \(point.y)")

point.moveBy(x: 5, y: 5)
print("x: \(point.x), y: \(point.y)")

point.moveBy(x: 7, y: 3)
print("x: \(point.x), y: \(point.y)")


// Computed Properties.

// rectangle -> w, h , area

struct Rectangle {
    var width: Double
    var height: Double

//    func area() -> Double {
//        return width * height
//    }

    var area: Double {
        return width * height
    }
}


let rectangle = Rectangle(width: 10, height: 12)
print("Area: \(rectangle.area)")


// Consturctors (Intializers)


// struct circle -> return radius

struct Circle {
    var radius: Double

    init(radius: Double) {
        self.radius = radius
    }

    init(diameter: Double){
        self.radius = diameter / 2
    }
}

// Implementation
let circle = Circle(radius: 5.0)
let circle1 = Circle(diameter: 7.0)

print(circle.radius)

print(circle1.radius)

// Mutating functions another example

// counter -> +1, -1

struct Counter {
    var count: Int = 0

    // increment
    mutating func increment() {
        count += 1
    }
    // decrement
    mutating func decrement() {
        count -= 1
    }
}

// Implement
var counter = Counter()
counter.increment()
counter.increment()
counter.increment()
counter.decrement()

print(counter.count)



```
