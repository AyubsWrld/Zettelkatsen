1. **Exporting a Single Value**: Use `export` to make a value (e.g., constant, function) available for import in other files.
   ```jsx
   export const MY_VALUE = 42;
   ```

2. **Named Exports**: You can export multiple values using named exports.
   ```jsx
   export const API_URL = 'https://example.com';
   export const MAX_ITEMS = 10;
   ```

3. **Default Exports**: A file can also export a default value (typically a component).
   ```jsx
   const MyComponent = () => <div>Component</div>;
   export default MyComponent;
   ```

4. **Importing**: Use `import` to bring the values into other files.
   - For named exports:  
     ```jsx
     import { MY_VALUE, API_URL } from './MyComponent';
     ```
   - For default exports:  
     ```jsx
     import MyComponent from './MyComponent';
     ```


___

Tags : #react #javascript #programming 