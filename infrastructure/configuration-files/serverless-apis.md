# Serverless APIs

## How Do I Change the Serverless API subdomain? <a id="serverless-api-subdomain"></a>

By default the Serverless API subdomain is `sly` \(shorthand for "Scaffoldly", creative right?!\) but if you want something more traditional like `api` its extremely easy to configure. In the `scaffoldly-bootstrap` project, edit the `main.tf` file, set the `serverless_api_subdomain` variable to the subdomain of your choice:

```text
module "bootstrap" {
  source  = "scaffoldly/bootstrap/scaffoldly"
  version = "..."
  
  ... other configuration options ...
  
  serverless_api_subdomain = "api"
}
```

{% hint style="danger" %}
Be extremely careful changing this after your project is up and running, since the subdomain of your services is changing, you'll have downtime in your **Nonlive** and **Live** environments until you deploy the updated configuration files. For more information, see the details about [Backend Deployments](../../releases-versions-deployments/backends.md) and the [Configuration Files](../service-discovery.md).
{% endhint %}

