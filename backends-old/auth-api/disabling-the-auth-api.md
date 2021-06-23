# Disabling the Auth API

{% hint style="info" %}
Make sure you have an appropriate alternative in place and have modified your frontends and other APIs prior to disabling the Auth API.
{% endhint %}

{% hint style="warning" %}
If you disable the Auth API, existing JWT tokens that have been issued will no longer be able to be generated/verified. 
{% endhint %}

{% hint style="danger" %}
The out-of-the-box frontends depend highly on the Auth API. If you haven't modified them to work without the Auth API, they will cease to function properly.
{% endhint %}

The Auth API can be disabled by setting `auth_service = false` within the `bootstrap` block of `main.tf` of your `scaffoldly-bootstrap` project:

{% hint style="warning" %}
This will **DELETE** `/auth`from API Gateway and delete the `sly-auth-api` from your GitHub Organization as if they never existed.
{% endhint %}

```text
module "bootstrap" {
  source  = "scaffoldly/bootstrap/scaffoldly"
  
  # ... other configuration ...
  
  auth_service = false
}
```

