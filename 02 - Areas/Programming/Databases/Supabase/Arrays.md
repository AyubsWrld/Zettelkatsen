Within the table set column attribute as text and set to array . Then write to database as you would with any array .
```javascript
      try {
          const { error } = await supabase
              .from("users")
              .update({
                  role_id: selectedOption === "Tutor" ? 1 : 0,
                  topics : topicList ,    // Push array to db 
                  user_id: user_id  
              })
              .eq("user_id" , user_id); 
          
          if (error) {
              console.error("Error occurred while inserting:", error);
              return; // Handle the error as needed
          }

          // console.log("Insert successful");
          
      } catch (error) {
          console.error("Error occurred:", error);
      } finally {
          setLoading(false);
      }

```
___
Tags : #supabase #programming 