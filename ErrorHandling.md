```swift
import UIKit

enum DivisionError: Error {
    case divideByZero
}

// This error type will be used to represent a "divide by zero" error.

// Throwing the error.
func divide(_ a: Int, by b: Int) throws -> Int {
    if b == 0 {
        throw DivisionError.divideByZero
    }
    return a / b
}

//  Handling Errors Using do-catch

do {
    let result = try divide(10, by: 0)
    print("Result: \(result)")
} catch DivisionError.divideByZero {
    print("Error: Cannot divide by zero!")
} catch {
    print("An unexpected error occurred.")
}


// Using try? for Optional Error Handling
var result = try? divide(10, by: 0)
print(result)  // Output: nil

// Using try! to Force Unwrapping

result = try! divide(10, by: 2)
print("Result: \(result)")  // Output: Result: 5


//Propagating Errors
// You can also propagate the error to the caller of a function using throws:

func performDivision() throws {
    let result = try divide(10, by: 0)
    print("Result: \(result)")
}

do {
    try performDivision()
} catch {
    print("Error occurred while performing division: \(error)")
}


```
