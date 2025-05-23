---
project: PhotoSelectAndCrop
stars: 107
description: |-
    This package integrates a UIImagePickerController into a SwiftUI app. Obtain 1) a copy of the original image, 2) a scaled and / or cropped version of it, 3) a CGFloat and 4) CGPoint. The CGFloat and CGPoint represent the scale and position of the original image used to make the processed version. 
url: https://github.com/Rillieux/PhotoSelectAndCrop
---

Photo Select and Crop
=====================

<img align="right" src="Screenshots/example-detail.png" width="50%">

This Swift Package integrates a UIImagePickerController into a SwiftUI app and allows a user to select, scale and position an image to be cropped and saved as a conatct's photo, similar to the stock iOS Contacts app. To accomplish this, the project uses a `composeImageAttributes()` function to send four variables via bindings to the parent view:

1) a copy of the original `UIImage`,
2) a scaled and / or cropped `UIImage` version of it,
3) a `CGFloat`, and 
4) a `CGPoint`. 

The `CGFloat` and `CGPoint` represent the scale and position of the original image used to make the processed version. 

> :point_up: By saving the original image and scale and position markers and passing them to the `ImageMoveAndScaleSheet` view, if the user taps the "Change photo" button, the original photo is scaled and positioned to allow subsequent adjustments.
> 

## Implementation

Add an ImagePane view to your parent view like this:

`ImagePane(image: image, isEditMode: $isEditMode, renderingMode: renderingMode, colors: colors)`

<img align="right" src="Screenshots/coreDataEntity.png" width="60%">

Using CoreData, one might do the following. Define two entities: `Contact` and `ProfileImage`, where `Contact` has a `To One` relationship to `ProfileImage`. The `ProfileImage` entity should have properties that can be mapped to the variables provided to the `ImageDisplay` struct after the user has selected an image from their library.

Then, an `ImageAttributes` class should be initialized with the properties from the Core Data entity. This `ImageAttributes` class is then passed to the `ImagePane` as in the above code. For the nil case, a second `ImageAttributes` struct is initialzed, this time with a default image named `avatar` which was saved to the project's Image Assets folder. 

An `ImageAttributes` object can easily be defined as a placeholder.  

With an SF Symbol: `let placeholderAperture = ImageAttributes(withSFSymbol: "camera.aperture")`

With an image from the Assets folder: `let placeholderAvatar = ImageAttributes(withImage: "avatar")`

Examples of working apps using this Package can be found at: https://github.com/Rillieux/Contacts (using CoreData), and https://github.com/Rillieux/PhotoSelectAndCropDemo (a basic working implementation which does not cover persistence).

