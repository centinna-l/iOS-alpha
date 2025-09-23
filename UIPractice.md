# SwiftUI Practice Assignment

**Weight:** This assignment counts for **2% of your final project grade**

---

## 📌 Instructions

- You are required to **visualize the given SwiftUI code** and **draw the UI** on **pen & paper** or **an iPad**.
- Do **not run the code in Xcode** – this is a **UI imagination and visualization exercise**.
- Pay attention to the layout structure:
  - How `VStack`, `HStack`, and `ZStack` are arranged
  - The use of `Spacer` for spacing
  - Placement of `Image`, `Text`, and `Button`
  - Shapes such as `RoundedRectangle` and their styling
- **Neatness matters**: Your sketches should clearly reflect the hierarchy of the UI components.
- Submit either:
  - **Scanned pages/photos** of your sketches, OR
  - **A digital drawing (iPad, tablet, etc.)**

---

## 📝 Tasks

### 1. Top Bar + Title + Action Row

```swift
import swiftui

struct Q1View: View {
    var body: some View {
        VStack(alignment: .leading, spacing: 16) {
            // Top bar
            HStack {
                Button(action: {}) {
                    Image(systemName: "chevron.left")
                }
                Spacer()
                Text("Dashboard")
                    .font(.title2)
                Spacer()
                Button(action: {}) {
                    Image(systemName: "bell")
                }
            }
            .padding(.horizontal)

            // Actions row
            HStack(spacing: 12) {
                Button(action: {}) {
                    HStack {
                        Image(systemName: "square.and.arrow.up")
                        Text("Share")
                    }
                }
                Spacer()
                Button(action: {}) {
                    HStack {
                        Image(systemName: "square.and.pencil")
                        Text("Edit")
                    }
                }
                Spacer()
                Button(action: {}) {
                    HStack {
                        Image(systemName: "trash")
                        Text("Delete")
                    }
                }
            }
            .padding(.horizontal)

            Spacer()
        }
    }
}

````

2. Card with Banner (ZStack) + Badge

```swift
import SwiftUI

struct Q2View: View {
    var body: some View {
        VStack {
            ZStack {
                RoundedRectangle(cornerRadius: 20)
                    .fill(Color.blue)

                VStack(spacing: 12) {
                    Text("Pro Plan")
                        .font(.title3)
                        .foregroundColor(.white)
                    Text("Monthly Overview")
                        .foregroundColor(.white)
                    HStack {
                        Image(systemName: "chart.bar.fill")
                            .foregroundColor(.white)
                        Spacer()
                        Image(systemName: "arrow.up.right.circle.fill")
                            .foregroundColor(.white)
                    }
                    .padding(.horizontal, 24)
                }
                .padding(.vertical, 24)

                // Badge
                VStack {
                    HStack {
                        Spacer()
                        ZStack {
                            RoundedRectangle(cornerRadius: 10)
                                .fill(Color.white)
                                .frame(width: 70, height: 28)
                            Text("NEW")
                                .foregroundColor(.blue)
                                .bold()
                                .font(.caption)
                        }
                    }
                    Spacer()
                }
                .padding(12)
            }
            .frame(height: 160)
            .padding()

            Spacer()
        }
    }
}
```

3. Product Row List (ForEach of rows)

```swift
import SwiftUI

struct Q3View: View {
    let items = [
        ("headphones", "Headphones"),
        ("laptopcomputer", "Laptop"),
        ("watch.case", "Watch")
    ]

    var body: some View {
        VStack(spacing: 12) {
            ForEach(items, id: \.0) { icon, title in
                HStack {
                    Image(systemName: icon)
                        .font(.title2)
                    VStack(alignment: .leading) {
                        Text(title)
                            .font(.headline)
                        Text("Tap to view details")
                            .foregroundColor(.gray)
                            .font(.caption)
                    }
                    Spacer()
                    Button(action: {}) {
                        Text("Buy")
                    }
                }
                .padding(.horizontal)
            }
            Spacer()
        }
        .padding(.top)
    }
}
```

4. 2×2 Photo Grid (Images + Captions)

```swift
import SwiftUI

struct Q4View: View {
    var body: some View {
        VStack(spacing: 16) {
            HStack(spacing: 16) {
                VStack {
                    Image("photo1")
                        .resizable()
                        .frame(width: 120, height: 80)
                    Text("Beach")
                        .font(.caption)
                }
                VStack {
                    Image("photo2")
                        .resizable()
                        .frame(width: 120, height: 80)
                    Text("City")
                        .font(.caption)
                }
            }
            HStack(spacing: 16) {
                VStack {
                    Image("photo3")
                        .resizable()
                        .frame(width: 120, height: 80)
                    Text("Forest")
                        .font(.caption)
                }
                VStack {
                    Image("photo4")
                        .resizable()
                        .frame(width: 120, height: 80)
                    Text("Mountains")
                        .font(.caption)
                }
            }
            Spacer()
        }
        .padding()
    }
}
```

5. Profile Header with Cover + Overlapping Avatar

```swift
import SwiftUI

struct Q5View: View {
    var body: some View {
        VStack(spacing: 12) {
            ZStack {
                // Cover banner
                RoundedRectangle(cornerRadius: 12)
                    .fill(Color.green)
                    .frame(height: 120)

                // Overlapping avatar
                VStack {
                    Spacer()
                    Image("avatar")
                        .resizable()
                        .frame(width: 90, height: 90)
                        .clipShape(Circle())
                }
                .padding(.bottom, -45) // pushes avatar outside the banner
            }
            .padding(.horizontal)

            // Name + buttons row
            VStack(spacing: 8) {
                Text("Jerry Joy")
                    .font(.title2)
                HStack {
                    Button(action: {}) {
                        HStack {
                            Image(systemName: "plus")
                            Text("Follow")
                        }
                    }
                    Spacer()
                    Button(action: {}) {
                        HStack {
                            Image(systemName: "message")
                            Text("Message")
                        }
                    }
                }
                .padding(.horizontal)
            }

            Spacer()
        }
    }
}

```

---

## 🎯 Grading Rubric (2%)

| Criteria         | Description                                               | Weight   |
| ---------------- | --------------------------------------------------------- | -------- |
| **Correctness**  | UI layout matches the code (proper placement of elements) | **1.0%** |
| **Neatness**     | Drawings are clear, readable, and well-structured         | **0.5%** |
| **Completeness** | All 5 tasks are attempted and concept check is answered   | **0.5%** |
