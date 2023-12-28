### Auto Layout

---

Auto Layout is used to automatically format layout of our application, and handle screen orientation.

**Things we will learn**

- [Size Classes and Orientation](#size-classes-and-orientation)
  - [Size Classes](#size-classes)

## Size Classes and Orientation

Size classes and device orientation are important concepts in iOS development, particularly when working with Auto Layout to create adaptive user interfaces that look good on various screen sizes and orientations.


### Size Classes

> Size classes are a way of categorizing different screen sizes into compact and regular variations for both width and height.


We use UIView to create containers for our sub views. it will help us algin elements so the application knows how to responsd to screen orientation changes.

There are 3 ways to embed your elements in the container (UIView)
1. Drage and drop the UIView from the wizard
2. Select all the elements you want to embed and follow these steps
   1. Editor -> Embed In -> View
3. Select all the elements you want to embed and follow these steps
   1. Bottom right corner of the StoryBoard Screen (You will find a arrow down, inside a box)-> View