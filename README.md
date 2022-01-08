# codeStyling # Eslint # prettier #visual code code styling
You can set visual studio code to fix your code styling according to Eslint on save ,

<b>A </b>- First of all,install dependencies:
```swift
    npm i eslint eslint-config-prettier eslint-plugin-prettier husky lint-staged prettier -D
```    
    
<b>B</b> - Now create two files in project root and rename those to .eslintrc.js  &  .prettierrc.js,

copy this code in .eslintrc.js
```swift
    module.exports = {
      env: {
        commonjs: true,
        es2020: true,
        node: true,
      },
      extends: ["plugin:prettier/recommended"],
      parserOptions: {
        ecmaVersion: 11,
      },
      rules: {
        indent: ["error", "tab"],
        "linebreak-style": ["error", "unix"],
        quotes: ["error", "double"],
        semi: ["error", "never"],
      },
    }
```  
copy this code in .prettierrc.js
```swift
    module.exports =  {
        semi: false,
        useTabs: true
    }
```  
<b>C </b>- Now you should say to Visual Studio Code to fix wrong styles on save or paste.Open setting.json
(files>preference>setting>text editor>font>edit in settings.json)
copy this code in setings.json
```swift
    "editor.formatOnSave": true,
    "editor.formatOnPaste": true
```      
<b>D </b>- Finally open package.json and add theselines 
```swift
    "husky": {
      "hooks": {
        "pre-commit": "lint-staged"
      }
    },
    "lint-staged": {
      "**/*.{js,json,sacc,scss,css,html,ts}": [
         "eslint --fix ./",
        "prettier --write",
        "git add"
      ]
    }
```  
Here we have a hook that runs before commit. lint-staged executes commands line by line, but here only files with js and json extensions are checked, which you can add if you have files with other extensions that you want to check.<br>
<b>To ignore some files</b> and folders, such as node_modules, you must create ignore files for each one and enter the name of the file or folder in them as follows:<br>
create .eslintignore & .prettierignore in root project folder
and add folder name that you want ignore code style checking<br>
as instance you can add node_modules to ignore checking

<b>E</b> - Now you can change any thing in .TST,HTML,SASS,CSS,SCSS files and see Eslint fix your styling code to standard formatting on save .
