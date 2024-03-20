# Upload Data Firesbase Firestore

## Steps

[Complete this first](./UploadFileFirebase.md#button)

> We will be modifying the code here. 

```swift

// Inside the button
 print(sender.currentTitle ?? "Button Clicked")
let storage = Storage.storage()
let reference = storage.reference()
        
let mediaFolder = reference.child("media") // get the reference for the media folder in firebase storage.
        
if let buffer = imageView.image?.jpegData(compressionQuality: 0.5) {
    let uuid = UUID().uuidString
    let imageReference = mediaFolder.child("\(uuid).jpg")
    imageReference.putData(buffer, metadata: nil){
        ( metaData, error) in
            if error != nil {
                print(error?.localizedDescription ?? "Something went wrong.")
                self.makeAlert(title: "Error", message: error?.localizedDescription ?? "Firebase: Something went wrong.")
            }else{
                imageReference.downloadURL(){
                    ( url, error) in
                        if error == nil {
                            let imageUrl = url?.absoluteString
                            print(imageUrl ?? "Empty String URL Present here!")
                            // Upload the link to firebase firestore.
                            let firestoreDatabase = Firestore.firestore()
                            var firestoreReference: DocumentReference? = nil
                            
                            let post = [ "imageUrl": imageUrl!, "postedBy": Auth.auth().currentUser!.email!, "comment": self.commentText.text!, "date": FieldValue.serverTimestamp(), "likes": 0] as [String : Any]
                            
                            firestoreReference = firestoreDatabase.collection("Posts").addDocument(data: post, completion: {
                                (error) in
                                print("Firestore Reference! ")
                                if error != nil {
                                    self.makeAlert(title: "Error", message: error?.localizedDescription ?? "Unable to store image.")
                                }else{
                                    self.imageView.image = UIImage(named: "select")
                                    self.commentText.text = ""
                                    print("Post Uploaded Successfully!")
                                    self.tabBarController?.selectedIndex = 0
                                }
                            })
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