# Serverless 설정 순서 및 이력 기술

## 설치

### Serverless 설치
```/bin/bash
 $ npm install -g serverless
```

### 프로젝트 생성
```/bin/bash
 $ serverless create --template aws-nodejs --path slack-notifiaction
 
 Serverless: Generating boilerplate...
 Serverless: Generating boilerplate in "/Users/ian/actwo/slack-notifiaction"
   _______                             __
  |   _   .-----.----.--.--.-----.----|  .-----.-----.-----.
  |   |___|  -__|   _|  |  |  -__|   _|  |  -__|__ --|__ --|
  |____   |_____|__|  \___/|_____|__| |__|_____|_____|_____|
  |   |   |             The Serverless Application Framework
  |       |                           serverless.com, v1.32.0
   -------'

  Serverless: Successfully generated boilerplate for template: "aws-nodejs"
```


### 프로파일 사용해서 배포하기(실패)
```
 $ serverless deploy --aws-profile dev
 
 Serverless: Packaging service...
Serverless: Excluding development dependencies...

  Serverless Error ---------------------------------------

  ServerlessError: The request signature we calculated does not match the signature you provided. 
  Check your AWS Secret Access Key and signing method. Consult the service documentation for details.

  Get Support --------------------------------------------
     Docs:          docs.serverless.com
     Bugs:          github.com/serverless/serverless/issues
     Issues:        forum.serverless.com

  Your Environment Information -----------------------------
     OS:                     darwin
     Node Version:           8.12.0
     Serverless Version:     1.32.0
```

### Default profile설정 후(실패)
```
➜  slack-notifiaction serverless deploy --aws-profile dev
Serverless: Packaging service...
Serverless: Excluding development dependencies...

  Serverless Error ---------------------------------------

  ServerlessError: The request signature we calculated does not match the signature you provided. 
  Check your AWS Secret Access Key and signing method. Consult the service documentation for details.

  Get Support --------------------------------------------
     Docs:          docs.serverless.com
     Bugs:          github.com/serverless/serverless/issues
     Issues:        forum.serverless.com

  Your Environment Information -----------------------------
     OS:                     darwin
     Node Version:           8.12.0
     Serverless Version:     1.32.0

➜  slack-notifiaction
```

### Lambda Full Access 적용 후 실패(실패)
```
➜  slack-notifiaction serverless deploy --aws-profile dev -v
Serverless: Packaging service...
Serverless: Excluding development dependencies...
Serverless: Creating Stack...
Serverless: Checking Stack create progress...
CloudFormation - CREATE_IN_PROGRESS - AWS::CloudFormation::Stack - slack-notifiaction-dev
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - ServerlessDeploymentBucket
CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - ServerlessDeploymentBucket
CloudFormation - CREATE_COMPLETE - AWS::S3::Bucket - ServerlessDeploymentBucket
CloudFormation - CREATE_COMPLETE - AWS::CloudFormation::Stack - slack-notifiaction-dev
Serverless: Stack create finished...
Serverless: Uploading CloudFormation file to S3...
Serverless: Uploading artifacts...
Serverless: Uploading service .zip file to S3 (387 B)...
Serverless: Validating template...
Serverless: Updating Stack...
Serverless: Checking Stack update progress...
CloudFormation - UPDATE_IN_PROGRESS - AWS::CloudFormation::Stack - slack-notifiaction-dev
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - HelloLogGroup
CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - HelloLogGroup
CloudFormation - CREATE_FAILED - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - CREATE_COMPLETE - AWS::Logs::LogGroup - HelloLogGroup
CloudFormation - UPDATE_ROLLBACK_IN_PROGRESS - AWS::CloudFormation::Stack - slack-notifiaction-dev
CloudFormation - UPDATE_ROLLBACK_COMPLETE_CLEANUP_IN_PROGRESS - AWS::CloudFormation::Stack - slack-notifiaction-dev
CloudFormation - DELETE_IN_PROGRESS - AWS::Logs::LogGroup - HelloLogGroup
CloudFormation - DELETE_COMPLETE - AWS::IAM::Role - IamRoleLambdaExecution
CloudFormation - DELETE_COMPLETE - AWS::Logs::LogGroup - HelloLogGroup
CloudFormation - UPDATE_ROLLBACK_COMPLETE - AWS::CloudFormation::Stack - slack-notifiaction-dev
Serverless: Operation failed!

  Serverless Error ---------------------------------------

  An error occurred: IamRoleLambdaExecution - API: iam:CreateRole User: arn:aws:iam::905136931838:user/devops-cli is not authorized to perform: iam:CreateRole on resource: arn:aws:iam::905136931838:role/slack-notifiaction-dev-ap-northeast-2-lambdaRole.

  Get Support --------------------------------------------
     Docs:          docs.serverless.com
     Bugs:          github.com/serverless/serverless/issues
     Issues:        forum.serverless.com

  Your Environment Information -----------------------------
     OS:                     darwin
     Node Version:           8.12.0
     Serverless Version:     1.32.0
```

# Link
[Iam Policy in Serverless Framework](https://serverless-stack.com/chapters/customize-the-serverless-iam-policy.html)
