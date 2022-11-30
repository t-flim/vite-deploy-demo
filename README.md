# [**Vite + React** App - Github Pages Deploy Demo](https://thefulim.my/vite-deploy-demo/)

### 1. Create app, run:
   > ```shell
   > # npm 6.x
   > $ npm create vite@latest my-app --template react
   > 
   > # npm 7+, extra double-dash is needed:
   > $ npm create vite@latest my-app -- --template react
   > 
   > # yarn
   > $ yarn create vite my-app --template react
   > ```

### 2. Enter newly created app folder
   > ```shell
   > $ cd my-app
   > 
   > $ npm install
   > $ npm run dev
   > ```

### 3. Install the `gh-pages` npm package
   > ```shell
   > $ npm install gh-pages --save-dev
   > ```

### 4. Add a `homepage` property to the `package.json` file
   > ```diff
   > {
   >     "name": "my-app",
   >     "version": "0.1.0",
   > +   "homepage": "https://{username}.github.io/{repo-name}",
   > ```

### 5. Add a `predeploy` property and a `deploy` property to the `scripts` object in the `package.json` file
   > ```diff
   > "scripts": {
   >     "dev": "vite",
   >     "build": "vite build",
   >     "preview": "vite preview",
   > +   "predeploy": "npm run build",
   > +   "deploy": "gh-pages -d dist"
   > }
   > ```

### 6. Add `base` property to `vite.config.js` file
   > ```diff
   > export default defineConfig({
   > +   base: "/{repo-name}/",
   >     plugins: [react()]
   > })    
   > ```

### 7. Add a "remote" that points to  the GitHub repository
   > ```shell
   > $ git remote add origin https://github.com/{username}/{repo-name}.git
   > ```

### 8. Push the app to the GitHub repository
   > ```shell
   > # deploy without commit message
   > $ npm run deploy
   > 
   > # deploy with commit message
   > $ npm run deploy -- -m "some-commit-message"
   > ```

### 9. Configure GitHub Pages
1. Navigate to the **GitHub Pages** settings page
   1. In your web browser, navigate to the GitHub repository
   1. Above the code browser, click on the tab labeled "Settings"
   1. In the sidebar, in the "Code and automation" section, click on "Pages"
1. Configure the "Build and deployment" settings like this: 
   1. **Source**: Deploy from a branch
   2. **Branch**: 
      - Branch: `gh-pages`
      - Folder: `/ (root)`
1. Click on the "Save" button