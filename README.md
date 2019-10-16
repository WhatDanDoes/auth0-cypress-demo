# auth0-cypress-demo

This was all straight up jacked from [this fine fellow](https://auth0.com/blog/end-to-end-testing-with-cypress-and-auth0/). Although this app implements the _password_ grant type, it does demonstrate the desirable _Stay logged in_ SPA functionality for which we are all hungry.

The original app took a bit of _massaging_ to get running. Dependencies are probably all up to date...

## Setup

Clone the repo and install:

```
npm install
```

### Configure

```
cp .env.sample .env
```

Fill in the blanks in your `.env` file:

```
REACT_APP_AUTH0_DOMAIN=dev-sillsdev.auth0.com
REACT_APP_AUTH0_CLIENT_ID=SomeCrazyFakeID
```

Do likewise in `src/conf.gs`: 

```
const {
  REACT_APP_AUTH0_DOMAIN: AUTH0_DOMAIN = 'dev-sillsdev.auth0.com',
  REACT_APP_AUTH0_CLIENT_ID: AUTH0_CLIENT_ID = 'somePseudoRandomAppID',
} = process.env;

//...
```

## Dev Server

```
npm start
```

## Test

This is the best part!

### Configure

```
touch cypress.env.json
```

Your config will look something like this:

```
{
  "auth_audience": "https://my_tenant.auth0.com/api/v2/",
  "auth_url": "https://my_tenant.auth0.com/oauth/token",
  "auth_client_id": "my_client_id",
  "auth_client_secret": "my_client_secret",
  "auth_username": "my_username",
  "auth_password": "my_password"
}
```

Open browser-based test interface:

```
npm start &       # <-- Or open another terminal
npm run cypress:open
```

## Notes

[The blog tutorial](https://auth0.com/blog/end-to-end-testing-with-cypress-and-auth0/) was a little sketchy on one particular setting...

To get the `cypress` test running, I needed to set a _Default Directory_ under the SIL account settings:

- Dashboard > Account Dropdown (in the upper-right) > Settings
- Under “API Authorization Settings”:
  - Default Directory: `Username-Password-Authentication`

