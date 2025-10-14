# Mid Term

## Sample Data

```swift
static let courses: [Course] = [
        Course(
            title: "Intro to Swift",
            instructor: "A. Patel",
            hours: 10,
            level: .beginner,
            summary: "Variables, constants, types, basic operators, and functions."
        ),
        Course(
            title: "iOS Layout Basics",
            instructor: "K. Nguyen",
            hours: 8,
            level: .beginner,
            summary: "Stacks, spacers, and text/images for simple, readable UIs."
        ),
        Course(
            title: "Control Flow Workshop",
            instructor: "S. Chen",
            hours: 6,
            level: .beginner,
            summary: "If/switch statements and loops with practical exercises."
        ),
        Course(
            title: "Swift Collections",
            instructor: "D. Brown",
            hours: 9,
            level: .intermediate,
            summary: "Arrays, dictionaries, sets, iteration patterns, and mutability."
        ),
        Course(
            title: "Optionals & Safety",
            instructor: "J. Singh",
            hours: 7,
            level: .intermediate,
            summary: "Optionals, nil-coalescing, optional binding, and guard."
        ),
        Course(
            title: "Navigation Essentials",
            instructor: "M. Garcia",
            hours: 5,
            level: .intermediate,
            summary: "NavigationView, NavigationLink, and passing data via initializers."
        ),
        Course(
            title: "Enums & Raw Values",
            instructor: "R. Lee",
            hours: 4,
            level: .intermediate,
            summary: "Modeling states with enums and displaying user-friendly raw values."
        ),
        Course(
            title: "State & Data Flow",
            instructor: "T. Wilson",
            hours: 6,
            level: .advanced,
            summary: "Using @State correctly and designing simple, predictable views."
        ),
        Course(
            title: "Performance Fundamentals",
            instructor: "I. Martinez",
            hours: 6,
            level: .advanced,
            summary: "Understanding rendering costs and writing efficient SwiftUI."
        ),
        Course(
            title: "Testing Basics",
            instructor: "P. Rossi",
            hours: 5,
            level: .advanced,
            summary: "Unit testing fundamentals and testable function design."
        )
    ]
```

## Toggle

```swift
import SwiftUI

struct CourseDetailView: View {
    let course: Course                 // passed in from NavigationLink
    @State private var isEnrolled = false  // local state for the toggle

    var body: some View {
        VStack(alignment: .leading, spacing: 16) {

            // code above

            // --- The Toggle ---
            Toggle("Enroll (local only)", isOn: $isEnrolled)

            // Simple feedback based on the toggle state
            if isEnrolled {
                Text("✅ You are enrolled in this course.")
                    .font(.subheadline)
            } else {
                Text("❌ You are not enrolled.")
                    .font(.subheadline)
            }

            // Code below
        }
        .padding()
        .navigationTitle("Course Details")
    }
}


```
