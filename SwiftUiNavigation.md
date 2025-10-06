# 📘 SwiftUI Navigation Assignment

This assignment will help you practice **NavigationView**, **NavigationLink**, and **passing data between screens** in SwiftUI.
**This is graded for 2% of your project**
**_Focus more on navigation, the UI can be basic, if you want you can replicate any UI from the internet for reference._**

---

## Question 1: Book List ➜ Detail

### Goal

Create an app with two screens:

- **Screen 1:** A `NavigationView` with a `List` of book titles.
- **Screen 2:** A detail screen showing the tapped book’s **title** and **description**, passed from Screen 1.

### Model

```swift
struct Book: Identifiable {
    let id = UUID()
    let title: String
    let description: String
}
```

### Sample Data

```swift
let sampleBooks: [Book] = [
    .init(title: "Atomic Habits", description: "Small habits, big results."),
    .init(title: "Clean Code", description: "A handbook of agile software craftsmanship."),
    .init(title: "SwiftUI Essentials", description: "Learn declarative UI the Apple way."),
    .init(title: "The Pragmatic Programmer", description: "Tips for becoming a better developer."),
    .init(title: "Design Patterns", description: "Classic solutions to common design problems.")
]
```

### Instructions (Step by Step)

1. Create the Book model above.
2. Make an array of at least 5 books with title and description.
3. Display the books in a List inside a NavigationView.
4. Wrap each row in a NavigationLink that goes to BookDetailView(book: selectedBook).
5. In BookDetailView, show the book’s title and description.
6. Add .navigationTitle("Books") to the list screen.

## 📝 Question 2: Users List ➜ Profile Detail

### Goal

Create an app with two screens:

- **Screen 1:** A `NavigationView` with a `List` of users (name, age).
- **Screen 2:** A profile screen showing the selected user’s **name** and **age**, passed from Screen 1.
- **(Optional)** Add a **“Go Back”** button on the detail screen.
  - **Hint** `@Environment(\.dismiss) var dismiss` use this inside the view to make a back button, refere `official documentation`.

---

### Model

```swift
struct User: Identifiable {
    let id = UUID()
    let name: String
    let age: Int
}
```

### Sample Data

```swift
let sampleUsers: [User] = [
    .init(name: "Aisha Khan", age: 21),
    .init(name: "Liam Chen", age: 25),
    .init(name: "Sara Dupont", age: 23)
]
```

### Instructions (Step by Step)

1. Create the User model above.
2. Make an array of at least 3 users with name and age.
3. Display the users in a List inside a NavigationView.
4. Wrap each row in a NavigationLink that goes to ProfileDetailView(user: selectedUser).
5. In ProfileDetailView, show the user’s name and age.
6. Add a button that dismisses the detail screen use either:
   1. `@Environment(\.dismiss) private var dismiss`
