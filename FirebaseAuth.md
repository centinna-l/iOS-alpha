# Firebase Auth

We will see how to connect a firebase app to our IOS Application.

## Steps To connect to Firebase

1. Make a Firebase Project on the console. [Firebase](https://console.firebase.google.com/)
2. Click on the Add IOS App in the console.
3. In your IOS App in xcode, click on the general and get the **Bundle Identifier** and copy the Bundle Id **without an extra space**.
4. Paste the Bundle Id in the firebase console.
5. Download the Google Services (PLIST) file and paste it in your app, **Beneath** the Info(PLIST) file.
6. Get the SDK link from Firebase.
7. In xcode click on **file (top left corner)** New -> Add Package Dependencies -> Paste the SDK Link and click on **Add Package (Blue color button)**
8. With this Our IOS App and Firebase are connected. 

> Even though the app and console are linked, the app will not know when to establish the connection with firebase. Ideally we will need to establish the connection as soon as the app is launched.

## Establish Connection

To establish the connection, as soon as our App is launched, we will need to configure firebase in the app's *AppDelegate.swift*.

```swift
import UIKit
import Firebase // Add this line.

@main
class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        // Override point for customization after application launch.

        FirebaseApp.configure() // Add this line.
        return true
    }
    // Remaining Code.
}

```

This will establish the connection between the App and firebase Console.

## Login 

In your Login View, when the user types in their Email and Password, we need to send these information to Firebase for user Authentication. **Before** that we need to make sure authentication is enabled in Firebase with email/password authentication **toggled on**

```swift
import UIKit
import Firebase // Add this Line Here.
// Code above


// Inside the loginButtonPressed.
// emailText and passwordText are textfields.
if emailText.text != "" && passwordText.text != ""{
            Auth.auth().signIn(withEmail: emailText.text!, password: passwordText.text!){
                ( authData, error) in
                if error != nil {
                    self.makeAlert(title: "Firebase Error", message: error?.localizedDescription ?? "Something went wrong!")
                }else{
                    self.performSegue(withIdentifier: "toFeedVC", sender: nil) // Move to the Home page.
                }
            }
        }else{
            makeAlert(title: "Error", message: "Email/Password Missing!") // Custom Function to make an Alert Box.
        }

// Code Below

```

### Alert Function

```swift
    func makeAlert(title: String, message: String  ){
        let alert = UIAlertController( title: title, message: message, preferredStyle: UIAlertController.Style.alert)
        let okButton = UIAlertAction(title: "OK", style: UIAlertAction.Style.default, handler: nil)
        alert.addAction(okButton)
        self.present( alert, animated: true, completion: nil)
    }

```


## Signup

```swift

import UIKit
import Firebase // Add this Line Here.
// Code above


// Inside the loginButtonPressed.
// emailText and passwordText are textfields.
if emailText.text != "" && passwordText.text != "" {
            Auth.auth().createUser(withEmail: emailText.text!, password: passwordText.text! ){
                ( authData, error) in
                if error != nil {
                    self.makeAlert(title: "Firebase Error", message: error?.localizedDescription ?? "Something went wrong!")
                }else {
                    self.performSegue(withIdentifier: "toFeedVC", sender: nil) // Move to home view
                }
            }
        }else{
            makeAlert(title: "Error", message: "Email/Password is missing!") //  custom Alert Function.
        }
       
        performSegue(withIdentifier: "toFeedVC", sender: nil)

// Code Below

```

### Alert Function

```swift
    func makeAlert(title: String, message: String  ){
        let alert = UIAlertController( title: title, message: message, preferredStyle: UIAlertController.Style.alert)
        let okButton = UIAlertAction(title: "OK", style: UIAlertAction.Style.default, handler: nil)
        alert.addAction(okButton)
        self.present( alert, animated: true, completion: nil)
    }

```


## Logout

Code Implementation

```swift

import UIKit
import Firebase // Add this Line Here.


// code above

// Inside the logout Button
        do{
            try Auth.auth().signOut()
        }catch {
            print("error")
            self.performSegue(withIdentifier: "toViewController", sender: nil)
        }
        performSegue(withIdentifier: "toViewController", sender: nil)

// Code below

```

## User Persistance.

At this point our authentication works. but everytime we lauch our application we need to type in the email and password. To avoid that we can use persistance where the app will keep track of the token given by the firebase when we login. To achieve this functionality we need to write some code in *SceneDelegate.swift*

```swift
import UIKit
import Firebase // Add this Line here.

class SceneDelegate: UIResponder, UIWindowSceneDelegate {

    // Code Above

        func scene(_ scene: UIScene, willConnectTo session: UISceneSession, options connectionOptions: UIScene.ConnectionOptions) {
        // Use this method to optionally configure and attach the UIWindow `window` to the provided UIWindowScene `scene`.
        // If using a storyboard, the `window` property will automatically be initialized and attached to the scene.
        // This delegate does not imply the connecting scene or session are new (see `application:configurationForConnectingSceneSession` instead).

        // This is specefically for a Tab Bar.
        let currentUser = Auth.auth().currentUser
        if currentUser != nil {
            let board = UIStoryboard(name: "Main", bundle: nil)
            let tabBar = board.instantiateViewController(identifier: "tabBarController") as UITabBarController
            window?.rootViewController = tabBar // we change the starting point to the tab bar controller.
        }

        guard let _ = (scene as? UIWindowScene) else { return }
    }


    // Code Below
}


```
