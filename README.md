# heroku-google-application-credentials-buildpack

Generates a Google credential file based on Heroku Config Vars.

This is useful when using a package such as [@google-cloud/storage](https://www.npmjs.com/package/@google-cloud/storage) which loads credentials from a file instead of an environmental variable.

## Usage

1. Create Config Var `GOOGLE_CREDENTIALS` and include the json contents wrapped in single quotes, eg: `'{"type":"...","key":"val"}'`
2. Create Config Var `GOOGLE_APPLICATION_CREDENTIALS` and set a value to the location you want the file `/app/google-credentials.json`.

The compile step will generate a script `/.profile.d/google-credentials.sh`
This script copies the contents of `GOOGLE_CREDENTIALS` into `GOOGLE_APPLICATION_CREDENTIALS` at startup.
