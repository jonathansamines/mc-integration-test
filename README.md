# mc-integration-test

### Setup Steps

- Clone this repository
- Install dependencies
  - `npm install`
- You will need to your own MailChimp account (this is free to do). This is so that you can register a dummy application so that you have a client id and secret to use when testing:
  - Instructions to register an app can be found here:
    - https://mailchimp.com/developer/guides/access-user-data-with-oauth-2/#register-your-application
    - When you get to `Redirect URI` field, you should insert `http://127.0.0.1:3000/oauth/mailchimp/callback` as this is what is defined in the code we will use
- Once you have registered a dummy app, copy the `client id` and `client secret` and paste it in the respective `MAILCHIMP_CLIENT_ID` and `MAILCHIMP_CLIENT_SECRET` variables in the `index.js` file
- The code inside `index.js` is copied straight from Mailchimp's documentation
  - https://mailchimp.com/developer/guides/access-user-data-with-oauth-2/#implement-the-oauth-2-workflow-on-your-server
- I have made a change in this code so that we are using `simple-oauth2` when retrieving the access token - you can find this on `L89-95`.
- To run the application, you just need to execute the following command in your terminal:
  - `node index.js`
- Then open up the web page, and click on the `here` link to go through MailChimp's login page to authorise the app (you use the same Mailchimp credentials to authorise)

### Expected Behaviour

- After authorisng the app, you should get re-directed back to your local webpage, with the access token displayed.
  - You can re-create this by commenting out the simple oauth `getToken` logic i.e. comment out `L90-94`, and then uncomment `L69-85` and try re-running again.

### Actual Behaviour

- I get the `Error: Unexpected token in JSON at position 0` error mentioned
