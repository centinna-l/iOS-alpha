# Upload File Firebase

We will see how to upload an image to firebase from our ios application.


## Steps 

1. Enable Firebase Storage in your firebase app console
   1. Create a new storage in **test mode**
2. Add Package Dependency in your IOS Application 
   1. Dependency - **FirebaseStorage**
3. Make sure The *GoogleServices.plist*
4. Follow the steps below.


## Storyboard

For this example we will use a simple UI 
- ImageView (Gesture enabled)
  - You can use any placeholder image
- Button (style: default)
  - Make sure the style of the button is **default**

In the upload view follow the example below.


```swift

class UploadViewController: UIViewController, UIImagePickerControllerDelegate, UINavigationControllerDelegate {  // these two should be added.
// Inside the viewdidload

    override func viewDidLoad() {
        super.viewDidLoad()
        
        imageView.isUserInteractionEnabled = true // enable user interaction
        let gestureRecogniser = UITapGestureRecognizer(target: self, action: #selector(chooseImage))
        imageView.addGestureRecognizer(gestureRecogniser) // added gesture recognizer
        // Do any additional setup after loading the view.
    }

    // #selector(chooseImage) 
     @objc func chooseImage( ){
        print("Choose Image")
        let pickerController = UIImagePickerController( )
        pickerController.delegate = self
        pickerController.sourceType = .photoLibrary // you can use camera if required
        // .camera is not available in simulator, so we use .photolibrary instead.
        present(pickerController, animated: true, completion: nil)
    }

        func imagePickerController(_ picker: UIImagePickerController, didFinishPickingMediaWithInfo info: [UIImagePickerController.InfoKey : Any]) {
        imageView.image = info[.originalImage] as? UIImage
        self.dismiss(animated: true, completion: nil)
    }
}
```


### Button

```swift
// Inside the button click

    var images: [String] = []
    @IBAction func actionButtonPressed(_ sender: UIButton) {
        print(sender.currentTitle ?? "Button Clicked")
        let storage = Storage.storage()
        let reference = storage.reference()
        
        let mediaFolder = reference.child("media") // get the reference for the media folder in firebase storage.
        
        // we need to convert the image to a buffer type.
        if let buffer = imageView.image?.jpegData(compressionQuality: 0.5) {
            let uuid = UUID().uuidString
            let imageReference = mediaFolder.child("\(uuid).jpg")
            imageReference.putData(buffer){
                ( metaData, error) in
                if error != nil {
                    print(error?.localizedDescription ?? "Something went wrong.")
                    self.makeAlert(title: "Error", message: error?.localizedDescription ?? "Firebase: Something went wrong.")
                }else{
                    imageReference.downloadURL(){
                        ( url, error) in
                        if error == nil {
                            let imageUrl = url?.absoluteString
                            images.append(imageUrl)
                            self.makeAlert(title: "Success", message: "Image Uploaded Successfully")
                        }
                    }
                }
            }
        }
    }
```

### Alert Function

```swift
func makeAlert(title: String, message: String ){
        let alert = UIAlertController(title: title, message: message, preferredStyle: UIAlertController.Style.alert)
        let okButton = UIAlertAction(title: "OK", style: UIAlertAction.Style.default, handler: nil)
        alert.addAction(okButton)
        // The present(_:animated:completion:) method is used to display the alert modally.
        self.present( alert, animated: true, completion: nil)
    }

```
