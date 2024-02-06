# Instagram Clone

We will be making an instagram clone with firebase.

## Things to Know

1. StoryBoards
2. UserDeafaults
3. TabViewControllers
4. SceneDelates
5. UI Elements - Button, Label, textView/TextField etc.
6. Firebase and its functionalities
7. Photo Picker
8. Strong Foundation in Swift.


### User Defaults

> UserDefaults is commonly used to store small pieces of data persistently across app launches. Here's an example of how to use UserDefaults in Swift:

```swift
let userName = "John Doe"
// we store it here, and then fetch it inside the viewDidLoad()
UserDefaults.standard.set(userName, forKey: "userName")


// Retrieving data
if let savedUserName = UserDefaults.standard.string(forKey: "userName") {
    print("Welcome back, \(savedUserName)!")
} else {
    print("No user name saved yet.")
}

// Delete UserDefaults value for a specific key
UserDefaults.standard.removeObject(forKey: "userName")
```


## Photo Picker

Here is an example of Photo Picker in swift.


```swift
// inside viewDidLoad()
override func viewDidLoad() {
        super.viewDidLoad()

        imageView.isUserInteractionEnabled = true
        let gestureRecognizer = UITapGestureRecognizer(target: self, action: #selector(chooseImage))
        imageView.addGestureRecognizer(gestureRecognizer)
        
    }

@objc func chooseImage() {
        
        let pickerController = UIImagePickerController()
        pickerController.delegate = self
        pickerController.sourceType = .photoLibrary
        present(pickerController, animated: true, completion: nil)
        
    }

    func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [UIImagePickerController.InfoKey : Any]) {
        imageView.image = info[.originalImage] as? UIImage
        self.dismiss(animated: true, completion: nil)
    }
    
    func makeAlert(titleInput: String, messageInput: String) {
        let alert = UIAlertController(title: titleInput, message: messageInput, preferredStyle: UIAlertController.Style.alert)
        let okButton = UIAlertAction(title: "OK", style: UIAlertAction.Style.default, handler: nil)
        alert.addAction(okButton)
        self.present(alert, animated: true, completion: nil)
    }
    
```