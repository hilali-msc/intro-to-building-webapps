# Applying Animation and Interface Enhancements

In order to provide a better experience for users, it is useful to leverage some of the "sugar" that we can apply to sweeten up our application. Namely, we can use animation and more responsive messaging to allow our users to more easily track how state or data has changed in our application.

## Animating for meaning
One of the side-effects of writing highly performant Javascript applications is that when we change the data on the screen it can be difficult for users to notice the alterations. It's not at all uncommon when working with an unstyled app for even developers, bleary eyed from looking closely at code, may miss that a value has changed in a corner of the screen.

In order to make it more evident that changes are happening on the page, we often turn to animation. Humans are very good at noticing even small movements, especially if everything else on a page is generally stationary. We can animate position, size, color, and shape to help us draw attention to whatever we have changed. 

We will explore how to use the features of the ngAnimate module to allow us to capture animations as they are happening on our views. This primarily leverages common techniques for applying CSS animation, but it's useful to understand the many hooks AngularJS provides to trigger the correct animation at the correct time. Making good use of the ngAnimate module will allow your app to easily draw attention in whatever way makes the most sense for the user and purpose.

## Messaging for clarity
Another weakness we have in our current interface has to do with clarity of what has happened when the user clicks the "Save City" button. This is a common problem we encounter when using websites. If we click a button to do something (like save a favorite), and then we receive no confirmation that action was successful, we are left wondering whether or not "it worked". 

Sometimes sites rely purely on animation to indicate something worked, such as making a favorite star jiggle when you click it, but although animation is good for many things in an interface, it may be insufficient to communicate to the user "that action you just attempted was successful" (or not).

For these sorts of transactions (and many others), we often use a concept of "messaging" in our apps. That is, we use a standard message format, design, and placement to convey updates from the system: "Successfully saved the city" or "Error retrieving data". Adding messaging like this will dramatically improve the usability of our application.
