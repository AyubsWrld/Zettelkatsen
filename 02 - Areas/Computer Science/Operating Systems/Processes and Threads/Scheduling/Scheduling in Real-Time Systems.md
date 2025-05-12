A real-time system is one in which time plays an essential role. **Real-time** systems usually fall into one of two categories: 
- **Hard Real-Time**: Deadlines are crucial and missing them are catastrophic. ( Air traffic control ) 
- **Soft Real-Time**: Missing Deadlines are undesirable but are not the end of the world. ( Video streaming ). 
The events that a real-time system may have to respond to can be further categorized as periodic (meaning they occur at regular intervals) or aperiodic (meaning they occur unpredictably).

Real-time scheduling algorithms can be static or dynamic. The former make their scheduling decisions before the system starts running. The latter make their scheduling decisions at run time, after execution has started. Static scheduling works only when there is perfect information available in advance about the work to be done and the deadlines that have to be met. Dynamic scheduling algorithms do not have these restrictions.
___
Tags : #computer-architecture #operating-systems #processes