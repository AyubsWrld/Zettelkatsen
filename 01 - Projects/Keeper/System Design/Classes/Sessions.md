```typescript
class Session {
  session_id     : string;
  guardian_id    : string;
  restriction_id : string;
  start_time     : string;
  end_time       : string;
  days_of_week   : string[];
  children_id    : string[];
  current_participants : Number = 0 ; 
  participants   : Number ; 
  constructor(
    session_id: string,
    guardian_id: string,
    restriction_id: string,
    start_time: string,
    end_time: string,
    days_of_week: string[],
    children_id: string[]  // Added this parameter
  ) {
    this.session_id     =    session_id;
    this.guardian_id    =    guardian_id;
    this.restriction_id =    restriction_id;
    this.start_time     =    start_time;
    this.end_time       =    end_time;
    this.days_of_week   =    days_of_week;
    this.children_id    =    children_id;
    this.participants   =    children_id.length ; 
  }
}
```

___

Tags : #programming #keeper #system-design 