# FAQs

## What happens on the Initial Bootstrap? <a id="aws-org"></a>

1. Creates a new sub-AWS Account in the Organization of your Root Account
2. Sets up Cloud Logging
   1. CloudTrail
   2. CloudFront
   3. TODO: API Gateway Log Rotation from CloudWatch
3. Creates SSL/TLS Certificates
   1. Adds DNS Verification Records for the respective domain\(s\) in Route53 in the Root Account
4. Sets up API Gateway
   1. Adds `nonlive` and `live` domain names with their respective SSL/TLS Certificates
   2. Sets up CloudWatch Logs
   3. Adds CNAME records for the respective domain\(s\) in Route53 in the Root Account
5. If `auth_service = true` \(true, by default\) in `main.tf` of your `scaffoldly-bootstrap` project, the [Auth API](../backends-old/auth-api/) is created:
   1. Creates a GitHub repository named `sly-auth-api`in your GitHub organization which is cloned from a template of [scaffoldly/sly-auth-api-template](https://github.com/scaffoldly/sly-auth-api-template).
   2. Creates an IAM user, Access Key and Secret Key for GitHub Actions + Serverless deploys
      1. TODO: List specifics
   3. Creates an IAM role for functions to execute
      1. TODO: List specifics
   4. Sets up an API in API Gateway
      1. Creates an initial `/health` endpoint
      2. Configures Logging to CloudWatch
      3. Adds secrets/configuration for `live` and `nonlive` to the new GitHub Repo
   5. Configures Secrets Manager
      1. Adds an empty secret for `live` and `nonlive` to be maintained later
   6. Commits environment configuration to the GitHub Repo
      1. Shared Environment Variables
      2. URLs to other Services
   7. Triggers a `nonlive` release

## Why does Scaffoldly create an AWS Organization within my main AWS account? <a id="aws-org"></a>

TODO

## How do I run bootstrap from the beginning after I've already run it?

{% hint style="danger" %}
These instructions will destroy your infrastructure and start everything fresh. Proceed with caution.
{% endhint %}

1. Remove all API Gateway Domains
2. Remove all Cloudfront Distros
3. Delete sly records in Route53 in the Root Account
4. Generate a new Root Email
5. Update the `BOOTSTRAP_ROOT EMAIL` in the `scaffoldly-bootstrap` project secrets
6. Remove all sly-\* and sls-\* repos
7. Update the email address on Terraform Cloud
8. Delete scaffoldly-bootstrap from Terraform Cloud 
9. Run scaffoldly-bootstrap workflow\_dispatch \(creates a new AWS Organization\)
10. Delete the old AWS Organization



