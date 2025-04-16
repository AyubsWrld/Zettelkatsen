### Member Variables (Private)
---
  virtual void setBatteryDuration() = 0 ; 
  virtual void activate() = 0 ; 
  virtual void deactivate() = 0 ; 
  virtual void setPossession( Team team ) = 0 ; 
  virtual void updateObservers() = 0 ;  // Make this template with callback to assign send to observers
                                            
    public:
      virtual float getBatteryDuration() const = 0 ; 
      virtual Team getPossession() const  = 0 ; 
      virtual uint8_t getPlayersInVisionCount() const = 0 ; 
      virtual const std::shared_ptr<PlayableCharacter> getPlayerInPossession() const = 0 ; 
      virtual const std::shared_ptr<Monitor> getMonitor() const = 0 ; 
      virtual bool getIsActive() const = 0 ; 
      virtual void placeCamera( FVector location ) const = 0 ; 
      virtual CameraState getState() const = 0 ; 
  };
