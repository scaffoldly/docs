# CDN

These instructions will provision a CDN for various uses.

The following steps will create a web portal with a subdomain of `content`.

### Provision the Frontend in `scaffoldly-bootstrap`

Edit `main.tf` in the `scaffoldly-bootstrap` project

Within the `bootstrap`module, add the following:

```text
module "bootstrap" {
  source  = "scaffoldly/bootstrap/scaffoldly"
  
  # ... other configuration here ...
  
  public_websites = {
    content = {
      template = "scaffoldly/web-cdn-template"
    }
  }
}
```

Commit and push.

Observe GitHub Actions on `scaffoldly-bootstrap`

A release will be created on `scaffoldly-bootstrap`, if you're ready to create the portal, publish the release.

### The New Project

Following a successful release of `scaffoldly-bootstrap`, you will see a new project in you GitHub organization called `content-web-cdn`.

Head on over to the GitHub Actions `content-web-cdn` and you will see the first release in process to `nonlive`.

Once the release has been finished, and assuming your `nonlive` domain is `myproject.dev`, you can navigate in your browser to https://content.myproject.dev and see the new portal up and running!

