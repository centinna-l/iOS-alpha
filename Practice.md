# Practice Questions

Questions below will help you with understanding the basics of swift, and improve your command over the language.

---

## Questions

1. Write a program that calculates the power of a number (x^n) without using the built-in function. Define a method called CalculatePower that takes two parameters (x and n) and returns the result. 

**Code:**

```swift
func calculatePower(base: Double, exponent: Int) -> Double {
    if exponent == 0 {
        return 1.0
    } else if exponent > 0 {
        return base * calculatePower(base: base, exponent: exponent - 1)
    } else {
        // Negative exponent
        return 1.0 / calculatePower(base: base, exponent: -exponent)
    }
}

let baseNumber = 2.0
let exponentValue = 3
let powerResult = calculatePower(base: baseNumber, exponent: exponentValue)

print("\(baseNumber) raised to the power of \(exponentValue) is \(powerResult)")

```
2. Write a program to print the **Fibonacci series** up to a specified number of terms. Define a method called FibonacciSeries that takes an integer parameter (n) and prints the Fibonacci series up to the nth term. 

**What is a Fibonacci series?**
> The Fibonacci sequence is a type series where each number is the sum of the two that precede it. It starts from 0 and 1 usually. The Fibonacci sequence is given by 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, and so on. The numbers in the Fibonacci sequence are also called Fibonacci numbers.

**Code:**

```swift
func fibonacciSeries(upto: Int) -> [Int] {
    var series = [Int]() // create an empty array.
    var counter = 2 // first two values are 0 and 1
    var a = 0
    var b = 1
    series.append(a) // adding the value of a to the list.
    series.append(b) // adding the value of b to the list.
    
    while counter < upto {
        var next = a + b
        series.append(next) // adding the next value to the list.
        a = b
        b = next
        counter += 1
    }
    return series
}

print(fibonacciSeries(upto: 5))


```

3. Write a program that checks if a given number is an **Armstrong number.** Define a method called IsArmstrongNumber that takes an **integer** parameter and **returns true** if it's an Armstrong number, otherwise false.

**What is an Armstrong Number?**
> An Armstrong number (also known as a narcissistic number, pluperfect digital invariant, or pluperfect number) is a number that is the sum of its own digits each raised to the power of the number of digits. In other words, an n-digit number is an Armstrong number if the sum of its digits, each raised to the nth power, is equal to the number itself. 

**Example** 

> 153 is an Armstrong number. 

> 1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153 

> 1634 is an Armstrong number. 

> 1^4 + 6^4 + 3^4 + 4^4 = 1 + 1296 + 81 + 256 = 1634 

**Code:**

```swift
let power: (Int, Int) -> Int = {
    (num, pow) in
    var power: Int = 1
    for i in 1...pow{
        power *= num
    }
    return power
} // Example usage of clousure.

func isArmstrongNumber(_ number: Int) -> Bool {
    guard number >= 0 else {
        print("Invalid input. Please enter a non-negative integer.")
        return false
    } // gaurd is a type of shorthand used for if-else. (It is swift specefic.`ß``)
    
    var tempNumber = number
    var numberOfDigits = 0 // we will use this to count the number of digits.
    var sum = 0
    
    var temp = tempNumber // to make a copy to count.
    while temp > 0 {
        numberOfDigits += 1
        temp /= 10 // remove the last digit. Eg. 153 -> 15 -> 1 -> 0.1 => 0
    }

    temp = tempNumber // reinitailize the temp.
    
    while temp > 0 {
        let digit = temp % 10
        sum += power(digit, numberOfDigits) // usage of clousure.
        temp /= 10
    }
    
    return sum == number
}

let exampleNumber = 153
if isArmstrongNumber(exampleNumber) {
    print("\(exampleNumber) is an Armstrong number.")
} else {
    print("\(exampleNumber) is not an Armstrong number.")
}

```


4. Implement a program that checks if a given number, is a **Perfect Number.** Define a method called IsPerfectNumber that takes an integer parameter and returns true if it's a perfect number, otherwise false. 

**What is a Perfect Number?**
> A perfect number is a positive integer that is equal to the sum of its proper divisors, excluding itself. In other words, the sum of the positive divisors of a perfect number (excluding the number itself) equals the number. 


**Examples**

**6 is a perfect number.**

> Divisors of 6: 1, 2, 3 

> 1 + 2 + 3 = 6 

**28 is a perfect number.**

> Divisors of 28: 1, 2, 4, 7, 14 

> 1 + 2 + 4 + 7 + 14 = 28


**Code:**

```swift
func isPerfectNumber(_ number: Int) -> Bool {
    // Check for invalid input
    guard number > 0 else {
        print("Please enter a positive integer.")
        return false
    }
    
    // Calculate the sum of proper divisors
    var sumOfDivisors = 0
    for divisor in 1..<number {
        if number % divisor == 0 {
            sumOfDivisors += divisor
        }
    }
    
    // Check if the sum of divisors is equal to the original number
    return sumOfDivisors == number
}

let exampleNumber = 28
if isPerfectNumber(exampleNumber) {
    print("\(exampleNumber) is a Perfect Number.")
} else {
    print("\(exampleNumber) is not a Perfect Number.")
}

```


5. Write a program to calculate the sum of prime numbers up to a given limit. Define a method called SumOfPrimes that takes an integer parameter (limit) and returns the sum of prime numbers. 

**Code:**

```swift
func isPrime(_ number: Int) -> Bool {
    guard number > 1 else {
        return false
    }

    for i in 2..<number {
        if number % i == 0 {
            return false
        }
    }

    return true
}

func sumOfPrimes(upTo limit: Int) -> Int {
    guard limit > 1 else {
        print("Please enter a limit greater than 1.")
        return 0
    }

    var sum = 0
    for num in 2...limit {
        if isPrime(num) {
            sum += num
        }
    }

    return sum
}

let limit = 10
let result = sumOfPrimes(upTo: limit)
print("Sum of prime numbers up to \(limit): \(result)")

```

## 25 Jan, 2024

Before Procedding ahead, Read About Closures, and Guard.
- [Closures](Readme.md#closures)
- [guard](SwiftBasics.md#guard-statement)

[**Online Compiler**](https://online.swiftplayground.run/)

You can download the playground file from here, and upload it on omnivox.

![PlayGround File Download.](/Images/practiceP1.png)

Complete the following questions shown below.
*Try using Closures and Guard, wherever possible in the code.*


1. Two Sum:

Given an array of integers, return indices of the two numbers such that they add up to a specific target. You may assume that each input would have exactly one solution.

> Input: nums = [2, 7, 11, 15], target = 9
> 
> Output: [0, 1]


2. Write a program that prints the numbers from 1 to 100. But for multiples of three, print "Fizz" instead of the number, and for the multiples of five, print "Buzz". For numbers that are multiples of both three and five, print "FizzBuzz".

> Input: 1 to 15
> 
> Output: 1, 2, Fizz, 4, Buzz, Fizz, 7, 8, Fizz, Buzz, 11, Fizz, 13, 14, FizzBuzz

3. Counting Elements: Given an array of integers, find and print the count of distinct elements.

> Input: [3, 1, 4, 2, 2, 1, 4]
> 
> Output: 4 (distinct elements are 3, 1, 4, 2)

4. Given a binary array, find the maximum number of consecutive 1's.

> Input: [1, 1, 0, 1, 1, 1, 0, 1, 1, 1, 1]
> 
> Output: 4 (the maximum consecutive ones are in the sequence 1, 1, 1, 1)

5. Implement a function to compute the square root of a given non-negative integer.

> Input: 16 
> 
> Output: 4 (since 4 x 4 = 16)

6. Given a sorted array, remove the duplicates in-place such that each element appears only once and return the new length.

> Input: [1, 1, 2, 2, 3, 4, 5, 5, 5]
> 
> Output: 5 (the array becomes [1, 2, 3, 4, 5])
