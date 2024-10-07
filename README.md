# Docs as Code (with GitHub and Docusaurus)

This guide is an example of how to use [Docs as Code](https://www.writethedocs.org/guide/docs-as-code/) to create and publish documentation. This guide walks through using GitHub for version control, using Docusaurus and Markdown to write your docs, and using GitHub Pages to publish your docs.

## Before you start

You need the following to complete the guide:

- A GitHub account: You can sign up for a free account at [GitHub](https://github.com).
- Git: You can download and install Git from the [Git website](https://git-scm.com/downloads).
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
    - Run the following command in your terminal or command prompt to install Docusaurus globally:
      - `npm install -g docusaurus-init`
    - Run the following command to create a new Docusaurus project:
      - `docusaurus-init`
    - Follow the prompts to set up your project.
    - Navigate to the project directory:
      - `cd [project-name]`
      - Replace `[project-name]` with the name of your project.
      - Run the following command to start the development server:
        - `npm start`
        - Open your browser and go to `http://localhost:3000` to view your Docusaurus site.
        - You can now start writing your documentation using Markdown.
        - For more information on how to use Docusaurus, refer to the [official documentation](https://docusaurus.io/docs/en/installation).

2. **Make a small change**: 
    - Open the `docs` directory in your project.
    - Edit the `index.md` file to make a small change.
    - Save your changes and refresh the browser to see the updated documentation.
    - You can continue to make changes and preview them in the browser as you write your documentation.

3. **Build your site**:
    - Once you are happy with your documentation, you can build your site for deployment.
    - Run the following command in your terminal or command prompt:
      - `npm run build`
    - This will generate a `build` directory with the static files for your site.
    - You can deploy these files to a web server or use GitHub Pages to host your documentation.

4. **Add and commit your changes**:
   - In your terminal or command prompt, navigate to your project directory.
   - Run the following commands to add and commit your changes:
     - `git add .`
     - `git commit -m "Add initial documentation"`
   - Run the following command in your terminal or command prompt to push your changes to GitHub:
     - `git push origin main`
   - Your changes should now be pushed to your GitHub repository.

## Set up GitHub Pages

GitHub Pages is a feature of GitHub that allows you to host static websites directly from a GitHub repository. You can use GitHub Pages to host your documentation site for free.

Follow these steps to set up GitHub Pages:

1. **Set up GitHub Pages**:
    - Go to your repository on GitHub.
    - Click on the "Settings" tab.
    - Scroll down to the "GitHub Pages" section.
    - Under "Source", select the branch you want to use for GitHub Pages (e.g., `main` or `master`).
    - Click "Save".
    - Your site should now be published at `https://[username].github.io/[repository-name]`.
    - Replace `[username]` with your GitHub username and `[repository-name]` with the name of your repository.

7. **Push your changes**:
    - You can view your published documentation at `https://[username].github.io/[repository-name]`.