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

원인파악: 
