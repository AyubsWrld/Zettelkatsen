
### **General CocoaPods and Bundler Setup**

1. **Install CocoaPods Globally:**
   ```bash
   sudo gem install cocoapods
   ```

2. **Navigate to iOS Directory:**
   ```bash
   cd ios
   ```

3. **Install Pods (without Bundler):**
   ```bash
   pod install
   ```

4. **Clean Up Old Pods:**
   ```bash
   rm -rf Pods
   rm Podfile.lock
   ```

5. **Reinstall Pods:**
   ```bash
   pod install
   ```

6. **Create a Gemfile:**
   ```bash
   touch Gemfile
   ```

7. **Edit the Gemfile:**
   Add the following content to `Gemfile`:
   ```ruby
   source "https://rubygems.org"
   gem "cocoapods"
   ```

8. **Install Bundler:**
   ```bash
   sudo gem install bundler
   ```

9. **Install Bundler Dependencies:**
   ```bash
   bundle install
   ```

10. **Run `pod install` with Bundler:**
    ```bash
    bundle exec pod install
    ```

### **Cleaning and Verifying CocoaPods Setup**

1. **Clean CocoaPods Cache:**
   ```bash
   rm -rf Pods
   rm Podfile.lock
   pod install
   ```

2. **Verify CocoaPods Version:**
   ```bash
   pod --version
   ```

3. **Update CocoaPods:**
   ```bash
   sudo gem install cocoapods
   ```

### **Xcode and Ruby Configuration**

1. **Check Ruby Version:**
   ```bash
   ruby -v
   ```

2. **Install Xcode Command Line Tools:**
   ```bash
   xcode-select --install
   ```

3. **Open Xcode Workspace:**
   ```bash
   open YourProject.xcworkspace
   ```

4. **Clean Build Folder in Xcode:**
   Go to `Product` > `Clean Build Folder`

### **Other Useful Commands**

1. **Clear NPM/Yarn Cache:**
   ```bash
   npm cache clean --force
   ```
   or
   ```bash
   yarn cache clean
   ```

2. **Delete `node_modules` and Lock Files:**
   ```bash
   rm -rf node_modules
   rm package-lock.json
   npm install
   ```
   or
   ```bash
   rm -rf node_modules
   rm yarn.lock
   yarn install
   ```

3. **Clear Watchman Cache:**
   ```bash
   watchman watch-del-all
   ```

### **Additional Steps**

1. **Create a New Expo Project for Testing:**
   ```bash
   expo init new-project
   cd new-project
   expo start
   ```

2. **Update Expo CLI Globally:**
   ```bash
   npm install -g expo-cli
   ```

3. **Upgrade Expo SDK and Dependencies:**
   ```bash
   expo upgrade
   ```

These commands should cover most of the steps needed to troubleshoot and resolve issues related to CocoaPods, Bundler, and React Native projects. Keep this list handy for future reference!___

Tags : #build-issues #error #programming 