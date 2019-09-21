# vue-login-practice

## 1. Background:
This is a demo application for Login and Register function by using Vue

## 2. Installation:

Please make sure to follow the official website to install Vue properly. Here is the link:

https://cli.vuejs.org/guide/installation.html

Or you can directly run the following code:


```
npm install -g @vue/cli
# OR
yarn global add @vue/cli
```

and then check the version by using


```
vue --version
```

download the project either directly download the zip file or use git clone to download

Then go to project folder run:

```
npm install
```

Now you will be able to run the application locally(please make sure the port is not in using otherwise change the default port to a different number):

```
npm run serve
```

## 3. How to use:
![front page](https://i.ibb.co/k98FwNW/login.png)

This is the front page. The sign up function is under construction.

You can provide any username or password to sign in.

![after login](https://i.ibb.co/xfbMpm2/Capture.png)

After login you will see this welcome page with the user name on it.

## 4. Deployment:

use to generate the dist folder.
```
npm run build
```

or you can preview the production version by install serve locally:

```
npm install -g serve
```
And then use the following commend to preview
```
serve -s dist
```


## 5. Recommended improvements:

Here are some improvement suggestion:

- Add Unit test
- Add oauth(linkedin,  google...) to register
- Add forget password

