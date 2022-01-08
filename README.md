# codeStyling
You can set visual studio code to fix your code styling according to Eslint on save ,

A - First of all,install dependencies:
```swift
    npm i eslint eslint-config-prettier eslint-plugin-prettier husky lint-staged prettier -D
```    
    
B - Now create two files in project root and rename those to .eslintrc.js,.prettierrc.js,

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
C - Now you should say to Visual Studio Code to fix wrong styles on save or paste.Open setting.json
(files>preference>setting>text editor>font>edit in settings.json)
copy this code in setings.json
```swift
    "editor.formatOnSave": true,
    "editor.formatOnPaste": true
```      
D - Finally open package.json and add theselines 
```swift
    "husky": {
      "hooks": {
        "pre-commit": "lint-staged"
      }
    },
    "lint-staged": {
      "**/*.{js,json}": [
                "eslint --fix ./",
        "prettier --write",
        "git add"
      ]
    }
```     

Now you can change any thing in .ts files and see Eslint fix your styling code to standard formattingon save .
