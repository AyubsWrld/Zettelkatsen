#### Install the Package
___
```bash
npx expo install react-native-reanimated
```

##### Add the [[Babel]] plug-in 
___
```javascript
  module.exports = {
    presets: [
      ... // don't add it here :)
    ],
    plugins: [
      ...
      'react-native-reanimated/plugin',
    ],
  };
```

`react-native-reanimated/plugin` has to be listed last.

##### Step 3: Wrap metro config with reanimated wrapper (recommended)
___
Wrap your existing Metro configuration in the `metro.config.js` file with the `wrapWithReanimatedMetroConfig` function.
```javascript
// metro.config.js
const {
  wrapWithReanimatedMetroConfig,
} = require('react-native-reanimated/metro-config');

const config = {
  // Your existing Metro configuration options
};

module.exports = wrapWithReanimatedMetroConfig(config);
```
___
Tags : #react-native #language #programming #mobile-development 