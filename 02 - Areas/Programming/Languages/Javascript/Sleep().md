```javascript
function loopWithTimeout() {
    if (true) {
        console.log("Count:", count);
        count++;
        setTimeout(loopWithTimeout, 1000);
    } else {
        console.log("Loop completed");
    }
}

// Start the loop
loopWithTimeout();

```
____

Tags : #javascript