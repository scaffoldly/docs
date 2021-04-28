# Angular

These instructions will provision a web portal from a Scaffoldly template thats fully integrated with the Auth API.

The following steps will create a web portal with a subdomain of `app`.

### Provision the Frontend in `scaffoldly-bootstrap`

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
}
```

Commit and push.

Observe GitHub Actions on `scaffoldly-bootstrap`

A release will be created on `scaffoldly-bootstrap`, if you're ready to create the portal, publish the release.

### The New Project

Following a successful release of `scaffoldly-bootstrap`, you will see a new project in you GitHub organization called `app-web-angular`.

Head on over to the GitHub Actions `app-web-angular` and you will see the first release in process to `nonlive`.

Once the release has been finished, and assuming your `nonlive` domain is `myproject.dev`, you can navigate in your browser to https://app.myproject.dev and see the new portal up and running!

