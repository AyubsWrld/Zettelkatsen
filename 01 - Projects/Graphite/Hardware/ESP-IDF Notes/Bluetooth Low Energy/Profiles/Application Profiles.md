In [[Bluetooth Low Energy (BLE)]] , a *profile* is a category or folder that groups related functionalities together . 

A *profile* is a way to organize your [[Bluetooth Low Energy (BLE)]] data so that other devices ( Like a smartphone ) can easily understand and interact with it . 

### Example
___
Suppose we wanted to setup two profiles , *Profile ( A )* & *Profile ( B )* . Each of these profiles has its own set of services and characteristics . 

- *Profile ( A )* could be for something like Power Data
- *Profile ( B )* could be for something like an internal Clock 

Each *Profile* can behave differently depending on the client device , For instance : 
- The Power data might only be used to send power to LED lights 
- Whereas another app may only use *Profile ( B )*  . 

____ 
Tags : #programming #computer-architecture #graphite