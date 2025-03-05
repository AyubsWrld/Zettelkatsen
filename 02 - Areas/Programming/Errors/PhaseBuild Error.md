https://github.com/getsentry/sentry-react-native/issues/948

change the  Bundle React Native code and images and move the with-environment.sh file into the script folder
PhaseBuild File : 
```bash
#!/bin/sh

set -e

  

# Define React Native path

REACT_NATIVE_PATH="/Users/ayubmohamed/Desktop/Programming/nativeAPI/node_modules/react-native"

WITH_ENVIRONMENT="$REACT_NATIVE_PATH/scripts/with-environment.sh"

REACT_NATIVE_XCODE="$REACT_NATIVE_PATH/scripts/react-native-xcode.sh"

  

# Setup nvm and set node

[ -z "$NVM_DIR" ] && export NVM_DIR="$HOME/.nvm"

  

if [[ -s "$HOME/.nvm/nvm.sh" ]]; then

    . "$HOME/.nvm/nvm.sh"

elif [[ -x "$(command -v brew)" && -s "$(brew --prefix nvm)/nvm.sh" ]]; then

    . "$(brew --prefix nvm)/nvm.sh"

fi

  

[ -z "$NODE_BINARY" ] && export NODE_BINARY="node"

  

# Set up node permissions

n=$(which node)

n=${n%/bin/node}

chmod -R 755 $n/bin/*

  

# Execute the React Native build script with environment

/bin/sh -c "$WITH_ENVIRONMENT $REACT_NATIVE_XCODE"
```
