We can alter the shape of tables after creation through the use of the the `Alter` directive. 

###  Syntax

```sql
ALTER TABLE table_name
ADD COLUMN column_name data_type [constraints];
```

---

### Example

Suppose you have this table:

```sql
CREATE TABLE users (
  user_id UUID PRIMARY KEY
);
```

Now you want to add a `username` column:

```sql
ALTER TABLE users
ADD COLUMN username TEXT NOT NULL;
```

---

### 🔧 More Examples

- Add with a default:
    
    ```sql
    ALTER TABLE users
    ADD COLUMN is_active BOOLEAN DEFAULT TRUE;
    ```
    
- Add enum or foreign key:
    
    ```sql
    ALTER TABLE sessions
    ADD COLUMN status SESSION_STATUS DEFAULT 'SESSION_STATUS_INACTIVE';
    ```
    
- Add a foreign key:
    
    ```sql
    ALTER TABLE sessions
    ADD COLUMN guardian_id UUID;
    
    ALTER TABLE sessions
    ADD CONSTRAINT fk_guardian
    FOREIGN KEY (guardian_id) REFERENCES users(user_id);
    ```
    

___
Tags: #neovim #lsp