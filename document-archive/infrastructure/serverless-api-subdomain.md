# Serverless API Subdomain

By [default](https://github.com/scaffoldly/terraform-scaffoldly-bootstrap/blob/1fc5c7a78d53346d643c29aac1aa77adee85c1a1/variables.tf#L23-L26), Scaffoldly will host your Serverless APIs at `sly.your-domain.tld`. (`sly` is shorthand for "Scafoldly").

If you would like a different domain, you can change it in the `main.tf` of your `scaffoldly-bootstrap` project:

{% hint style="danger" %}
Changing this after your services are in use will cause downtime. The `sly` subdomain will be deleted.
{% endhint %}

```
module "bootstrap" {
  source  = "scaffoldly/bootstrap/scaffoldly"
  
  # ... other config
  serverless_api_subdomain = "api"
}
```

This will now host your Serverless APIs at `api.your-domain.tld`.
