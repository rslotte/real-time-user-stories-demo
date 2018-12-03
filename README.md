# Real-time User Stories Demo


This repository contains the code used to demo building feature branches from Github with AWS Codebuild and deploying onto AWS Fargate.


## Codebuild Project


To create the Codebuild project:
```
$ aws cloudformation create-stack --stack-name real-time-user-stories-codebuild --template-body file://codebuild.yml --parameters \
ParameterKey=RepositoryLocation,ParameterValue=https://github.com/rslotte/real-time-user-stories-demo.git \
--capabilities CAPABILITY_NAMED_IAM
```


Modify the trigger if you only want to build on a specific branch naming pattern:
```
$ aws codebuild update-webhook --project-name branch-deploy --branch-filter ^story\\d+$
```


## Feature branches on Fargate

See `buildspec.yml`
