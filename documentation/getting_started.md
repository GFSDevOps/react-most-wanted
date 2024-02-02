# Getting started

## Installation

Run this command: `npx create-react-app link-app --template lnk`.

Then enter the created folder with `cd link-app`.

You can now start the application with `yarn run start`.

If you get error messages about peer dependencies during installation you can enable the legacy configuration for peer dependencies with this command: `yarn config set legacy-peer-deps true`. You can find more about that [here](https://github.com/yarn/rfcs/discussions/283)

## Changing Firebase project

To change the Firebase project used in the application we need to go to the file `src/config/config.js`. There we have a `json` object with all configurations for the application. The first one is called `firebase`. There we have separate configurations for `prod` (production) and `dev` (development). I would always recommend to have two separated Firebase projects. For each of them we copy the firebase configuration from our Firebase Console inside.

If you plan to use the messaging feature don't forget to copy the `publicVapidKey` from your Firebase project into the configs.

## Publishing to Firebase

### [Login to Firebase over your CLI](https://firebase.google.com/docs/cli)

### Select Firebase project

Using the command `firebase use --add` select your project and set the alias to `dev`, `prod` or `default`. I like to set all 3. That way you can select with the command `firebase use dev` or `firebase use prod` your Firebase project and publish your code there.

### Prepare functions

To publish this template to your Firebase project we need everything the projects needs. The database rules and routing are already prepared but we need to prepary the Firebase Cloud Functions to. To do so we enter the folder for the functions with `cd functions` and run `yarn i` to install all needed dependencies.

After that we need to set some environment configs for our functions with: `firebase functions:config:set gmail.email="test@email.com" gmail.password="Password"`
You can set here dummy data.

### Build and deploy

Before we can deploy our project we need to run `yarn run build`.
After that we can deploy it to Firebase with `firebase deploy`.
