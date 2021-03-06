---
layout: post
title: "Floating Action Button With Compose"
post-excerpt: "Providing a main action for a screen is the perfect job for a Floating Action Button. Learn how to implement one with Jetpack Compose in this blog post."
social-image: "/assets/images/compose_11/social_image.png"
header: "/assets/images/compose_11/header_image.jpg"
---

This post takes a look at adding a [Floating Action Button](https://material.io/develop/android/components/floating-action-button/) to replace the add action in the `TopAppBar`. Since that is the main action on the screen it makes sense to put it into the floating action button to position it in an easier to tap location.

## Create the button

The first step is to create a new composable function for the button. This function will be included in the `Scaffold` when it is ready.

<script src="https://gist.github.com/BrianGardnerAtl/2276c5d2a7c0902221410eee171392d5.js"></script>

The next step is to create the button with the `FloatingActionButton` function. There are two versions of this in `FloatingActionButton.kt`. One version takes in some text to display and a listener. The second version takes in a listener and requires a composable function to be passed in to create the child views for the button.

The second version is used since it only requires an `Icon`.

<script src="https://gist.github.com/BrianGardnerAtl/afe0c9f68ef0e29691eba5a335a8beb6.js"></script>

Next, the `FloatingActionButton` is created with an `Icon` child. The `onClick` lambda is left empty for now just to get things working.

<script src="https://gist.github.com/BrianGardnerAtl/71b9c9856dbd39c381f0221beebcccb8.js"></script>

## Add button to the scaffold

The `Scaffold` has a parameter for the floating action button that will ensure that it is positioned correctly.

<script src="https://gist.github.com/BrianGardnerAtl/e517b7e2972b1d6aa7b81853964a7fc8.js"></script>

Running the app after adding the button to the scaffold shows it in the bottom right corner.

<div class="center-screenshot">
    <img class="post-device-screenshot" src="/assets/images/compose_11/initial_floating_action_button.png" alt="Emulator screenshot showing the floating action button displayed on screen."/>
</div>

## Reacting to clicks

Handling click events involves adding the handling code in the `onClick` parameter on the `FloatingActionButton`. In this case, a `Toast` will do well enough to prove the point.

<script src="https://gist.github.com/BrianGardnerAtl/f98262c2e05e182ecca1bbd2434ee94b.js"></script>

Running the app shows that the `Toast` is displayed when the button is clicked. The button also has a nice ripple animation by default which is nice feedback for the user.

<div class="center-screenshot">
    <video class="post-emulator-recording" controls preload="auto">
        <source src="/assets/images/compose_11/fab_click_event.webm" type="video/webm">
        Emulator screen recording of the floating action button handling the click event and showing a toast message.
    </video>
</div>

## Position the button

Another option provided by the `Scaffold` is changing the position of the button. The `floatingActionButtonPosition` parameter handles this functionality. The default value is `Scaffold.FabPosition.End` which positions the button at the bottom end of the screen. Another option is `Scaffold.FabPosition.Center` which places the button at the bottom of the screen in the center. Using this may look good depending on the design of the app.

<script src="https://gist.github.com/BrianGardnerAtl/f7cb1c45215f07109f5652e391a635cc.js"></script>

<div class="center-screenshot">
    <img class="post-device-screenshot" src="/assets/images/compose_11/centered_button.png" alt="Emulator screenshot showing the floating action button centered on the bottom of the screen."/>
</div>

There are two additional options: `Scaffold.FabPosition.EndDocked` and `Scaffold.FabPosition.CenterDocked`. These are to be used with the `BottomAppBar` component, and the `Scaffold` will actually throw an exception if it is not used.

Overall, adding the `FloatingActionButton` is fairly streamlined with the use of the `Scaffold`. My next post will look at using the `BottomAppBar` and how the docked position of the floating action button compare.

Thanks for reading and stay tuned for more!

Photo by [Wim van 't Einde](https://unsplash.com/@wimvanteinde) on [Unsplash](https://unsplash.com).