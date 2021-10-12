# Using an Existing Domain

Scaffoldly will manage DNS records on your domain so you don't have to.

## Reserved Subdomains

Assuming your domain is `my-domain.tld`, by default, the following subdomain names are reserved:

* **`slyses`**`.my-domain.tld`: used for AWS SES inbound and outbound email
  * This is not modify-able
* **`sly`**`.my-domain.tld`: used as the Serverless API subdomain
  * [Alternatively](serverless-api-subdomain.md), set `serverless_api_subdomain`configuration in `scaffoldly-bootstrap`.

## Migrate Existing Records

Your domain will need to be hosted on AWS Route53 for Scaffoldly to work.

When adding your existing domain to Route53, be sure to copy the existing records into Route53. Most DNS providers have an export option:

After you create a hosted zone in AWS Route53, follow [these instructions](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/MigratingDNS.html).
