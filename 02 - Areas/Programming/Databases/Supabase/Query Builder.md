# Supabase Query Builder Notes

## Basic Structure

The Supabase query builder follows this general structure:
```javascript
const { data, error } = await supabase
  .from('table_name')
  .select('column1, column2, relation:foreign_table(foreign_column)')
  .filter('column', 'operator', 'value')
```

## Key Methods

1. **from(table_name)**
   - Specifies which table to query
   - Example: `.from('users')`

2. **select(columns)**
   - Specifies which columns to retrieve
   - Can select all columns with `*`
   - Example: `.select('id, name, email')`

3. **filter methods**
   - `eq`: Equals
   - `neq`: Not equals
   - `gt`: Greater than
   - `lt`: Less than
   - `gte`: Greater than or equal to
   - `lte`: Less than or equal to
   - `like`: Pattern matching
   - `ilike`: Case insensitive pattern matching
   - Example: `.eq('name', 'Alice')`

4. **range(from, to)**
   - Selects a range of rows
   - Example: `.range(0, 9)` (first 10 rows)

5. **order(column, { ascending: true/false })**
   - Sorts the result
   - Example: `.order('created_at', { ascending: false })`

6. **limit(count)**
   - Limits the number of rows returned
   - Example: `.limit(10)`

## Advanced Features

1. **Foreign Table Joins**
   - Use `select()` with dot notation
   - Example: `.select('*, profile:profiles(*)')`

2. **Conditional Chaining**
   ```javascript
   let query = supabase.from('users').select('*')
   if (condition) {
     query = query.eq('status', 'active')
   }
   const { data, error } = await query
   ```

3. **Full Text Search**
   - Use `textSearch(column, query)`
   - Example: `.textSearch('description', 'programmer')`

4. **Aggregations**
   - Available functions: `count`, `sum`, `avg`, `min`, `max`
   - Example: `.select('id, count').eq('status', 'active')`

5. **Modifiers**
   - `cs`: Case sensitive (default)
   - `cd`: Case insensitive
   - `sl`: Slashes are literal
   - Example: `.like('name', '%Ali%', { cs: false })`

## Error Handling

Always check for errors:
```javascript
const { data, error } = await supabase.from('users').select()
if (error) console.error('Error:', error)
else console.log('Data:', data)
```

## Best Practices

1. Use `.single()` when expecting one result
2. Use `.maybeSingle()` when result might be null
3. Always handle potential errors
4. Use prepared statements for user input to prevent SQL injection

## Performance Tips

1. Select only needed columns
2. Use indexes on frequently queried columns
3. Limit result set size when possible
4. Use count() instead of fetching all rows when only the count is needed

Remember to refer to the [official Supabase documentation](https://supabase.com/docs/reference/javascript/select) for the most up-to-date information and additional details.
____
Tags : #programming #supabase