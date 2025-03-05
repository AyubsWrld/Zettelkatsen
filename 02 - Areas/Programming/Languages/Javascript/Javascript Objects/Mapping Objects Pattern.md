```javascript
  const values = sessions.map((dict , index ) => { 
    return {
      id: `Session ${index + 1}`,
      name: `${dict.subject}`,
      exp: `Session ${index + 1}`,
    };
  });
```

____

Tags : #javascript