#### Location 
___
- Sits in direct Contact with [[01 - Projects/Keeper/Microservices/Session Manager|Session Manager]]
#### Purpose
___
- Handles operations when the application is in a locked state.
#### Responsibilities 
___
- Receive lock/unlock configs (per session or globally)
    
- Respond to queries from the device like:  
    → `isAppLocked(appId, sessionId)`
    
- Push lock instructions to the user’s device
    
- Handle **emergency app exceptions**, **unlock requests**, and **policy updates**
    
- Enforce constraints even **offline** if config is cached locally


#### Outputs 
___
- Unlock Application 
- Push updates to session participants 

| Concern                | Why It Belongs to That Service                                        |
| ---------------------- | --------------------------------------------------------------------- |
| **Orchestration**      | ✅ Session Manager (creates/ends sessions)                             |
| **Policy Enforcement** | ✅ Lock Manager (enforces restrictions)                                |
| **Stateful Decisions** | Lock Manager must respond to device queries                           |
| **Scalability**        | Lock Manager may scale independently (e.g., more users than sessions) |
| **Modularity**         | Keeps business logic focused and testable                             |

Guardian starts a session → Session Manager creates session_id → 
Session Manager tells Lock Manager what apps to lock →
Lock Manager syncs with User device and enforces the rules →
User tries to open TikTok → Device asks Lock Manager → 
Lock Manager says "Nope, blocked by active session"

___
Tags : #system-design 