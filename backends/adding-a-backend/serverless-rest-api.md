# Serverless REST API

### Provision the Backend in `scaffoldly-bootstrap`

Edit `main.tf` in the `scaffoldly-bootstrap` project

Within the `bootstrap`module, add the following:

```text
module "bootstrap" {
  source  = "scaffoldly/bootstrap/scaffoldly"
  
  # ... other configuration here ...
  
  serverless_apis = {
    # Use whatever name you like instead of example
    # The new GitHub repo will be `sls-example-api`
    # The endpoint will be hosted at https://sly.{stage_domain}/example 
    #                             or https://sly-{subdomain_suffix}.{stage_domain}/example
    example = {
      template = "scaffoldly/sls-rest-api-template"
    }
  }
}
```

Commit and push.

Observe GitHub Actions on `scaffoldly-bootstrap`

A release will be created on `scaffoldly-bootstrap`, if you're ready to create the portal, publish the release.

### The New Project

Following a successful release of `scaffoldly-bootstrap`, you will see a new project in you GitHub organization called`example-sls-rest-api`. \(If you stuck with the name `example`\)

Head on over to the GitHub Actions `example-sls-rest-api` and you will see the first release in process to `nonlive`.

Once the release has been finished, and assuming your `nonlive` domain is `myproject.dev`and the service name is `example` you can `curl` it as follows:

```text
# Output the version in package.json
curl -v https://sly.myproject.dev/example/version
```

