# Set up project with webpack

## Learning objectives
- Use webpack to bundle JavaScript.

### Estimated time: 1.5h

## Exercise

In this exercise you will build a simple yet powerful webpack boilerplate, which you can later use as a starting point in your projects. You will be working with the webpack official guides, which you know already from the previous lesson.

*IMPORTANT NOTE: Read **all** instructions before you start this exercise.*

### Instructions

#### Initialize a new project and install webpack

- First set up a new GitHub repository for this exercise.
- Follow the instructions from the [getting started](https://webpack.js.org/guides/getting-started/#basic-setup) guide to set up the basics. Implement all the steps from *Basic Setup* to *NPM Scripts*.

#### Add HTML
- You already know that all the distribution files will be placed in */dist* directory. You also know that you should not create files manually in the */dist* folder, as there's a risk they will be overwritten. Therefore, install the HtmlWebpackPlugin to automatically create the **index.html** file in the */dist* directory. 
- Follow the instructions from the [setting up HtmlWebpackPlugin](https://webpack.js.org/guides/output-management/#setting-up-htmlwebpackplugin) guide. Be extra careful when updating the `module.exports` object in your **webpack.config.js** file, to not to make any nesting mistakes.
- Now delete all the files from the */dist* directory and run:
```
npm run build
```
- Check your */dist* folder. If it contains a new **index.html** file, it means you were successful. 

#### HTML template
- If you plan to write some HTML in your project, it's easiest to do it with a template. Create a **/src/index.html** in which you can write your markup. Add some basic page markup, like:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Wbpack Exercise</title>
</head>
<body>
    <h1>Hello webpack!</h1>
</body>
</html>

```
- Then modify **webpack.config.js** to point HtmlWebpackPlugin towards your template file:
```javascript
plugins: [
  new HtmlWebpackPlugin({
-   title: 'Output Management',
+   template: './src/index.html',
  }),
],
```
- You could remove the title property as well (as shown above), because you have set the page title in your **/src/index.html**.
- Run `npm run build` to update the **/dist/index.html**.
- View the **/dist/index.html** file in a code editor and notice how webpack inserted a `<script>` tag with correct path and minified the HTML for better performance.

#### Add CSS
The next step in building your webpack boilerplate is to add some style to it.
Follow the steps in [loading CSS](https://webpack.js.org/guides/asset-management/#loading-css) guide.

- In your **style.css** file add a generic rule, like:
```css
body {
    background-color: bisque;
}
```
- Next, execute `npm run build` and check if the HTML body style has changed.

#### Setup local dev server
Finally, it's time to improve your developer experience. When working on the project you will not want to run the build command from the terminal every time you make a change in the code. 
Therefore go ahead and install a webpack dev server, which will *watch* your source files, generate compiled distribution files and even refresh the browser every time you save changes in the source code.

- Follow the [using webpack-dev-server](https://webpack.js.org/guides/development/#using-webpack-dev-server) guide and set it up on your local machine.
Again, be cautious with updating the `module.exports` object in your **webpack.config.js**.
- Once these steps are complete, you should see your application working at: `http://localhost:8080/`. Every change you make in **js** or **css** files now should be reflected in a browser a few seconds later.

### Submit your exercise
[Read this FAQ for a reminder on how to submit your exercise.](https://microverse.zendesk.com/hc/en-us/articles/360061344234)
Now go to your Student Dashboard and submit your exercise. 
Please note that as it is an exercise you do not need a code review so, you can merge the pull request immediately after you are done with the task.
Paste the link to your GitHub repository.

## Additional materials
*These are all optional, but if you're interested in exploring this topic further, here are some resources to help you. Any exploration here should be done outside program time.*
- We strongly advise you to check the [official webpack documentation](https://webpack.js.org/concepts/) for better understanding of the tools you're using here.
- To check all available options for HtmlWebpackPlugin plugin configuraion, visit the [webpack plugin GitHub repo](https://github.com/jantimon/html-webpack-plugin).

------

_If you spot any bugs or issues in this activity, you can [open an issue with your proposed change](https://github.com/microverseinc/curriculum-transversal-skills/blob/main/git-github/articles/open_issue.md)._