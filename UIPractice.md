# Swift UI Practice

1. Basic Profile Card UI

```swift
import swiftui

struct ProfileCardView: View {
    var body: some View {
        VStack(spacing: 10) {
            Image(systemName: "person.circle.fill")
                .resizable()
                .frame(width: 80, height: 80)
                .foregroundColor(.blue)

            Text("John Doe")
                .font(.title2)
                .fontWeight(.bold)

            Text("iOS Developer")
                .font(.subheadline)
                .foregroundColor(.gray)
        }
        .padding()
        .background(RoundedRectangle(cornerRadius: 10).fill(Color(.systemGray6)))
        .shadow(radius: 5)
    }
}
```

2. List with Search Functionality

```swift
import SwiftUI

struct SearchableListView: View {
    @State private var searchText = ""
    let items = ["Apple", "Banana", "Cherry", "Date", "Elderberry"]

    var filteredItems: [String] {
        if searchText.isEmpty {
            return items
        } else {
            return items.filter { $0.localizedCaseInsensitiveContains(searchText) }
        }
    }

    var body: some View {
        VStack {
            TextField("Search...", text: $searchText)
                .padding()
                .background(RoundedRectangle(cornerRadius: 10).fill(Color(.systemGray6)))
                .padding(.horizontal)

            List(filteredItems, id: \.self) { item in
                Text(item)
            }
        }
    }
}
```

3. E-Commerce Product Card with Add-to-Cart Button

```swift
import SwiftUI

struct ProductCardView: View {
    var productImage = "photo" // Replace with a real image
    var productName = "Product Name"
    var productPrice = "$19.99"

    var body: some View {
        VStack(spacing: 10) {
            Image(systemName: productImage)
                .resizable()
                .aspectRatio(contentMode: .fill)
                .frame(width: 150, height: 150)
                .clipped()
                .cornerRadius(10)

            Text(productName)
                .font(.headline)
                .lineLimit(1)

            Text(productPrice)
                .font(.subheadline)
                .foregroundColor(.gray)

            Button(action: {
                // Add to cart action
            }) {
                Text("Add to Cart")
                    .font(.subheadline)
                    .foregroundColor(.white)
                    .padding()
                    .frame(maxWidth: .infinity)
                    .background(Color.blue)
                    .cornerRadius(10)
            }
        }
        .padding()
        .background(RoundedRectangle(cornerRadius: 10).fill(Color.white))
        .shadow(radius: 5)
        .frame(width: 180)
    }
}
```

4. Shopping Cart UI with Total Price Calculation

```swift
import SwiftUI

struct CartItem: Identifiable {
    var id = UUID()
    var name: String
    var price: Double
}

struct ShoppingCartView: View {
    @State private var cartItems = [
        CartItem(name: "Apple", price: 1.99),
        CartItem(name: "Banana", price: 0.99),
        CartItem(name: "Cherry", price: 2.49)
    ]

    var totalPrice: Double {
        cartItems.reduce(0) { $0 + $1.price }
    }

    var body: some View {
        VStack {
            List(cartItems) { item in
                HStack {
                    Text(item.name)
                        .font(.headline)
                    Spacer()
                    Text("$\(item.price, specifier: "%.2f")")
                        .foregroundColor(.gray)
                }
            }

            HStack {
                Text("Total")
                    .font(.title2)
                    .fontWeight(.bold)
                Spacer()
                Text("$\(totalPrice, specifier: "%.2f")")
                    .font(.title2)
                    .fontWeight(.bold)
            }
            .padding()
        }
        .padding()
    }
}
```

5. Complex Form with Validation and Error Messages

```swift
import SwiftUI

struct RegistrationFormView: View {
    @State private var name = ""
    @State private var email = ""
    @State private var password = ""
    @State private var showErrorMessage = false

    var isNameValid: Bool {
        !name.isEmpty
    }

    var isEmailValid: Bool {
        email.contains("@") && email.contains(".")
    }

    var isPasswordValid: Bool {
        password.count >= 8
    }

    var canSubmit: Bool {
        isNameValid && isEmailValid && isPasswordValid
    }

    var body: some View {
        VStack(spacing: 20) {
            Text("Register")
                .font(.largeTitle)
                .fontWeight(.bold)

            TextField("Name", text: $name)
                .padding()
                .background(RoundedRectangle(cornerRadius: 8).stroke(isNameValid ? Color.green : Color.red, lineWidth: 1))

            TextField("Email", text: $email)
                .keyboardType(.emailAddress)
                .padding()
                .background(RoundedRectangle(cornerRadius: 8).stroke(isEmailValid ? Color.green : Color.red, lineWidth: 1))

            SecureField("Password (8+ characters)", text: $password)
                .padding()
                .background(RoundedRectangle(cornerRadius: 8).stroke(isPasswordValid ? Color.green : Color.red, lineWidth: 1))

            if !isNameValid || !isEmailValid || !isPasswordValid {
                VStack(alignment: .leading, spacing: 5) {
                    if !isNameValid {
                        Text("Name cannot be empty").foregroundColor(.red).font(.caption)
                    }
                    if !isEmailValid {
                        Text("Enter a valid email").foregroundColor(.red).font(.caption)
                    }
                    if !isPasswordValid {
                        Text("Password must be at least 8 characters").foregroundColor(.red).font(.caption)
                    }
                }
            }

            Button(action: {
                // Submit action
            }) {
                Text("Submit")
                    .foregroundColor(.white)
                    .frame(maxWidth: .infinity)
                    .padding()
                    .background(canSubmit ? Color.blue : Color.gray)
                    .cornerRadius(8)
            }
            .disabled(!canSubmit)

            Spacer()
        }
        .padding()
        .background(Color(.systemGray6).edgesIgnoringSafeArea(.all))
    }
}
```

---

## What is **SecureField**?

> SecureField in SwiftUI is a UI component specifically designed for entering secure text, such as passwords or sensitive information. It hides the entered text by displaying dots (●●●) instead of the actual characters, keeping the input hidden from view.
