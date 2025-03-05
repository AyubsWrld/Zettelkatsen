
```javascript
import { createClient } from '@supabase/supabase-js';
const supabaseUrl = supabaseUrl
const supabaseAnonKey = SupabaseMasterKey (Dont use anon)
export default const supabase = createClient(supabaseUrl, supabaseAnonKey);

```

Included to import the supabase client to the all the files . Possibly store the values for the api keys within a .env folder . 

____
Tags : #programming #supabase