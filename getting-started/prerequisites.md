# Prerequisites

## AWS Account \("Root Account"\)

Scaffoldly will require an AWS account to get started, and it will create a dedicated organization within your AWS account, which has [various benefits](../infrastructure-old/faqs.md#aws-org).

1. If you don't already have an AWS Account, [create one](https://portal.aws.amazon.com/billing/signup)
   1. This account will be used as the Root account
   2. All Scaffoldly resources will be created in a separate sub-account

### Dedicated Domain \(or Subdomain\) For Your Project

Scaffoldly will require at least one dedicated domain \(or subdomain\). The domain can be registered anywhere, but needs to be hosted in Route53 for the AWS "Root Account". For more information on this see the page on [DNS](../infrastructure-old/dns.md).

1. If you haven't already, manually add a Hosted Zone for your domain \(or subdomain\) in the [Route53 console](https://console.aws.amazon.com/route53)
   1. Your domain can be a domain \(myproject.com\) or a subdomain \(myproject.mycompany.com\)
   2. You can also have a second domain \(myproject.dev\) or a subdomain \(myproject.mycompany.dev\) if you wish for other stages
   3. See [DNS](../infrastructure-old/dns.md) for the various ways you can configure this
2. Make note of the **Hosted Zone ID** of each domain, as you'll need it in the next step.
3. Set the Name Servers for your domain or subdomain to the NS records for your domain hosted at Route53. For information on how to do this, please refer to the documentation of your domain registrar \(GoDaddy, 101domains, etc.\) or your primary DNS provider \(if you're using a subdomain\)

### Access Privileges

Scaffoldly needs a very light privileges in the AWS Root Account.

1. In the AWS "Root Account" Create a new [IAM User](https://console.aws.amazon.com/iam/home#/users$new)
   1. The name is unimportant, as a recommendation, you could use `scaffoldly-bootstrap`
   2. Enable **Programatic Access** so an Access Key and Secret Key are created
   3. Save the **Access Key and Secret Key**, you'll need it in few steps
   4. Once the user is created, add an **Inline Policy**, and paste the following into the JSON tab in IAM: `{   "Version": "2012-10-17",   "Statement": [     {       "Effect": "Allow",       "Action": [         "organizations:*",         "route53:List*",         "route53:Get*"       ],       "Resource": "*"     },     {       "Effect": "Allow",       "Action": [         "sts:AssumeRole",         "route53:ChangeResourceRecordSets"       ],       "Resource": [         "arn:aws:iam::*:role/ScaffoldlyBootstrap",         "arn:aws:route53:::hostedzone/YOUR-HOSTED-ZONE-ID"       ]     }   ] }`
      1. Be sure to change `YOUR-HOSTED-ZONE-ID` to the **Hosted Zone Id** from the previous step.
         1. If you have multiple domains Scaffoldly is to manage \(e.g. myproject.dev\), add those Zone IDs on separate lines as well.

## Dedicated Email Address

1. Create a new "root" email address for your project, for example \(myproject@mycompany.com\)
   1. It must NOT be the same as the email address of your root AWS account
   2. It must NOT have been used previously at AWS for another AWS account

## GitHub Organization and Token

1. Create a GitHub account \(if you don't have one already\)
2. Create a [**GitHub Organization**](https://github.com/account/organizations/new)\*\*\*\*
3. Create a [**GitHub Token**](https://github.com/settings/tokens/new), save it for a moment, you'll need it in a few steps
   1. 1. [x] `repo`
      2. [x] `workflow`
      3. [x] `admin:org`
         1. [x] `org:read`
         2. [x] `org:write`

## Terraform Cloud

1. Create a [**Terraform Cloud**](https://app.terraform.io/signup/account) account
   1. Username: Same as your GitHub Organization
   2. Email: The Dedicated Email Address you created earlier
2. Create an [**API Token**](https://app.terraform.io/app/settings/tokens), save it for a moment, you'll need it in a few steps
   1. Name: scaffoldly-bootstrap

## Great! You're ready to go, continue to [**Bootstrapping**](bootstrapping.md).



