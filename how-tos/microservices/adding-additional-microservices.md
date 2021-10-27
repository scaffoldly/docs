# Adding Additional Microservices

## Using [Scaffoldly Start](https://start.scaffold.ly)

The Scaffoldly Dashboard is an upcoming feature. Follow and upvote it in the [Issue Tracker](https://github.com/scaffoldly/start.scaffold.ly/issues/1).

For now, complete the steps Manually.

## Manually

The following instructions will allow you to provision a new Service the same way that Scaffoldly Start provisions them when the Infrastructure is first created.

### Create a Repository from the [GitHub Template](https://github.com/scaffoldly/github-template/generate)

* Add it to your Organization or User account managed by Scaffoldly
* Add a Description of `Managed by Scaffoldly` (**Important: **this is so our automations can detect it's one we should affect)
* Repository Naming:
  * Let's assume you want to call this service `payments` and have it accessible at `https://{{your-domain}}/payments`
  * Name the repository `payments-sls-rest-api` (all lower case, delimited with hyphens)
  * If you prefer, make it Private

### Render the Code Base from the Serverless Express Archetype

1. Go to **Actions** for the new repository
2. Choose **Render Template** then click **Run Workflow**
   1.  **Archetype Source Git URL**&#x20;

       [https://github.com/scaffoldly/archetype-express-serverless-rest-api.git](https://github.com/scaffoldly/archetype-express-serverless-rest-api.git)
   2.  **Archetect Render Options**

       `-s overwrite -s github -s serverless -s entity -a repository-name=payments-sls-rest-api -a persistence=dynamodb -a entities=example -a auth=true`

       1. _NOTE_: Update `repostiory-name` to match the repository name
       2. _NOTE_: Omit `-a auth=true` if you did NOT add the Authentication service (e.g.`auth-sls-rest-api` is not in your User/Organization
   3. **GitHub Token**
      1. Create and Provide a [Personal Access Token](https://github.com/settings/tokens) (if you don't already have one) that has `workflow` and `repo` permissions.
         1. NOTE: This token isn't stored anywhere, it is used once in the GitHub Action to commit changes to the repository

Click **Run Workflow**. In a few moments, you will see the Repository populated.

### Update the Scaffoldly Bootstrap Project

1. Navigate to the `scaffoldly-bootstrap` project
2. Go to **Actions**
3. Choose **Render Template** then click **Run Workflow**
   1.  **Archetype Source Git URL**

       [https://github.com/scaffoldly/archetype-scaffoldly-bootstrap.git](https://github.com/scaffoldly/archetype-scaffoldly-bootstrap.git)
   2.  **Archetect Render Options**

       `-s overwrite -s aws -s github -s serverless-api -a serverless-api-repos=payments-sls-rest-api`
   3. **GitHub Token**
      1. Use the same Personal Access Token from earlier

Click **Run Workflow**. In a few moments, you will see additional files added to the repository

* `aws-serverless-api-payments-sls-rest-api.tf`
* `aws-serverless-api-payments-sls-rest-api-github.tf`

### Provision the New Service

1. Within the `scaffoldly-bootstrap` project, go to **Actions**
2. Choose **Terraform Plan** then **Run Workflow**
3. No additional options are needed here, so click **Run Workflow** to start a `terraform plan` operation

A new Release will be created, which can be found by clicking **Releases** on the `scaffoldly-bootstrap` repository home page in GitHub.

![](<../../.gitbook/assets/Screen Shot 2021-10-27 at 8.59.01 AM.png>) ![](<../../.gitbook/assets/Screen Shot 2021-10-27 at 8.59.17 AM.png>)

Click the **Edit** icon (✎) and then click **Publish release**

Back under **Actions** you will be able to see the changes made to AWS under the **Terraform Apply** GitHub Action.

### Initial Nonlive Deploy

After the **Terraform Apply **is complete, navigate back to your new Repository and go to **Actions**. Our automations kicked off a **Nonlive Deploy **for you.&#x20;

If this did not happen please contact `#help` in our [Scaffoldly Slack](https://scaffold.ly/community).







