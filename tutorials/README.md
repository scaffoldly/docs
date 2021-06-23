# Tutorials

## Introduction

The tutorials in this section will build our Demo Organization:  
[https://github.com/scaffoldly-demo](https://github.com/scaffoldly-demo)

#### This tutorial will instruct the following:

* Set up a GitHub Organization and AWS account
* Add the Scaffoldly Bootstrap Template to the GitHub organization
* Add an API and a Portal
* Add a new API Endpoint to the backend and frontend
* Release to Live

#### Services created in the demo:

* Scaffoldly Bootstrap: [GitHub Repo](https://github.com/scaffoldly-demo/scaffoldly-bootstrap)
* Authentication API: [GitHub Repo](https://github.com/scaffoldly-demo/sly-auth-api) \| OpenAPI: [Non-Live](https://swagger.scaffold.ly/?url=https://sly-dev.scaffoldly.xyz/auth/openapi.json), [Live](https://swagger.scaffold.ly/?url=https://sly.scaffoldly.xyz/auth/openapi.json)
* "Cool" API OpenAPI: [GitHub Repo](https://github.com/scaffoldly-demo/cool-sls-rest-api) \| OpenAPI: [Non-Live](https://swagger.scaffold.ly/?url=https://sly-dev.scaffoldly.xyz/cool/openapi.json), [Live](https://swagger.scaffold.ly/?url=https://sly.scaffoldly.xyz/cool/openapi.json)
* "App" Angular Portal: [GitHub Repo](https://github.com/scaffoldly-demo/app-web-angular) \| Portal: [Non-Live](https://app-dev.scaffoldly.xyz), [Live](https://app.scaffoldly.xyz)

## One Time Setup

⏱Too fast? 📕 Don't want to watch the video? [Follow these steps](one-time-setup.md#prerequisites)

{% embed url="https://youtu.be/08wrzSMRFz0" %}

#### Questions / Links

* ❓ [Why a dedicated email address?](../faqs.md#why-do-i-need-a-dedicated-email-for-my-project)
* 🔗 [New GitHub Organization](https://github.com/organizations/plan)
* ⚠️ [Updating your domain to Route53](../infrastructure-1/using-an-existing-domain.md)
* 📕 [Policy Document](one-time-setup.md#iam-role)
* 🔗 [Terraform Cloud](https://www.terraform.io/cloud)
* [🔗 Scaffoldly Bootstrap Template](https://github.com/scaffoldly/bootstrap-template)
* [❓ What does Scaffoldly Create?](https://github.com/scaffoldly/terraform-scaffoldly-bootstrap/blob/main/README.md)

#### For Your Reference

* [Scaffoldly Demo Organization](https://github.com/scaffoldly-demo)
* [Stages Configuration](https://github.com/scaffoldly-demo/scaffoldly-bootstrap/blob/76206b8a41af9e2a58c0eba3c987f3f65ab46ea3/main.tf#L20-L28)

#### Repo Secrets

1. `BOOTSTRAP_ROOT_EMAIL`: The [Dedicated Project Email Address](one-time-setup.md#dedicated-project-email-address) you created earlier
2. `BOOTSTRAP_AWS_ACCESS_KEY_ID`: The [AWS Access Key](one-time-setup.md#iam-user) in the CSV you downloaded
3. `BOOTSTRAP_AWS_SECRET_ACCESS_KEY`: The AWS Secret Key in the CSV you downloaded
4. `BOOTSTRAP_GITHUB_TOKEN`: The [GitHub Access Token](one-time-setup.md#github-token) you created
5. `BOOTSTRAP_TERRAFORM_TOKEN`: The [Terraform API Key](one-time-setup.md#terraform-cloud) you created

## Add a New Services

### Serverless API

⏱Too fast? 📕 Don't want to watch the video? Follow these steps

{% embed url="https://youtu.be/rlSJU3jzEPQ" %}

### Web Portal Implementation

⏱Too fast? 📕 Don't want to watch the video? Follow these steps

{% embed url="https://youtu.be/6EYJ2\_631kU" %}

## Add a New API Endpoint

### Backend

⏱Too fast? 📕 Don't want to watch the video? Follow these steps

{% embed url="https://youtu.be/51ayFP8WOms" %}

### Frontend

⏱Too fast? 📕 Don't want to watch the video? Follow these steps

{% embed url="https://youtu.be/aVzwuKzru90" %}

## Push to Live

⏱Too fast? 📕 Don't want to watch the video? Follow these steps

{% embed url="https://youtu.be/5Ybef2xzwC0" %}



