---
name: "aws-serverless"
displayName: "AWS Serverless Development"
description: "Build and deploy serverless applications with AWS Lambda, SAM, API Gateway, and comprehensive serverless tooling"
keywords: ["serverless", "lambda", "sam", "api gateway", "aws", "deployment", "cloudformation", "event-driven", "microservices", "backend", "web app"]
---

# Onboarding

## Step 1: Validate tools work
Before using AWS Serverless MCP, ensure the following are installed and configured:
- **AWS CLI**: Install and configure with your AWS credentials
  - Verify with: `aws --version` and `aws sts get-caller-identity`
  - **CRITICAL**: If AWS CLI is not configured, DO NOT proceed with serverless setup.
- **AWS SAM CLI**: Install via pip, npm, or package managers
  - Verify with: `sam --version`
- **Docker Desktop**: Required for local testing and container-based builds
  - Verify with: `docker --version`
  - **CRITICAL**: Docker must be running for local Lambda testing.

## Step 2: Add hooks
Add hooks to `.kiro/hooks/` for common serverless workflows:

```json
{
  "enabled": true,
  "name": "Deploy Serverless Application",
  "description": "Build and deploy SAM application to AWS",
  "version": "1",
  "when": {
    "type": "userTriggered"
  },
  "then": {
    "type": "askAgent",
    "prompt": "Build and deploy the SAM application in the current directory using sam_build and sam_deploy tools"
  }
}
```

```json
{
  "enabled": true,
  "name": "Check Application Logs",
  "description": "Retrieve CloudWatch logs for serverless application debugging",
  "version": "1",
  "when": {
    "type": "userTriggered"
  },
  "then": {
    "type": "askAgent",
    "prompt": "Use sam_logs tool to fetch recent logs for troubleshooting"
  }
}
```

# When to Load Steering Files
- Creating new serverless projects → `sam-project-setup.md`
- Building event-driven architectures → `event-source-mappings.md`
- Deploying web applications → `web-app-deployment.md`
- Performance optimization → `serverless-optimization.md`
- Troubleshooting issues → `serverless-troubleshooting.md`

# Best Practices

## Lambda Function Design
- Use appropriate memory allocation (128MB-10GB based on workload)
- Implement proper error handling and retries
- Leverage environment variables for configuration
- Use layers for shared dependencies
- Enable X-Ray tracing for observability

## SAM Template Structure
```yaml
AWSTemplateFormatVersion: '2010-09-09'
Transform: AWS::Serverless-2016-10-31

Globals:
  Function:
    Timeout: 30
    MemorySize: 512
    Runtime: python3.12
    Tracing: Active

Resources:
  MyFunction:
    Type: AWS::Serverless::Function
    Properties:
      CodeUri: src/
      Handler: app.lambda_handler
      Events:
        Api:
          Type: Api
          Properties:
            Path: /hello
            Method: get
```

## Security Considerations
- Use IAM roles with least privilege principles
- Enable CloudTrail for audit logging
- Implement proper input validation
- Use AWS Secrets Manager for sensitive data
- Enable VPC endpoints for private communication

## Performance Optimization
- Right-size Lambda memory allocation
- Use provisioned concurrency for consistent latency
- Implement connection pooling for databases
- Optimize cold start times with smaller deployment packages
- Use appropriate batch sizes for event sources

## Common Patterns

### API Gateway + Lambda
```yaml
ApiGatewayApi:
  Type: AWS::Serverless::Api
  Properties:
    StageName: prod
    Cors:
      AllowMethods: "'GET,POST,PUT,DELETE'"
      AllowHeaders: "'Content-Type,X-Amz-Date,Authorization'"
      AllowOrigin: "'*'"
```

### DynamoDB Integration
```yaml
TodoTable:
  Type: AWS::DynamoDB::Table
  Properties:
    BillingMode: PAY_PER_REQUEST
    AttributeDefinitions:
      - AttributeName: id
        AttributeType: S
    KeySchema:
      - AttributeName: id
        KeyType: HASH
```

### Event Source Mapping
```yaml
MyEventSourceMapping:
  Type: AWS::Lambda::EventSourceMapping
  Properties:
    EventSourceArn: !GetAtt MyKinesisStream.Arn
    FunctionName: !Ref MyFunction
    StartingPosition: LATEST
    BatchSize: 100
```

## Available Tools

This power provides access to comprehensive serverless tooling through the AWS Serverless MCP Server:

### SAM CLI Integration
- `sam_init` - Initialize new serverless projects
- `sam_build` - Build applications for deployment
- `sam_deploy` - Deploy to AWS CloudFormation
- `sam_local_invoke` - Test functions locally
- `sam_logs` - Retrieve CloudWatch logs

### Web Application Tools
- `deploy_webapp` - Deploy full-stack applications
- `configure_domain` - Set up custom domains
- `update_webapp_frontend` - Update frontend assets
- `get_metrics` - Retrieve performance metrics

### Event Source Mapping Tools
- `esm_guidance` - ESM setup and configuration
- `esm_optimize` - Performance optimization
- `esm_kafka_troubleshoot` - Kafka-specific troubleshooting

### Schema & EventBridge Tools
- `search_schema` - Find event schemas
- `describe_schema` - Get schema definitions
- `list_registries` - Browse schema registries

### Guidance Tools
- `get_lambda_guidance` - Lambda use case recommendations
- `get_iac_guidance` - Infrastructure as Code selection
- `get_serverless_templates` - Example templates from Serverless Land
