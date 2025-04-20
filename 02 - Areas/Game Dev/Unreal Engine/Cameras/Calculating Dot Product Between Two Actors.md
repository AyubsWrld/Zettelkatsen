We want to calculate the Dot product between two actors on a per tick basis. The FOV of our camera becomes the threshold for this calculation which we will compare between the *Dot Product* between the Cameras forward vector and the vector between the actor and the camera.

#### What we need to conduct this check.
___
- **Camera's Forward vector** 
	- `FVector Forward = Camera->GetForward()`
- **Target Actors Positional Vector**
	- **Get Player Pointer** -> `UGameplayStatics::GetPlayerCharacter( GetWorld(), 0)`
	- `FVector PlayerPosition = GetPlayerPosition()`
#### Steps to calculate
___
- **Calculate the vector between the actor and the camera**.
- **Calculate** $cos(\theta)$ **between two vectors using the dot product**.
- **Calculate $cos(\dfrac{FOV}{2})$. This is a constexpr value. 
- **Compare the two angles to see if the dot product of the two vectors lies within the angle of view of the camera**
___
Tags : #programming #game-dev #unreal-engine #cpp