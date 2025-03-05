Here's a step-by-step outline of the process you followed to set up your Docusaurus site, configure it properly, and push it to the `gh-pages` branch on GitHub:

### Steps to Set Up Docusaurus

1. **Install Docusaurus**:
   - Used the Docusaurus CLI to create a new project:
     ```bash
     npx create-docusaurus@latest Lucidity-Documentation classic
     ```

2. **Navigate to Your Project Directory**:
   - Changed to the project directory:
     ```bash
     cd Lucidity-Documentation
     ```

3. **Configure Docusaurus**:
   - Edited `docusaurus.config.js` to set up your site configuration:
     - Updated `baseUrl` to `/Lucidity-Documentation/`.
     - Set `url` to `https://AyubsWrld.github.io`.
     - Modified `organizationName` and `projectName` to match your GitHub repo.

4. **Build the Site**:
   - Built the static site files for deployment:
     ```bash
     npm run build
     ```

5. **Deploy to GitHub Pages**:
   - Install the `gh-pages` package to handle deployment:
     ```bash
     npm install gh-pages --save-dev
     ```

6. **Update `package.json` for Deployment**:
   - Added the following deployment script in the `scripts` section of `package.json`:
     ```json
     "scripts": {
       "deploy": "gh-pages -d build"
     }
     ```

7. **Push to `gh-pages` Branch**:
   - Deployed the site by running:
     ```bash
     npm run deploy
     ```

### Git Commands to Push to `gh-pages` Branch

1. **Initialize a Git Repository** (if not already initialized):
   ```bash
   git init
   ```

2. **Add Remote Repository**:
   ```bash
   git remote add origin https://github.com/AyubsWrld/Lucidity-Documentation.git
   ```

3. **Stage Changes**:
   ```bash
   git add .
   ```

4. **Commit Changes**:
   ```bash
   git commit -m "Initial commit"
   ```

5. **Push to `gh-pages` Branch**:
   - If you are directly using the `gh-pages` package, it automatically handles this step. However, if you need to push manually, you would do:
   ```bash
   git push origin gh-pages
   ```

### Verification

1. **Check GitHub Pages Settings**:
   - Go to your GitHub repository settings and ensure that GitHub Pages is enabled for the `gh-pages` branch.

2. **Visit Your Site**:
   - Open your browser and navigate to `https://AyubsWrld.github.io/Lucidity-Documentation/` to view your deployed site.

### Summary
These steps outline the setup of your Docusaurus site, configuration adjustments for GitHub Pages, and the necessary Git commands to push your site to the `gh-pages` branch. If you have any specific details you'd like to add or modify, feel free to let me know!

----

Tags : #documentation #programming 