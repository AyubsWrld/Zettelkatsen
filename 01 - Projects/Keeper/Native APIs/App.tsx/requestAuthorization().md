> [!tldr] 
> `async-await` function which handles the Authorization of the application . Resolves to either a success , in which case the state `setIsAuthorized` is set to true  . In the case of a rejection a switch statement is used to error log based off of the potential return values . 
#### Bit-sized explanation 
___
```javascript
  const requestAuthorization = async () => {
      try {
        await ScreenTimeBridge.requestAuthorization();  // Promise 
        setIsAuthorized(true);
      } 
```

This is the function which actually interact with the [[ScreenTimeBridge]] class .  Once called a promise is created and , in the case of a successful authorization , setIsAuthorized() state is set to true . In the case authorization is not allowed , the catch block is entered with the following possible states . 


#### Catch Statement : ( Case Authorization Fails )
___
If the Authorization fails the following states may be entered . 
##### Catch block : The following cases will be expanded upon 
____

> [!tip] 
> *Pattern* : [[Switch-Error]]  pattern  which is used in tandem with an `async-await` function to print out error cases 

```javascript
      catch (error) {
        let message = 'Failed to get authorization';
        switch (error.code) {
         //Logic 
        }
```

##### Case ( l ) : Authorization Denied , `AUTH_DENIED`
____

Entered in the case when authorization is denied by the user 
```javascript
          case 'AUTH_DENIED':
            message = 'Authorization was denied. Please enable Screen Time in Settings.';
            break;
            ```

##### Case ( ll ) : Authorization Denied   , `AUTH_CANCELED`
____
Entered in the case when authorization is cancelled by the user . 
```javascript
          case 'AUTH_CANCELED':
            message = 'Authorization was canceled. Please try again.';
            break;
            ```


##### Case ( lll ) : Authorization Failed , `AUTH_FAILED_TO_RETRIEVE`
____
This occurs in the case that the authorization simply fails.

```javascript
          case 'AUTH_FAILED_TO_RETRIEVE':
            message = 'Failed to retrieve authorization status. Please check your device settings.';
            break;
            ```

##### Case ( lV ) : Authorization Unknown , `AUTH_FAILED_TO_RETRIEVE`
____
```javascript
          case 'AUTH_UNKNOWN':
            message = 'An unknown error occurred during authorization.';
            break;
```

___

Tags : #programming #native-module #javascript 