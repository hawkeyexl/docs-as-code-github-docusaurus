# Docs as Code (with GitHub and Docusaurus)

This guide is an example of how to use [Docs as Code](https://www.writethedocs.org/guide/docs-as-code/) to create and publish documentation. This guide walks through using GitHub for version control, using Docusaurus and Markdown to write your docs, and using GitHub Pages to publish your docs.

## Before you start

You need the following to complete the guide:

- A GitHub account: You can sign up for a free account at [GitHub](https://github.com).
- Git: You can get Git as part of [GitHub Desktop](https://desktop.github.com/download) or from the [Git website](https://git-scm.com/downloads).
- Node.js: You can download and install Node.js from the [Node.js website](https://nodejs.org/).
- A text editor: You can use any text editor to write your documentation. Some popular options include [Visual Studio Code](https://code.visualstudio.com/).

## Set up a new repository on GitHub

Your repository stores the source files for your documentation, manages version control, and allows you to collaborate with others.

Follow these steps to set up a new repository on GitHub:

1. **Sign in to GitHub**: Go to [GitHub](https://github.com) and sign in to your account.

2. **Create a new repository**:
   1. Click the '+' icon in the top-right corner of the page.
   1. Choose **New repository** from the dropdown menu.

3. **Configure the repository**:
   1. For **Repository name**, enter a name. Note this down. We'll use `dac-test`.
   1. Keep the repository **Public** so it will work with GitHub Pages for free. Note that all changes to your content will be public.
   1. Select **Add a README file**. This is where you can add information about how to make updates to your docs.
   1. For **Add .gitignore**, choose **Node**. Docusaurus is Node-based, and this will keep GitHub from storing unnecessary files.
   1. (Optional) Choose a license if you want to add one to your project. This is what dictates how people can (or can't) use the content of your repo. We'll use an MIT license, meaning anyone can use the repo contents for any purpose.
   1. Click **Create repository**.

4. **Clone the repository**:
   1. On the repository page, click the **Code** button.
   1. Make sure **Local** and **HTTPS** are selected.
   1. Next to the URL, click the copy button to copy your repository's Git URL.
   1. On your computer, open your terminal or command prompt.
   1. Navigate to the directory where you want to clone the repository.
   1. Run the command: `git clone [URL you copied]`.
      
      The command should look something like this, but with your GitHub username and repository name:
      
      `git clone https://github.com/hawkeyexl/dac-test.git`

## Set up Docusaurus

Docusaurus is an open-source documentation tool for creating documentation websites. It uses Markdown for writing content and provides a relatively simple way to customize the look and feel of your documentation site. Docusaurus is built using React and supports features like search, versioning, and internationalization. It also has a plug-in system that lets you extend its functionality.

Follow these steps to set up Docusaurus:

1. **Install Docusaurus**:

    1. In your terminal, create a new Docusaurus project:
       
       ```bash
       npx create-docusaurus@latest website classic
       ```

    1. Follow the prompts to set up your project. If in doubt, go with the defaults.

    1. Navigate to the project directory:
      
       ```bash
       cd website
       ```
      
    1. Start the local development server:
       
       ```bash
       npm start
       ```

       This opens your browser to your Docusaurus site at [`http://localhost:3000`](http://localhost:3000).
       
    1. In the upper navigation, click **Tutorial**. You can follow the local tutorial (which is great) on when you have the time.

       For more information on how to use Docusaurus, refer to the [official documentation](https://docusaurus.io/docs).

2. **Make a small change**:

    1. Open _website/docs/index.md_ in your editor.
    1. Make a small change and save.

       The page dynamically updates in the browser. You can continue to make changes and preview them in the browser as you write your documentation.

    1. When you're done making edits, stop the development server by clicking into your terminal and pressing Ctrl+C.

3. **Add and commit your changes**:

    Committing and pushing your changes is what saves them to GitHub.

    1. In your terminal, add your new files to Git to start tracking changes in those files:

       ```bash
       git add .
       ```
    
    1. Commit the changes with a message describing what the changes include:

       ```bash
       git commit -m "Add initial documentation"
       ```

    1. Push the changes to your repository to save them to GitHub:

       ```bash
       git push
       ```

       You should now see your changes in your GitHub repository.

## Set up GitHub Pages

GitHub Pages is a feature of GitHub that allows you to host static websites directly from a GitHub repository. You can use GitHub Pages to host your documentation site for free.

Follow these steps to set up GitHub Pages:

1. **Update Docusaurus config**:
    1. In your editor, open _website/docusaurus.config.js_.
    1. In the `const config` object, make the following updates:
      
       - `url`: Update to 'https://<github_username>.github.io'. If your username is 'hawkeyexl', it would be 'https://hawkeyexl.github.io'.
       - `baseUrl`: Update to '/<repository_name>/'. If your repo is 'dac-test', this should be '/dac-test/'.
       - `organizationName`: Update to your GitHub username.
       - `projectName`: Update to your repository name.
       - `deploymentBranch`: *Add* this field and set it to 'main'.
       - `trailingSlash`: *Add* this field and set it to `false`.

       Your config should have items that look something like this:

       ```javascript
       url: 'https://hawkeyexl.github.io/',
       baseUrl: '/dac-test/',
       organizationName: 'hawkeyexl',
       projectName: 'dac-test',
       deploymentBranch: 'main',
       trailingSlash: false,
       ```

       You can see more config options and details in the [Docusaurus deployment docs](https://docusaurus.io/docs/deployment).

    1. Save the config file.
    1. Commit and push to GitHub:

       ```bash
       git add .
       git commit -m "Update config for GitHub Pages"
       git push
       ```

1. **Set up GitHub Pages**:
    1. In your browser, go to your repository on GitHub.
    1. Click on the **Settings** tab.
    1. In the left navigation, click **Pages**.
    1. Under **Branch**, choose **main** branch.
    1. In folder drop-down, choose **/docs**
    1. Click **Save**.

## Publish changes

Once you're happy with your docs and have things configured, you can build and deploy your docs.

1. **Build your site**:

    1. Generate a static build of your site:
    
       ```bash
       npm run build -- --out-dir ../docs
       ```

       This will generate a `docs` directory at the root of your repo with the static files for your site.

    1. Move to the repository parent directory, add, commit, and push files to GitHub:

       ```bash
       cd ..
       git add .
       git commit -m "Docs build"
       git push
       ```

1. **Publish your docs**:

    Surprise, this part is already done for you! After pushing updates to the _/docs_ directory, GitHub automatically builds and publishes your docs to `https://<github_username>.github.io/<repository_name>`. For example, [https://hawkeyexl.github.io/dac-test/](https://hawkeyexl.github.io/dac-test/).

Any time you want to update your docs, make whatever changes you like, rebuild your site, and push the files to your repository. It will be automatically published for you.
