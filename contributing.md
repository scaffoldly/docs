---
description: >-
  We're so glad you're interested in Contributing to Scaffoldly or interested in
  learning more about our open source tooling.
---

# Contributing

If you'd like to contribute, [Join the Slack Community](https://scaffold.ly/community) and hop into the `#contributing` channel.

You can also check out the various Open Source Tooling we provide, maintain, use, and contribute to below.

## Open Source Components

Scaffoldly outfits a User or Organization with a lot of tooling. For transparency, we have open-sourced the tooling and components for full transparency of stacks we create and manage

### Infrastructure

#### Terraform for AWS

When the `scaffoldly-bootstrap` project is created, it's created using the [Terraform AWS Archetype](https://github.com/scaffoldly/archetype-scaffoldly-bootstrap).

The `scaffoldly-bootstrap` then configures an AWS account using the [Terraform AWS Bootstrap](https://github.com/scaffoldly/terraform-aws-bootstrap) Terraform Module, which is generally available in [Terraform Registry](https://registry.terraform.io/modules/scaffoldly/bootstrap/aws), as well as the [Additional Modules](https://registry.terraform.io/search/modules?namespace=scaffoldly) that are used. Links to the GitHub repositories can be found in each module within the [Scaffoldly Project on GitHub](https://github.com/scaffoldly).

### Code Templates

When Scaffoldly creates Microservices, we've partnered with an open-source template rendering tool called [Archetect](https://github.com/archetect/archetect). Scaffoldly has developed a [GitHub Action for Archetect](https://github.com/scaffoldly/archetect-render-action) to render Archetypes on a repository, and all projects are created using the [GitHub Template](contributing.md#open-source-components).

#### Serverless Express Microservices

When Microservices are created, they're creating using the [Serverless Express REST API Archetype](https://github.com/scaffoldly/archetype-express-serverless-rest-api). Various different ways we customize options in the generated tempates build it can be found [here](https://github.com/scaffoldly/archetype-express-serverless-rest-api/blob/2c4358a197c8daa13ec4f4d0865995a26b8a0d6b/.github/workflows/push-main.yml#L14-L21).

### CI/CD

#### Infrastructure

Scaffoldly provides a [Bootstrap Action](https://github.com/scaffoldly/bootstrap-action) to execute `terraform plan` and `terraform apply` operations within GitHub. This is automatically added to the `scaffoldly-bootstrap` repositories during [Template Rendering](https://github.com/scaffoldly/archetype-scaffoldly-bootstrap/tree/main/github/.github/workflows).

#### Microservices

Scaffoldly provides a [Bump Version Action](https://github.com/scaffoldly/bump-version-action) to execute deploys to AWS for `nonlive` and `live` environments. This is automatically added to each Microservice during [Template Rendering](https://github.com/scaffoldly/archetype-express-serverless-rest-api/tree/main/github/.github/workflows).

### Libraries

#### TypeScript

For each Serverless Express REST API that is generated, the [serverless-util](https://github.com/scaffoldly/serverless-util) [NPM package](https://www.npmjs.com/package/@scaffoldly/serverless-util) is added to simplify interaction with various components in AWS, such as Getting/Fetching Secrets, interacting with DynamoDB, and much more.

### Utilities

#### OpenAPI Generation

We've leveraged the [OpenAPI Generator](https://github.com/OpenAPITools/openapi-generator) project to automatically generate OpenAPI/Swagger docs when the project is built. In TypeScript, it auto-generates the OpenAPI document using [Tsoa](https://github.com/lukeautry/tsoa).

We've written a [Wrapper to the OpenAPI CLI](https://github.com/scaffoldly/openapi-generator) to discover and auto-generate OpenAPI docs for each [microservice in your project](https://github.com/scaffoldly/archetype-express-serverless-rest-api/blob/2c4358a197c8daa13ec4f4d0865995a26b8a0d6b/immutable/serverless/package.json#L12).

#### Dotenv

Each Microservice is outfitted with [Dotenv](https://www.npmjs.com/package/dotenv). To standardize environment variable injection from multiple locations in your project, we've written the [dotenv-out](https://www.npmjs.com/package/dotenv-out) CLI to write [multiple dotenv configurations to a single file](https://github.com/scaffoldly/archetype-express-serverless-rest-api/blob/2c4358a197c8daa13ec4f4d0865995a26b8a0d6b/immutable/serverless/package.json#L11) in various formats.

### Documentation

The documentation that you're reading now is [Open Source](contributing.md#docs) and we welcome contributions to it. The documentation is hosted generously for free by [GitBook](https://gitbook.com).
