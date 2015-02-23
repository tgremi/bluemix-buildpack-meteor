# Bluemix buildpack: Meteor

This buildpack is derived from [heroku-buildpack-meteorite](https://github.com/oortcloud/heroku-buildpack-meteorite) by [sweetleon](https://github.com/sweetleon) via [cloudfoundry-buildpack-meteorite](https://github.com/cloudfoundry-community/cloudfoundry-buildpack-meteorite).

This buildpack enables you to easily deploy meteor apps to IBM Bluemix.

## Usage

Create a CF app and bind it to a MongoLab service. _N.B.: MongoLab, not mongodb._ Then run the following command in your terminal:

```
cf push [APP_NAME] -b https://github.com/ind1go/bluemix-buildpack-meteor.git
```

Alternatively, you can specify the buildpack in your manifest.yml, if you have one:

```
  buildpack: https://github.com/ind1go/bluemix-buildpack-meteor.git
```

## NOTES

You can specify meteor settings by setting the `METEOR_SETTINGS` environment variable:

```
cf set-env [APP_NAME] METEOR_SETTINGS '{"herp":"derp"}'
```

You need to have a service for MongoLab available and bound to the app. Alternatively, you can set `MONGO_URL` to point to your MongoDB outside of Bluemix with the command:

```
cf set-env [APP_NAME] MONGO_URL mongodb://[SERVER]:[PORT]/[DB] # substitute your configuration values
```

Meteor projects tend to contain MBs of dependencies that will be re-downloaded by the buildpack, and they can take a while to upload. It's a good idea to ignore the `.meteor/local` folder within your Meteor project. To do so, create or modify a file called `.cfignore` in the root of the project, and add the following line to it:

```
.meteor/local
```
