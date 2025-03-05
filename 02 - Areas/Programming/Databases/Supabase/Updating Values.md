```javascript
const { error } = await supabase 
	.from('users')
	.update({ value : value })
	.eq('fieldname' , value) ; 
```

#### Example Code 
____
```javascript
  async function writeValues() {
      if (!topicList || !selectedOption) {
          console.error("Error: Values are missing");
          return; // Return early if values are missing
      }
      setLoading(true);
      try {
          const { error } = await supabase
              .from("users")
              .update({
                  role_id: selectedOption === "Tutor" ? 1 : 0,
                  // ArrayOfStuff: selectedOption === "Tutor" ? 1 : 0, //  add later  user_role delineates whether teaching or learning 
                  user_id: user_id  // Ig this is how u do it ?
              })
              .eq("user_id" , user_id); 
          
          if (error) {
              console.error("Error occurred while inserting:", error);
              return; // Handle the error as needed
          }

          console.log("Insert successful");
          
      } catch (error) {
          console.error("Error occurred:", error);
      } finally {
          setLoading(false);
      }
  }

```
___
Tags : #databases #programming 