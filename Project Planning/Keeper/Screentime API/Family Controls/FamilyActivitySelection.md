A collection of applications, categories, and web domains selected by the user.
This is put into place to add a level of abstraction such that the users activities cannot be directly accessed by any other parties . 

To protect the user’s privacy, `FamilyActivitySelection` holds opaque values that represent categories, applications, and web domains selected by the user.

#### What does this imply ? 
___
This implies that the selection of applications has to be selected by the user for anything to occur . therefore , in a practical implementation of this application the process of locking applications must be done through the use of this . 
###### Important
If a user, parent, or guardian revokes authorization of your app, any tokens that [`FamilyActivitySelection`](https://developer.apple.com/documentation/familycontrols/familyactivityselection) provided while your app was authorized are voided.

