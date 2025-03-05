```javascript
  const addTopic = (newTopic) => {
      if(topicList.includes(newTopic)) {
        const index = topicList.indexOf(newTopic);
        const updatedTopics = [...topicList]; 
        updatedTopics.splice(index, 1);   
        setTopic(updatedTopics);         
      } else {
        setTopic([...topicList, newTopic]);    
      }
  };
```

____

Tags : #programming #javascript 
