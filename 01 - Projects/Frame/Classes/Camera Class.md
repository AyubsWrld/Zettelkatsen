### Member Variables (Private)
---
- `CameraState* State` 
    Camera state delineating what state the camera is in. Can be either of three forms: `Placed`, `Inventory` , `NotYetPlaced`. 
- `std::shared_ptr<PlayableCharacter> camera_holder_`  
    unique pointer to a `PlayableCharacter` object representing the player who's inventory the camera is currently in. defaults to `nullptr` if the camera has not been found yet or has been placed. 
- `Team owner_`  
    Represents which team currently possesses the camera. Possible values:
    
    - `Unassigned`: No team owns the camera.
        
    - `TeamRed`: Red team has possession.
        
    - `TeamBlue`: Blue team has possession.
        
- `bool provides_safety_`  
    Indicates whether players within the cameras view are safe from the entity.
    
- `float battery_duration_`  
    The remaining battery life of the camera, in seconds.
    
- `FVector location_`  
    World location of the camera represented as an XYZ vector.
    
- `std::array<PlayableCharacter> players_in_vision_ `  
  Statically allocated array representing all players within the cameras line of sight. The size is initialized before the game starts ( Maximum number of players within the team ). 
 
- `uint8_t players_in_vision_count_` 
  Returns the count of the number of players within the cameras vision. 

---
### Member Functions
---
- `void setBatteryDuration(float duration)`  
    Sets the battery life of the camera.
- `float getBatteryDuration() const`  
    Returns the current battery life of the camera.
- `void setIsActive(bool is_active)`  
    Sets the active state of the camera (streaming on/off).
- `bool getIsActive() const`  
    Returns whether the camera is currently active.
- `Team getPossession() const`  
    Gets the current team in possession of the camera.
- `void setPossion(Team owner)`  
    Sets the current team in possession of the camera.
- `uint8_t getPlayersInVisionCount() const`  
    Gets the current number of players that are in direct vision of the camera. 
- `template void updateObservers( T x )`  
    Callback function which is applied to all the players within the array ( can be used to set/negate safety of every player ). 
- `void placeCamera( FVector location )`  
    Function to place camera in location within the map. 
___
Tags: #frame #cpp
