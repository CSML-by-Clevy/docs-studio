# Authenticating Users

In order to connect your users to various services, you may need to authenticate users. There are several ways to do this, depending on the authentication methods that are available in the 3rd-party service.

## Using Chatbot-wide Service Accounts

CSML chatbots run in a secure server, which means that you can load credentials for the service you want to access in your chatbot's [environment variables](bot-configuration-options.md#bot-wide-environment-variables) or either dynamically or statically accessing variables inside a flow. If a single set of credentials lets all your users access the service, it means that you probably created a dedicated _service account,_ an account specifically made for the chatbot to access your service with credentials that all users will use to perform the action they want to do.

This method is usually simple to implement (generate once and for all a set of credentials and load it in the chatbot) but has a major drawback: the same credentials are used for all of your users, which are now only differentiated between them by other means (for example, if the ID key is their email address, you could send them an email with a code to that email address to make sure that they are who they claim they are).

A good example of a service account is for things like database credentials, such as MySQL, MongoDB, or event cloud-based databases such as Airtable or Google Sheets. You will likely use the same database for all of your users: hence, one set of credentials should be stored on the server **(never expose them to the end users!)** and used for all requests to that service.

{% hint style="info" %}
In some cases where you can guarantee a high level of trust for the user's inputs (i.e when you can ensure that they are who they claim they are, for example when using an authenticated channel such as Microsoft Teams or Workplace by Meta, or when you verified the email address yourself), the service account could perform some actions _on behalf of_ the user: book an appointment, request a leave of absence...
{% endhint %}

## Using an OAuth2 Flow

In some cases, you may need to authenticate each user separately with their own separate authentication token, or the service does not support creating service accounts. For those cases and on supported channels (Web chat), we provide you with a generic OAuth 2 authorization component. To learn more about OAuth, this website has a lot of very useful information:

{% embed url="https://www.oauth.com/" %}

To initialize an OAuth flow for a given user, you should start by generating an OAuth App on the service you are going to use, in order to retrieve a `client_id` and `client_secret` values. You should also find the service's authorization endpoint (`authorization_endpoint`) as well as the endpoint where you will generate the access token (`token_endpoint`).

As an example, Github lets you create custom OAuth apps by visiting [https://github.com/settings/developers](https://github.com/settings/developers). As an aside, the "Personal Access Token" method that they offer is similar to creating a service account, but will perform all the API calls as they were made specifically by yourself, and never on behalf of the enduser. It may or may not let you build what you are looking for, hence the OAuth method, which lets the user perform all the calls as themselves.

![](<../.gitbook/assets/image (5).png>)

{% hint style="danger" %}
Note that the Callback URL (sometimes also called Redirect URL) should ALWAYS be `https://clients.csml.dev/v1/oauth/response`.
{% endhint %}

You should then generate a Client Secret. **NEVER** share this value publicly!

![](<../.gitbook/assets/image (4).png>)

We also need the Authorization Endpoint and Token Endpoint values, which we usually find in the API documentation in the "Auth" section. Sure enough, for github, this information can be found here:&#x20;

* Authorization endpoint: [https://docs.github.com/en/developers/apps/building-oauth-apps/authorizing-oauth-apps#1-request-a-users-github-identity](https://docs.github.com/en/developers/apps/building-oauth-apps/authorizing-oauth-apps#1-request-a-users-github-identity)
* Token endpoint: [https://docs.github.com/en/developers/apps/building-oauth-apps/authorizing-oauth-apps#2-users-are-redirected-back-to-your-site-by-github](https://docs.github.com/en/developers/apps/building-oauth-apps/authorizing-oauth-apps#2-users-are-redirected-back-to-your-site-by-github)

You will also need to pass a specific scope in the OAuth request, so that the generated access token has the right permissions for the calls you want to perform. How the scopes work is usually explained in the service's documentation.

Finally, in your CSML Studio code, add the following few lines (adapt with your own OAuth values):

```cpp
say OAuthRequest(
    client_id="XXXXX",
    client_secret="YYYYYY",
    authorization_endpoint="https://github.com/login/oauth/authorize",
    token_endpoint="https://github.com/login/oauth/access_token",
    scope="repo user",
    button=Button("Login with Github", payload="OAUTH_SUCCESS") as success
)
hold
```

{% hint style="info" %}
Make sure to update all the values with your own!
{% endhint %}

This will display the following button:

![](<../.gitbook/assets/image (3).png>)

If the response matches the button, it means that the OAuth flow succeeded. Otherwise, it was not successful (or the user did not authenticate at all).

```cpp
if (event.match(success)) {
  say "Your access token is: {{event.access_token}}"
}
else {
  say "No access token found in response. Error cause: {{event}}"
}
```

Using the access token, you can then start authenticating your API calls to the given service!

```cpp
do listRepos = HTTP("https://api.github.com/user/repos").set({
  "Authorization": "token {{token}}",
  "Accept": "application/vnd.github+json"
}).send()
```
