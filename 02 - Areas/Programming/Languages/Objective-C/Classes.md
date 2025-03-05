### Example 
```objective-c 
#include <Foundation/Foundation.h>

@interface Animal : NSObject {
    char* name;
    int age;
}

- (void)setAge:(int)newAge;
- (void)setName:(char*)newName;
- (void)printInfo;

@end

@implementation Animal

- (void)setAge:(int)newAge {
    age = newAge;  // Directly setting the instance variable
}

- (void)setName:(char*)newName {
    name = newName;  // Directly setting the instance variable
}

- (void)printInfo {
    NSLog(@"Animal's name: %s", name);
    NSLog(@"Animal's age: %d", age);
}

@end

int main() {
    // Creating an instance of Animal
    Animal *myAnimal = [Animal new];
    
    // Setting the name to "Piggy" and age to 35
    [myAnimal setName:"Piggy"];
    [myAnimal setAge:35];
    
    // Printing the information
    [myAnimal printInfo];
    
    return 0;
}```
___

Tags : #objective-c #programming #language 