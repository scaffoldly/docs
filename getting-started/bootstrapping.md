# Bootstrapping

## Create Bootstrap Repository

1. Create the [Scaffoldly Bootstrap](https://github.com/scaffoldly/bootstrap-template/generate) repository into to the GitHub organization you [created](prerequisites.md)
   1. Name it `scaffoldly-bootstrap`
      1. It's OK \(and recommended!\) to keep it **Private**
2. Go to **Settings** &gt; **Secrets** for `scaffoldly-bootstrap` in your organization
3. Add five new **Repository** **Secrets**
   1. `BOOTSTRAP_ROOT_EMAIL`: The email address you [created](prerequisites.md#dedicated-email-address)
   2. `BOOTSTRAP_AWS_ACCESS_KEY_ID`: The AWS Access Key you [created](prerequisites.md#aws-root-account)
   3. `BOOTSTRAP_AWS_SECRET_ACCESS_KEY`: The AWS Secret Key
   4. `BOOTSTRAP_GITHUB_TOKEN`: The GitHub Access Token you [created](prerequisites.md#github-organization-and-token)
   5. `BOOTSTRAP_TERRAFORM_TOKEN`: The Terraform API Key you [created](prerequisites.md#terraform-cloud)
4. You can now dispose of copies you made of these secrets, you won't need them again.

## Clone and Modify the Bootstrap Repository

1. Clone your newly created repository
2. In your favorite editor, modify `main.tf`
3. Find the section that starts with `module "bootstrap" {` and make the following modifications
   1. Set your domain\(s\) and/or subdomain\(s\) in the `stages` block
      1. There's two predetermined stages: "_**nonlive**_" \(aka "dev", "sandbox", "staging"\) and "_**live**_" \(aka "production"\), so **don't change those keywords**.
      2. The values in `domain` must match the **Hosted Zone** in Route53 of the Root Account
      3. For example, to have your API hosted at `myproject.dev` and/or `myproject.com` for `nonlive` and `live`, respectfully, you would have: `stages = {   nonlive = {     domain = "myproject.dev"     # or to suffix nonlive subdomains with '-dev.myproject.com'     # domain = "myproject.com"     # subdomain_suffix = "dev"   }   live = {     domain = "myproject.com"   } }`
      4. For alternative configuration options, see the [Configuration Files](../infrastructure/configuration-files/) documentation.
4. Commit and Push your updates
   1. A `terraform plan`operation will automatically happen after you push. **No changes will be made**. A `plan` is simply a "preview mode" to see the changes that are proposed.
      1. [What's going to happen on initial bootstrap?](../infrastructure/faqs.md#aws-org)
   2. In the next section, you'll see how to observe and execute the changes

## Spinning Up Your Infrastructure

All infrastructure changes are made by creating and/or publishing releases on the `scaffoldly-bootstrap` repository, a very familiar paradigm for most developers.

1. Open the Releases page for the `scaffoldly-bootstrap` repository
   1. Found on the right of your projects page in GitHub by clicking on **Releases**
2. You will see a new **Draft** release, likely called **0.1.0-0**
   1. The output of the `terraform plan` action is posted here, detailing all of the changes that are queued to be changed.
   2. Review it, make sure everything looks in order.
   3. The first release will have a substantial number of resources to create, for a rundown of what's being created, check out [What's going to happen on initial bootstrap?](../infrastructure/faqs.md#aws-org)
3. Click **Edit** for the draft
4. Click **Publish Release**
5. To watch the changes occur:
   1. Go to **Actions** at the top
   2. You should see an active job with the name of the Release you just published, click on that
   3. Click on **apply** to view the output

Once the apply finishes, you will see a few things:

* A new repo in your GitHub organization called `sly-auth-api`
* `sly-auth-api` will be running an Action doing its initial release to `nonlive`

Once the `sly-auth-api` `nonlive` release finishes, you can check that it's up by doing:

```text
# Change myproject.dev to be whatever your nonlove domain is
curl -v https://sly.myproject.dev/auth/api/v1/login/certs

# If you chose to use a subdomain suffix, such as "dev":
# curl -v https://sly-dev.myproject.com/auth/api/v1/login/certs
```

## Great! Your Infrastructure has now been prepared by Scaffoldly and Terraform! Continue to [Adding Services](adding-services.md)

