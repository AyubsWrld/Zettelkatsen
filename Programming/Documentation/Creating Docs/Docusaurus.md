### 1. **Install Docusaurus**
First, create a new Docusaurus project by running the following commands:

```bash
npx create-docusaurus@latest my-website classic
cd my-website
npm install
```

This will generate the basic project structure with the classic theme.

### 2. **Build the Website**
To deploy the website to GitHub Pages, you'll need to build it for production.

```bash
npm run build
```

This will generate the static files in the `build` folder, ready for deployment.

### 3. **Configure GitHub Pages Deployment**

#### Step 3.1: **Update `docusaurus.config.js`**
Modify your `docusaurus.config.js` file to set the correct URLs for GitHub Pages:

```js
module.exports = {
  // ...other config
  url: 'https://<your-github-username>.github.io',
  baseUrl: '/<repository-name>/',
  organizationName: '<your-github-username>',
  projectName: '<repository-name>',
};
```

Replace:
- `<your-github-username>` with your GitHub username.
- `<repository-name>` with the name of the GitHub repository you'll be deploying to.

#### Step 3.2: **Install `gh-pages` Plugin**
You can use the `gh-pages` npm package to deploy the build to GitHub Pages.

Install it:

```bash
npm install gh-pages --save-dev
```

#### Step 3.3: **Update `package.json`**
Add the following deployment script in your `package.json` file:

```json
{
  "scripts": {
    "deploy": "GIT_USER=<your-github-username> USE_SSH=true npm run deploy",
    "predeploy": "npm run build"
  }
}
```

Make sure to replace `<your-github-username>` with your actual GitHub username.

### 4. **Deploy to GitHub Pages**
Now, you're ready to deploy! Simply run:

```bash
npm run deploy
```

This will push your `build` folder to the `gh-pages` branch of your repository, and your site will be live at `https://<your-github-username>.github.io/<repository-name>/`.

### 5. **Verify Your GitHub Pages Settings**
In your GitHub repository settings, go to the **Pages** section and make sure the source is set to the `gh-pages` branch. Your website should now be accessible.


----

Tags : #documentation #programming 