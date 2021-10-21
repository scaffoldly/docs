---
description: This page explains how to run a Microservice locally
---

# Running Locally

After building, Scaffoldly created new repositories in your GitHub Organization. It's easy to run and debug them locally.

### Clone the Repository

```
➜  ~ git clone git@github.com:scaffoldly-demo/auth-sls-rest-api.git
Cloning into 'auth-sls-rest-api'...
remote: Enumerating objects: 98, done.
remote: Counting objects: 100% (98/98), done.
remote: Compressing objects: 100% (80/80), done.
remote: Total 98 (delta 20), reused 79 (delta 11), pack-reused 0
Receiving objects: 100% (98/98), 252.23 KiB | 1.24 MiB/s, done.
Resolving deltas: 100% (20/20), done.
```

### Download Dependencies

Run the `yarn` command

```
➜  ~ cd auth-sls-rest-api
➜  auth-sls-rest-api git:(main) yarn
yarn install v1.22.11
[1/4] 🔍  Resolving packages...
[2/4] 🚚  Fetching packages...
[3/4] 🔗  Linking dependencies...
...
yarn run v1.22.11
$ tsc
✨  Done in 16.64s.
✨  Done in 135.47s.
```

This will take a minute or so...

### Starting the Application

#### Command Line

Run `yarn start` to launch the Application

```
➜  auth-sls-rest-api git:(main) ✗ yarn start
yarn run v1.22.11
$ SLS_DEBUG=* serverless offline start
Serverless: Load command interactiveCli
Serverless: Load command config
...
   ┌─────────────────────────────────────────────────────────────────────────────────────┐
   │                                                                                     │
   │   ANY     | http://localhost:3000/auth                                              │
   │   POST    | http://localhost:3000/2015-03-31/functions/lambda-handler/invocations   │
   │   OPTIONS | http://localhost:3000/auth                                              │
   │   POST    | http://localhost:3000/2015-03-31/functions/lambda-handler/invocations   │
   │   ANY     | http://localhost:3000/auth/{proxy*}                                     │
   │   POST    | http://localhost:3000/2015-03-31/functions/lambda-handler/invocations   │
   │   OPTIONS | http://localhost:3000/auth/{proxy*}                                     │
   │   POST    | http://localhost:3000/2015-03-31/functions/lambda-handler/invocations   │
   │                                                                                     │
   └─────────────────────────────────────────────────────────────────────────────────────┘

offline: [HTTP] server ready: http://localhost:3000 🚀
offline:
offline: Enter "rp" to replay the last request
```

This should take 20-30 seconds to start...

#### Within VSCode

Open the Repository in VSCode, and in the **Debug** menu, click the **Play** icon next to **Local Debug**

![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 5.55.24 PM.png>) ![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 5.55.45 PM.png>)

![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 5.58.25 PM.png>)

You'll see the output in the VSCode Terminal and Debug Console.

### Use the Application

Here's a couple examples:

```
➜  ~ curl http://localhost:3000/auth/version
{"version":"1.0.0-2"}%
```

```
➜  auth-sls-rest-api git:(main) ✗ curl http://localhost:3000/auth/api/health
{"name":"auth-sls-rest-api","healty":true,"now":"2021-10-21T00:59:48.627Z","version":"1.0.0-2"}%
```

#### Swagger UI

> https://localhost:3000/auth/swagger.html

### Debug The Application

If you ran the project with VSCode, you can set breakpoints.

![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.02.14 PM.png>) ![](<../../.gitbook/assets/Screen Shot 2021-10-20 at 6.02.39 PM.png>)
