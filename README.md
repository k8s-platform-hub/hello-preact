[**Preact**](https://preactjs.com) is a 3kB fast React alternative with the same modern API. Comes with all the power of Virtual DOM Components without the overhead. It has familiar React API & Patterns, JSX support, SSR and a highly optimized diff algorithm.

## What does this come with?

* Preact.js Starter Project
  * Automatic reloading and bundling
  * Project scaffolding with *preact-cli*.
* Deployed with the [**superstatic**](https://www.npmjs.com/package/superstatic) package
* **Dockerfile** (automatically used by Hasura for deployment)

```
FROM node:8

WORKDIR /src

#Install deps
COPY src/package.json /src/package.json
RUN cd /src && npm install

#Add all source code
ADD src/ /src/
RUN cd /src

#Default command
CMD ["npm","run","prod"]
```

## Deployment instructions

### Basic deployment:

* Press the **Clone & Deploy** button and follow the instructions.
* The `hasura quickstart` command clones the project repository to your local computer, and also creates a **free Hasura cluster**, where the project will be hosted for free.
* A git remote (called hasura) is created and initialized with your project directory.
* Run `git add .`, `git commit`, and `git push hasura master`.
* Run the below command to open your new deployed Preact app.
``` shell
$ hasura microservice open www
```

### Making changes and deploying

* To make changes to the project, browse to `/microservices/www/src` and edit the files in `src` folder according to your app.
* Commit the changes, and perform `git push hasura master` to deploy the changes.

## Local development

To test and make changes to this app locally, follow the below instructions.
* Open Terminal and `cd` into the project folder
* Run `npm install` to install all the project dependencies
* Run `npm start` in the terminal to run it. This also enables hot reloading.
* Make changes to the app, and see the changes in the browser

## View server logs

You can view the logs emitted by the ‘superstatic’ package by running the below command:

``` shell
$ hasura microservice logs www
```
You can see the logs in your terminal, press `CTRL + C` to stop logging.

## Managing app dependencies

* System dependencies, like changing the web-server can be made in the Dockerfile
* npm/yarn deps can be managed by editing **package.json**.

If changes have been done to the dependencies, `git commit`, and perform `git push hasura master` to deploy the changes.

## Migrating your existing Preact.js app

* If you have an existing Preact app which you would like to deploy, replace the code inside `/microservices/www/src/` according to your app.
* You may need to modify the Dockerfile if your `package.json` or the build directory location has changed, but in most cases, it won't be required.
* Commit, and run `git push hasura master` to deploy your app.

## Adding backend features

Hasura comes with BaaS APIs to make it easy to add backend features to your apps.

### Add instant authentication via Hasura’s web UI kit

Every project comes with an Authentication kit, you can restrict the access to your app to specific user roles.
It comes with a UI for Signup and Login pages out of the box, which takes care of user registration and signing in.

![Auth UI](https://docs.hasura.io/0.15/_images/uikit-dark.png)

Follow the [Authorization docs](https://docs.hasura.io/0.15/manual/users/uikit.html) to add Authentication kit to your app.

### Add a custom API

Hasura project is composed of a set of microservices. These include certain Hasura microservices like, postgres, nginx, data API, auth API and more but can also include your own microservices.

* [Adding Microservice](https://docs.hasura.io/0.15/manual/custom-microservices/index.html)

### Add data APIs

Hasura comes with set of Data APIs to access the Postgres database which comes bundled with every Hasura cluster.
Detailed docs of data APIs can be found [here](https://docs.hasura.io/0.15/manual/data/index.html).

### Using the API console

The hasura CLI gives you a web UI to manage your data modelling, manage your app users and explore the Hasura APIs.
The API explorer gives you a collection of all the Hasura APIs and lets you test them easily.

Access the **api-console** via the following command:

```
$ hasura api-console
```

This will open up Console UI on the browser. You can access it at [http://localhost:9695](http://localhost:9695)
