# Adding Services

## Add a Web Portal

Need a web portals \(such as https://app.myproject.com\)? Scaffoldly has templates that are fully integrated with the Auth API and ready for login and basic account management.

Start from an available template:

* [Angular](../frontends/adding-a-frontend/angular.md)
* [Content Distribution Network \(CDN\)](../frontends/adding-a-frontend/cdn.md) \(for Static HTML, JavaScript, Images, Video, etc.\)
* React \(Coming Soon\)
* Vue \(Coming Soon\)

## Add APIs

Micro-services are the way to go. Our recommendation is to make many, narrowly focused services and avoid the monolithic API pattern. 

Scaffoldly makes it easy to provision a new API and there are templates available that are fully integrated with the Auth API and ready for use by the Web Portals and are integrated with the Auth API.

Start from an available template:

* [Serverless REST API](../backends-old/adding-a-backend/serverless-rest-api.md)
* Serverless GraphQL API \(Coming Soon\)

## Add More Cloud Infrastructure

You're not limited to the bootstrapping that Scaffoldly has put in place for you. 

You can add your own [Terraform](https://terraform.io) code to the `scaffoldly-bootstrap` project and start provisioning your customized infrastructure.

Have a look at [Adding Your Own Terraform Modules](../infrastructure-old/configuration-files/adding-your-own-terraform-modules.md).

## Ok great, what's next?

Go code!

And here's a laundry list of what have a look at as you continue to build:

* [Access the AWS Console for your new Organization](../infrastructure-old/console-access.md)
* [Live Deployment Checklist](../releases-versions-deployments/live-deploy-checklist.md)
* Adding Users to your Organization



