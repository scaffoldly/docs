# Angular

These instructions will provision a web portal from a Scaffoldly template thats fully integrated with the Auth API.

{% hint style="info" %}
If you don't wish to have a web portal, continue to the next section.
{% endhint %}

The following steps will create a web portal with a subdomain of `app`.

### Create a Google Client ID

{% hint style="info" %}
Currently only Google Login has been integrated, Apple Login and Email login will soon be added.
{% endhint %}

{% hint style="success" %}
These steps will soon be automated by Scaffoldly Bootstrapping
{% endhint %}

1. Navigate to the [Google Cloud Console](https://console.cloud.google.com/apis/credentials)
2. Create a new Project
3. Configure the [OAuth Consent Screen](https://console.cloud.google.com/apis/credentials/consent)
   1. Authorized Domains: Add the top level domains scaffoldly is managing, e.g. "myproject.com" \(and additionally, "myproject.dev"\)
   2. Non-Sensitive Scopes: 
      1. .../auth/userinfo.email
      2. .../auth/userinfo.profile
      3. openid
4. Create a OAuth Client ID
   1. Type: Web Application
   2. Allowed Javascript Origins:
      1. http://localhost:4200
      2. https://app.myproject.dev
         1. or https://app-dev.myproject.com if you're using a `subdomain_suffix` of `dev` in `scaffoldly-bootstrap`, for example
      3. https://app.myproject.com

### Enable the Service in `scaffoldly-bootstrap`

Edit `main.tf` in the `scaffoldly-bootstrap` project

Within the `bootstrap`module, add the following:

```text
module "bootstrap" {
  source  = "scaffoldly/bootstrap/scaffoldly"
  
  # ... other configuration here ...
  
  public_websites = {
    app = {
      template = "scaffoldly/web-angular-template"
    }
  }
  
  shared_env_vars = {
    GOOGLE_CLIENT_ID = "YOUR-CLIENT-ID-HERE"
  }
}
```

Commit and push.

Observe GitHub Actions on `scaffoldly-bootstrap`

A release will be created, if you're ready to create the portal, publish the release.

