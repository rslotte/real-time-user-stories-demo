# Demo


This repository contains the code used to demo building feature branches from Github with AWS Codebuild and deploying onto AWS Fargate.


## Codebuild Project


To create the Codebuild project:
```
$ aws cloudformation create-stack --stack-name branch-deploy --template-body file://codebuild.yml --parameters \
ParameterKey=ProjectName,ParameterValue=branch-deploy \
ParameterKey=RepositoryLocation,ParameterValue=https://github.com/rslotte/codebuild-demo.git \
--capabilities CAPABILITY_NAMED_IAM
```


Modify the trigger if you only want to build on a specific branch naming pattern:
```
$ aws codebuild update-webhook --project-name branch-deploy --branch-filter ^feature\\d+$
```


## Feature branches on Fargate

See `buildspec.yml`
