# User Authentication

If you enabled the Authentication microservice, additional services are pre-wired to use it for pass-through authentication.

Within other microservices, use the `@Securty('jwt')` annotation in the Controller on methods to enforce that an `Authorization` header is required with the request.

![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.14.48 PM.png>)

### Testing Authentication Locally

Microservices running **Locally** are configured to allow authentication tokens from the **Nonlive** environment.

Go to the [Scaffoldly Dashboard](https://start.scaffold.ly/dashboard) and find the JWT Token Generator

![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.14.30 PM.png>)

By default, emails can only be sent to your Scaffoldly email account, also shown on the Dashboard

![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 4.59.14 PM.png>)

![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.22.43 PM (1).png>) ![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.24.14 PM.png>) ![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.24.55 PM.png>) ![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.25.14 PM.png>)

Run your [Microservice locally](running-locally.md) (optionally in [Debug Mode](running-locally.md#debug-the-application)), and open the [Swagger UI](running-locally.md#use-the-application)

Click **Authorize** and paste the token, and invoke an endpoint with the padlock icon.

If you've set a breakpoint, you can see that the `httpRequest.user` is populated with the user's identity.

![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.29.38 PM (1).png>) ![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.29.55 PM (1).png>) ![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.31.30 PM.png>) ![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.32.22 PM.png>) ![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.33.00 PM.png>)
