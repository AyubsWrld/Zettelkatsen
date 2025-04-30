#### Goal
___
- I want to be able to play around with the "physical" buttons on the device and play around with the state of the program to set what the current video to be loaded is as well as any data surrounding the project. ( Load before or after ? ) ;
#### Requirements
____
- User should be able to press the buttons on the device and select which menu option to use ( Dynamically swap video texture ). This is already tied to the state of the object so it shouldn't be too hard to just select everything else based on that state. 
- The buttons should visually respond to up and down clicks, They should rotate along their own axis and bounce back. 

#### Tools
____
- Three.js 
- EventDispatchers
- EventListeners
- 2D Raycasting 

#### Steps
____
- Add event listener to document for onclick events.
- Take the X , Y of the mouse click and convert it to a 3D vector extending down Z until we touch something. 
- Return the list of intersected objects and see if our button is in there. If this is the case compare the X,Y against some Threshold to determine whether the top or bottom button was pressed. 

----
Tags : #javascript #portfolio-website