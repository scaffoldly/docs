# Introducing Scaffoldly

{% embed url="https://youtu.be/N\_i9dDo0br8" %}

{% hint style="info" %}
This documentation is a work-in-progress and may be lacking in some areas, but we're actively working to improve it!  
  
Missing context on anything?[ Join the Slack Community](https://join.slack.com/t/scaffoldly/signup) and lets discuss it in the `#documentation` channel, we'll be happy to fill you in as quickly as possible.

Check out our [Roadmap](roadmap.md) for the documentation we'll be updating constantly.  
  
Glad you're here!   
  
-- **Christian**, Scaffoldly Founder, June 24, 2020
{% endhint %}

Many frameworks are great at getting you started, but drop the ball when it comes time to deploy, so you're left to patchwork your own solution together to get your project hosted in the Cloud, which can sometimes take a month of clicking around in the cloud console to get your project to host on your own domain name.

Scaffoldly is picking up the ball. We're taking those frameworks and taking it a step further.

Scaffoldly uses Open Source and widely accepted tools such as [Terraform](https://terraform.io), [Serverless](https://serverless.com) and [GitHub](https://github.com). You bootstrap your project with a few lines of "Infrastructure Code" and Scaffoldly provisions and secures an AWS account, and provides templates that are ready to launch so you can [get down to business](https://open.spotify.com/track/6f3Slt0GbA2bPZlz0aIFXN?si=0cf95135cc9b424e).

Scaffoldly itself is [Open Source](https://github.com/scaffoldly) and free. You can have a fully functional, secure, and infinitely scalable infrastructure within minutes instead of months, hosted on your own domain.

## Who's it For?

Scaffoldly is for **Startups** and **Personal Projects**. Ideally, you've written no code and you're starting with an idea and you're ready to code, but need a place to start.

Out target persona is a CTO ready to build a startup, and/or a hobbyist wanting to make a quick project.

## What Does it Do?

Scaffoldly aims to set up all of the primitives of hosting your project while not relinquishing any of the control to evolve over time. You own the code and infrastructure from end-to-end.

### Infrastructure

* **Infinitely Scalable**: Scaffoldly uses highly-scalable infrastructure services from AWS \(Lambda, API Gateway, CloudFront\). They're the experts at scaling, so you don't have to be.
* **Infrastructure-as-Code**: No more clicking around in the AWS Console "trying to get things to work". All infrastructure changes are managed via reviews and releases.
* **Cost Conscious**: Scaffoldly leverages Cloud Services that are pay-as-you-go \(Lambda, CloudFront, S3, API Gateway, etc\) so your month-to-month hosting costs are pennines on the dollar, and you're not paying dearly for "Idle Infrastructure".
* **Multiple Environments**: Scaffoldly provisions Non-Live and Live "environments/stages" so you have a safe place to experiment with your platform before making them available to the world.

{% hint style="success" %}
**Projects provisioned using Scaffoldly cost less than $0.15/day in Cloud costs**
{% endhint %}

### Security

* **Service-Level Identity**: Every service has an identity based on its GitHub repository name and every dependent service contains that name to restrict its access to just what it needs.
* **Logging/Auditing**: Scaffoldly automatically enables logging of your AWS Cloud Activity and Applications and those logs cannot be tampered with.
* **SSL/TLS**: Scaffoldly provisions SSL Certificates for your domain\(s\) so communication to your Portals and APIs are secure by default.
* **Authentication/Authorization**: Scaffoldly provides an Authentication/Authorization service out-of-the box that manages user authentication via JWT tokens that are usable throughout your Organization.
* **Complete Control**: All code is completely modify-able by you, there's no "black box".

### Applications and Services

* **Microservices**: Scaffoldly embraces the microservices architecture with a slight twist, instead of Docker Containers, each service contains multiple individual Lambda Functions that are name spaced by the GitHub repository and stage and presented as a single service.
* **Service Discovery**: Scaffoldly places a configuration file in each managed repository with a map of each service and how to communicate with them. No more complicated service mesh and discovery.
* **JWT Tokens**: Scaffoldly provides an Authentication API to generate JWT tokens for users that can be used across all applications and all services.
* **OpenAPI**: Each backend service automatically generates an OpenAPI specification and  using [tsoa decorators](https://tsoa-community.github.io/docs/) \(on the backend\) and the [OpenAPI generator](https://github.com/scaffoldly/openapi-generator) \(backends and frontends\) for a tight API contract between your backends and frontends.

### DevOps

* **Continuous Integration:** Each checkin to the main branch of a repository triggers a build and releases to Non-Live.
* **Continuous Delivery**: Each Non-Live deployment creates a Pre-Release in GitHub. When you're ready to go live, click a button in GitHub.
* **Infrastructure Changes**: Instead of running Terraform from your Laptop or clicking around in the AWS Console, all [Infrastructure-as-Code](https://en.wikipedia.org/wiki/Infrastructure_as_code). All changes are previewed and applied using GitHub Actions and GitHub Releases. Each change is versioned and there's a full audit trail and everything is predictable and uses a familiar pattern for deploying code.

## How Do I Set Started?

Start with our [Tutorials](tutorials/)!

