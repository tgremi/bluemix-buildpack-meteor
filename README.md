# Bluemix buildpack: Meteor

This buildpack is derived from [heroku-buildpack-meteorite](https://github.com/oortcloud/heroku-buildpack-meteorite) by [sweetleon](https://github.com/sweetleon) via [cloudfoundry-buildpack-meteorite](https://github.com/cloudfoundry-community/cloudfoundry-buildpack-meteorite).

This buildpack enables you to easily deploy meteor apps to IBM Bluemix

## Usage

Create a CF app and bind it to a MongoDB service. Then run the following command in your terminal:

```
cf push [APP_NAME] -b https://github.com/ind1go/bluemix-buildpack-meteor.git
```

## NOTES

You can specify meteor settings by setting the `METEOR_SETTINGS` environment variable:

```
cf set-env [APP_NAME] METEOR_SETTINGS '{"herp":"derp"}'
```

You need to have a service for MongoDB available and bound to the app. Alternatively, you can set `MONGO_URL` to point to your MongoDB outside of Cloud Foundry with the command:

```
cf set-env [APP_NAME] MONGO_URL mongodb://[SERVER]:[PORT]/[DB] # substitute your configuration values
```

## Websockets

To enable websockets on run.pivotal.io, you will need to use SSL over port 4443, e.g., `https://[APP_NAME].cfapps.io:4443/`
