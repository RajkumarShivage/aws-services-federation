
# Account Federation

API Gateway and Lambda Function to manage AWS Account Federation

![aws-services][aws-services-image]

## How to Execute API Gateway Interface

Path
```
/federation?federateAccount=<federate_account_num>&federateRoleName=<federate_role_name>&account=<target_account_num>&roleName=<target_account_role_name>
```

Headers
```
roleExternalId:<externl_id_of_target_account_to_federate>
```

Return Value
```
{"statusCode":200,"body":{"ResponseMetadata":{"RequestId":""},"Credentials":{"AccessKeyId":"","SecretAccessKey":"","SessionToken":"","Expiration":""},"AssumedRoleUser":{"AssumedRoleId":"","Arn":""}}}
```

## How To Setup a CodePipeline

- First, create a S3 Bucket where the deployment files will be uploaded with below naming convention. *(You can use a different convention, but you need to add a permission for the CodeBuild to access this S3 bucket)*.

  >

      codepipeline-<region>-<account_num>-<project_name>

  like

      codepipeline-us-east-1-9999999999-aws-services-federation


- Follow the steps in http://docs.aws.amazon.com/lambda/latest/dg/automating-deployment.html along with an additional step to set environment variables under 'Advanced' setting when creating a new project in CodeBuild

  > S3_BUCKET_NAME : S3 bucket name you created above

  > AWS_DEFAULT_REGION : AWS region where this project is deployed

  > AWS_ACCOUNT_ID : AWS Account Number where this project is deployed


## How To Test Lambda Function

After populating the const variables in test.js, run below command

    $ node tests/test.js

## [![Sungard Availability Services | Labs][labs-logo]][labs-github-url]

This project is maintained by the Labs group at [Sungard Availability
Services](http://sungardas.com)

GitHub: [https://sungardas.github.io](https://sungardas.github.io)

Blog:
[http://blog.sungardas.com/CTOLabs/](http://blog.sungardas.com/CTOLabs/)

[labs-github-url]: https://sungardas.github.io
[labs-logo]: https://raw.githubusercontent.com/SungardAS/repo-assets/master/images/logos/sungardas-labs-logo-small.png
[aws-services-image]: ./docs/images/logo.png?raw=true
