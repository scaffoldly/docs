# FAQs

## General

### Why do I need a dedicated email for my project?

Scaffoldly creates a sub-organization on AWS. AWS requires an email address to create a sub-organization. AWS requires a unique email address for every organization. 

### My domain already is in use. Can I use it?

Probably, but there's some [extra steps](infrastructure-1/using-an-existing-domain.md).

## Infrastructure

### How do I access my Scaffoldly-created AWS Organization?

Check out [this article](https://aws.amazon.com/premiumsupport/knowledge-center/organizations-member-account-access/).

### SES can't send email. Why?

AWS SES, by default, is in Sandbox mode, so it can only send to verified email addresses. Scaffoldly automatically added your [Dedicated Project Email Address](tutorials/one-time-setup.md#dedicated-project-email-address) as a verified email address. Do one \(or both\) of the following:

* [Verify another email address](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/verify-email-addresses.html)
* [Leave sandbox mode](https://docs.aws.amazon.com/ses/latest/DeveloperGuide/request-production-access.html)

## Serverless APIs

## Frontends

## Releases & Deployments



