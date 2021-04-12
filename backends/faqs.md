# FAQs

## Why not leverage API Gateway Stages for `live` and `nonlive`?

We wanted `live` and `nonlive` to be clones of each other, not dependent on each other. 

This way, setting `NODE_ENV=nonlive` or `NODE_ENV=live`when doing a `serverless deploy` command, allows all the functions to be updated atomically without having the and visibility and knowledge about other environments allowed for the greatest level of flexibility in management and releases.

## Why not leverage Auth0 or Cognito for the Auth API?

We wanted to reduce the number of external dependencies required to bootstrap a project. Also, prescribing authentication providers is not our job, thats your decision. While we've built the Auth API to be flexible and modify-able, if you prefer to use a different provider, that's entirely up to you. The Auth API can be easily removed.





