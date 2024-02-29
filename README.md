# SwiftRatingComponent

This is a UI control for iOS written in Swift. It shows a star rating and takes rating input from the user. RatingStarView is a subclass of a UIView that will allow your users to post those inescapable 1-star reviews!

* Shows star rating with an optional text label.
* Can be used as a rating input control (iOS only).
* RatingStarView can be customized in the Storyboard without writing code.
* Includes different star filling modes: full, half-filled and precise.

Setup with Swift Package Manager
In Xcode 11+ select File > Packages > Add Package Dependency....
Enter this project's URL: https://github.com/Harsh-mi/SwiftRatingComponent

#### Setup with Swift Package Manager

* In Xcode 11+ select *File > Packages > Add Package Dependency...*.
* Enter this project's URL: https://github.com/Harsh-mi/SwiftRatingComponent

## Usage

1) Drag `View` object from the *Object Library* into your storyboard.

2) Set the view's class to `RatingStarView` in the *Identity Inspector*.

3) Customize the **RatingStarView** appearance in the *Attributes Inspector*. If storyboard does not show the stars click **Refresh All Views** from the **Editor** menu.

## Positioning the RatingStar view

One can position the RatingStar view using Auto Layout constaints. The width and height of the view is determined automatically based on the size of its content - stars and text. Therefore, there is no need to set width/height constaints on the RatingStarView.

## Using RatingStarView in code

Add `import SwiftRatingComponent` to your source code, unless you used the file setup method.

You can style and control RatingStarView from your code by creating an outlet in your view controller. Alternatively, one can instantiate `RatingStarView` class and add it to the view manually without using Storyboard.

```Swift
// Change the RatingStarVieww rating
ratingStarView.rating = 4

// Change the text
ratingStarView.text = "(123)"

// Called when user finishes changing the rating by lifting the finger from the view.
// This may be a good place to save the rating in the database or send to the server.
ratingStarView.didFinishTouchingRating = { rating in }

// A closure that is called when user changes the rating by touching the view.
// This can be used to update UI as the rating is being changed by moving a finger.
ratingStarView.didTouchRating = { rating in }
```

## Customization

One can customize RatingStarView from code by changing its `settings`.

```Swift
// Do not change rating when touched
// Use if you need just to show the stars without getting user's input
ratingStarView.settings.updateOnTouch = false

// Show only fully filled stars
ratingStarView.settings.fillMode = .full
// Other fill modes: .half, .precise

// Change the size of the stars
ratingStarView.settings.starSize = 30

// Set the distance between stars
ratingStarView.settings.starMargin = 5

// Set the color of a filled star
ratingStarView.settings.filledColor = UIColor.orange

// Set the border color of an empty star
ratingStarView.settings.emptyBorderColor = UIColor.orange

// Set the border color of a filled star
ratingStarView.settings.filledBorderColor = UIColor.orange
```

## Supplying images for the stars

By default, RatingStarView draws the stars from an array of points. Alternatively, one can supply custom images for the stars, both in the Storyboard and from code.

#### Using star images from code

```Swift
// Set image for the filled star
ratingStarView.settings.filledImage = UIImage(named: "filledImage")

// Set image for the empty star
ratingStarView.settings.emptyImage = UIImage(named: "emptyImage")
```
Note: you need to have the images for the filled and empty star in your project for this code to work.
