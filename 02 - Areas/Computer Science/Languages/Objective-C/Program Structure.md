##### A basic `Objective-C` program consists of the following parts ( See [[Program Structure.canvas|Program Structure]])

Essentially it is made up of [[Preprocessor Commands]] , [[Interface]] , [[Implementation]] , [[OOP in Go]] , [[02 - Areas/Computer Science/Languages/Objective-C/Variables]] , [[Statements & Expressions]] , [[Comments]] 


### Example Code

```objective-c
#import <Foundation/Foundation.h>

@interface SampleClass:NSObject
- (void)sampleMethod;
@end

@implementation SampleClass

- (void)sampleMethod {
   NSLog(@"Hello, World! \n");
}

@end

int main() {
   /* my first program in Objective-C */
   SampleClass *sampleClass = [[SampleClass alloc]init];
   [sampleClass sampleMethod];
   return 0;
}
```
___

Tags : #objective-c  #language 