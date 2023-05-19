# 🥸npm Course
*Doing the course of NPM in Platzi*

## ✍🏼Initial steps
- In your terminal use **npm init**: this will create a *package.json* file, which contains the information of our project.

- Then, we will want to install some dependencies, to do that just use **npm install "dependencie name"**: for example *"npm install moment"* , this command will install the dependencies and the first time npm is called it will create a node_modules directory, this is where your dependencies will be hosted.

### 👀But, you can also use some flags to control the installation... for example:
- Use the flag **--save-dev** or **-D** : to install the dependencies as a development resource instead of a production one. *npm install eslint --save-dev* or *npm install eslint -D*.
- Now if you want to install a dependency for production you can use the flag **--save** or **-S** or even just the basic command without flags. *npm install react --save*

### 👁After this you might see something like this in your package.json:
"dependencies": {
    "moment": "^2.29.4",
    "react": "^18.2.0"
  },
  "devDependencies": {
    "eslint": "^8.40.0"
  }
*these are the dependencies we have installed both the production ones and the dev ones.

### 🌏Everything is ok till now... but! you also can install global dependencies
To do that, you have to be sure that the dependencies are able to be installed globally.
- Using the **-g** flag, you can easily install a global dependency: *npm install -g cowsay*
*cowsay javascript*
 ____________
< javascript >
 ------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

### 🤔Awesome! We did it... Now, lets say i'm not sure about how many dependencies have i installed or which
To see the dependencies installed you can use the following command:
**npm list**
it will show you something like this:
curso-npm@1.0.0 /Users/caper/Downloads/cursos platzi/Curso-npm
├── eslint@8.40.0
├── moment@2.29.4
└── react@18.2.0
*There is it!*...This command also works with the flag **-g** to see the global dependencies installed.

### 😵‍💫Well well... the project is getting bigger, don't you think?.
It's not crazy to say that when you have many dependencies it may be conflicting resources between them, for example: two dependencies are using the same package but in different versions. To aboid that problem use:
**npm install react-dom --dry-run**
this command will simulate the dependencies instalation so you can check the outcome and continue with the normal instalation if there are no conflicts.

### ⏰Installing an specific version of a package is something that you will need to do according to the project itself, so let's see how is it done:
**npm install json-server@0.15.0**
this command will install the 0.15.0 version of the json-server package in your project.
*in our package.json file we can see:*
"json-server": "^0.15.0",

### 🙈But, wait!... maybe i change my mind and now i want the latest version, how should i update my json-server package?
- Use the command **npm install json-server@latest** to install the latest version.
now our *package.json* file show:
"json-server": "^0.17.3",


### 😁Hey look!, i found something cool and i clone this project to try some stuff
To install the dependencies of a project just use the command **npm install**
This command will install the dependencies of the package.json file, the production and development dependencies.

## 😎Whats next?
**Great we have learned some new commands to use when starting a project, what's next?**
**npm run**
this command is used to call a script, scripts are created in your package.json file:
"scripts": {
    "start": "node src/index.js"
  },
In the previous example there is the start script, which invoke the *node src/index.js* command that executes the *index.js* file. So to call this script we use **npm run start**.
*We can create as many scripts as we want*

## 👻Working upon an old project
1. Get into your project, if you have clone it from github you will have to:
2. run the command **npm install** to install de packages and create the node_modules directory.
3. run the command **npm list** to see the list of dependencies installed.
4. This step is important because with the command **npm outdate** we will see which packages have a recently version that could be installed.

**The more dependencies you have the harder will be to update all of them and to fix conflicts between them** So always consider installing just the dependenciess that are really needed, specially in a long term project.

5. Use **npm audit** so you can see in some details about the vulnerabilities and if is possible to address them.
6. If you want to see even more details about the vulnerabilities use the command **npm audit --json** this will show us a estructured view of the vulnerabilities so you can consider whether to update, delete or replace packages.
7. Once you have audited the vulnerabilities, the console will suggest to use the **npm audit fix** command which will try to fix the vulnerabilities (vulnerabilities have three levels: moderate, high and critical).
8. Probably the console will also recomend you to use the command **npm audit fix --force** to address all the remainder issues.
9. **npm audit fix --force** may not fix all the vulnerabilities so, what's next?. By this point you should have less issues so run the *npm audit* again and address each one of them indidually with the **npm install "nameOfThePackage"@latest** to update every package related with the issue you see before.

## 😈How to delete a package?
To delete a package you have a couple of options:
1. Use the **npm uninstall "nameOfThePackage"** command to remove the package from your project, this will erase all the files related to the package.
2. Erase the dependencies directly from the *package.json* file, then run the command **rm -rf node_modules** to delete the directory and then with **npm install** we will create node_modules directory again with our dependencies.

**npm run build**
This command will prepare our project for production creating some files with the project ready to deploy. Now if you want a detailed version use *npm run build --dd*, this will show you more info about the process.

**npm ci**
Is a command that stands for "clean install." Unlike npm install , which can install packages from the node_modules cache, *npm ci* installs packages from the **package-lock.json** file. It's meant to be used in automated environments such as test platforms, continuous integration, and deployment or any situation where you want to make sure you're doing a clean install of your dependencies.

**Quick notes:**
- We can install optional dependencies using the **-o** flag.
- In your scripts from package.json you can use *&&* to say that after one command execute the next one:
**"start": "node src/index.js && node src/index.js"** In this case we execute the same code twice one after the first.
-**npx** *node package execute* is used to execute a package, this command is not for instalation so for example when you use vite to create a environment.
