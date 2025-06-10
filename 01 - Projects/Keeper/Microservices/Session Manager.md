### Location
___
- Sits in between and communicates to Lock Manager and Notification Micro Service. 
#### Purpose
____
- The **Session Manager** handles the **lifecycle and coordination** of a Guardian–User session.
#### Responsibilities 
____
- Create, update, and end **sessions** (e.g., `startSession(userId, guardianId)`).
    
- Associate `tenant_id`, `session_id`, `user_id`, and `guardian_id`.
    
- Store **session metadata**:
    
    - Start time, end time
        
    - Whether a session is active
        
    - Optional session-specific rules (e.g., "study mode")
        
- Validate if a session is still active for other services (e.g., Lock Manager, Notification)

#### Outputs
___
- Session state (`active`, `expired`, `revoked`)
    
- Session config (references to restrictions, lock presets, etc.)

___
Tags : #system-design 