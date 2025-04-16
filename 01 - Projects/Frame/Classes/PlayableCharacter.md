### Member Variables (Private)

---

- `bool character_is_sprinting_`  
    Indicates whether the player character is currently sprinting.
    
- `float walk_speed_`  
    Current walking speed of the player character. 
    
- `float target_walk_speed_`  
    Target walk speed that `walk_speed_` is interpolating toward.
    
- `float current_fov_`  
    Current field of view (FOV) of the character’s camera.
    
- `float target_fov_`  
    Target field of view (FOV) to interpolate toward based on player state (e.g., sprinting).
    
- `Team alignment`  
    Enum value representing which team the player character is aligned with (e.g., TeamRed, TeamBlue, Unassigned).
    
- `UCameraComponent* Camera`  
    First-person or third-person camera attached to the player character.
    
- `UCharacterMovementComponent* MovementController`  
    Reference to the movement component responsible for handling character movement.
    

---

### Functions

---

- `template <typename T> void transitionState(float state_one, float state_two, T setter, float DeltaTime)`  
    Utility function for interpolating any float value (such as speed or FOV) toward a target over time using a setter callback.
    
- `void SetWalkSpeed(float value)`  
    Set the character’s walk speed, typically used during sprint transitions.
    
- `void SetPlayerFOV(float value)`  
    Sets the field of view for the character’s camera.
    
- `void MoveForward(float input_value)`  
    Adds movement input in the forward direction relative to the character's orientation.
    
- `void MoveRight(float input_value)`  
    Adds movement input in the rightward direction relative to the character's orientation.
    
- `void TurnCamera(float input_value)`  
    Adjusts the character’s yaw (left-right rotation) based on input.
    
- `void LookUp(float input_value)`  
    Adjusts the character’s pitch (up-down rotation) based on input.
    
- `void ToggleSprinting()`  
    Toggles the sprinting state and updates target speed and FOV values accordingly.

- `void setSafety( bool value )`  
    Set whether the current player is safe from attacks or not. Takes a `boolean` value to 
    
- `bool getSafety()`  
    Returns whether the current player is safe from attacks or not.
    
___
Tags: #frame #cpp
