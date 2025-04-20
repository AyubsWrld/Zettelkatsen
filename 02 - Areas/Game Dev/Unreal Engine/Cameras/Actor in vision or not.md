We do this through a two step process. First we calculate the dot product between the player and the camera. And if this value is within the cameras FOV it implies that the Player is within the Cameras field of view. After this we can conduct a line trace ( Ray cast ) to check if the camera can actually see the player.


___
Tags : #programming #game-dev #unreal-engine #cpp