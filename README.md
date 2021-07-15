# dynamosize

AWS DynamoDB table sizes aren't reported to CloudWatch. This fixes that. Metrics
are published hourly to the `dynamosize` namespace.

### Deployment

You have two options. The first is deploying the following CloudFormation template:

```yaml
Transform: AWS::Serverless-2016-10-31

Resources:
  App:
    Type: AWS::Serverless::Application
    Properties:
      Location:
        ApplicationId: arn:aws:serverlessrepo:us-east-1:607481581596:applications/dynamosize
        SemanticVersion: 0.1.0
```

The second option is clicking [this link][console] to open the AWS web console,
then click the _Deploy_ button. 

[console]: https://console.aws.amazon.com/lambda/home?region=us-east-1#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:607481581596:applications/dynamosize

I personally deploy the above CloudFormation template to all accounts and regions
in my AWS org using service-managed CloudFormation stack sets. For that you need 
to deploy `stackset.yml`.
