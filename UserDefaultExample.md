# UserDefault Example

## Step by Step

1. Create a Boolean flag in UserDefaults (for example: "hasLoadedNotes").
2. When the app launches, check this flag:
   - If false, call the API, upload the results to Firestore, and then set the flag to true.
   - If true, skip the API call entirely.
3. Place this logic inside the ViewModel or EnvironmentObject that initializes when the app starts.

```swift
// this is only an example, and not the exact implementation
let hasLoadedNotes = "hasLoadedNotes"

func loadDataOnce() {
    let alreadyLoaded = UserDefaults.standard.bool(forKey: hasLoadedNotes)

    if alreadyLoaded {
        // Skip API call
        return
    }

    // Perform your one-time API call here
    fetchFromAPI() // you have to write this function.

    // Mark as completed
    UserDefaults.standard.set(true, forKey: hasLoadedNotes)
}


```
