---
name: "aws-serverless"
displayName: "AWS Serverless Development"
description: "Build and deploy serverless applications with AWS Lambda, SAM, API Gateway, and comprehensive serverless tooling"
keywords: ["serverless", "lambda", "sam", "api gateway", "aws", "deployment", "cloudformation", "event-driven", "microservices", "backend", "web app"]
author: "Gunnar Grosch"
---

# Overview

The AWS Serverless Development Power provides comprehensive access to AWS serverless development tools and best practices. Build, deploy, and manage serverless applications with AWS Lambda, SAM, API Gateway, and the complete AWS serverless ecosystem.

**Key capabilities:**
- **SAM CLI Integration**: Initialize, build, deploy, and test serverless applications
- **Web Application Deployment**: Deploy full-stack applications with Lambda Web Adapter
- **Event Source Mappings**: Configure and optimize Lambda triggers for DynamoDB, Kinesis, SQS, Kafka
- **Schema Management**: Type-safe EventBridge integration with schema registry
- **Observability**: CloudWatch logs, metrics, and X-Ray tracing
- **Performance Optimization**: Right-sizing, cost optimization, and troubleshooting

**Authentication**: Requires AWS CLI configured with credentials and AWS SAM CLI installed.

## Available MCP Servers

### aws-serverless-mcp

**Package:** `awslabs.aws-serverless-mcp-server`
**Connection:** Local MCP server via uvx
**Tools:**

1. **sam_init** - Initialize serverless applications using AWS SAM CLI
   - Required: `project_name` (string) - Name of the SAM project
   - Required: `runtime` (string) - Runtime environment (python3.12, nodejs22.x, etc.)
   - Required: `project_directory` (string) - Absolute path for project creation
   - Required: `dependency_manager` (string) - Dependency manager (pip, npm, etc.)
   - Optional: `architecture` (string) - x86_64 or arm64 (default: x86_64)
   - Optional: `application_template` (string) - Template type (default: hello-world)
   - Returns: New SAM project with infrastructure and code templates

2. **sam_build** - Build serverless applications for deployment
   - Required: `project_directory` (string) - Absolute path to SAM project
   - Optional: `use_container` (boolean) - Use Docker for builds (default: false)
   - Optional: `parallel` (boolean) - Parallel builds (default: true)
   - Returns: Built artifacts ready for deployment

3. **sam_deploy** - Deploy serverless applications to AWS
   - Required: `application_name` (string) - Name of the application
   - Required: `project_directory` (string) - Absolute path to SAM project
   - Optional: `region` (string) - AWS region for deployment
   - Optional: `capabilities` (array) - IAM capabilities (default: ["CAPABILITY_IAM"])
   - Returns: Deployed CloudFormation stack with resources

4. **sam_local_invoke** - Test Lambda functions locally
   - Required: `project_directory` (string) - Absolute path to SAM project
   - Required: `resource_name` (string) - Lambda function name to invoke
   - Optional: `event_file` (string) - Path to JSON event file
   - Optional: `event_data` (string) - JSON event data
   - Returns: Local function execution results and logs

5. **sam_logs** - Retrieve CloudWatch logs for debugging
   - Optional: `resource_name` (string) - Resource to fetch logs for
   - Optional: `stack_name` (string) - CloudFormation stack name
   - Optional: `start_time` (string) - Start time (e.g., "5mins ago")
   - Optional: `end_time` (string) - End time (e.g., "now")
   - Returns: CloudWatch logs for serverless resources

6. **deploy_webapp** - Deploy web applications to AWS Serverless
   - Required: `deployment_type` (string) - backend, frontend, or fullstack
   - Required: `project_name` (string) - Project name
   - Required: `project_root` (string) - Absolute path to project root
   - Optional: `region` (string) - AWS region
   - Optional: `backend_configuration` (object) - Backend settings
   - Optional: `frontend_configuration` (object) - Frontend settings
   - Returns: Deployed web application with Lambda and CloudFront

7. **configure_domain** - Set up custom domains for web applications
   - Required: `project_name` (string) - Project name
   - Required: `domain_name` (string) - Custom domain name
   - Optional: `create_certificate` (boolean) - Create ACM certificate (default: true)
   - Optional: `create_route53_record` (boolean) - Create DNS record (default: true)
   - Returns: Configured custom domain with SSL certificate

8. **update_webapp_frontend** - Update frontend assets
   - Required: `project_name` (string) - Project name
   - Required: `project_root` (string) - Project root path
   - Required: `built_assets_path` (string) - Path to built frontend assets
   - Optional: `invalidate_cache` (boolean) - Invalidate CloudFront cache (default: true)
   - Returns: Updated frontend with cache invalidation

9. **get_metrics** - Retrieve CloudWatch metrics
   - Required: `project_name` (string) - Project name
   - Optional: `start_time` (string) - Start time (ISO format)
   - Optional: `end_time` (string) - End time (ISO format)
   - Optional: `resources` (array) - Resources to monitor (default: ["lambda", "apiGateway"])
   - Returns: Performance metrics and monitoring data

10. **esm_guidance** - Event Source Mapping setup and configuration
    - Optional: `event_source` (string) - dynamodb, kinesis, kafka, sqs, unspecified
    - Optional: `guidance_type` (string) - setup, networking, troubleshooting
    - Returns: Step-by-step ESM configuration guidance

11. **esm_optimize** - Optimize Event Source Mapping performance
    - Optional: `action` (string) - analyze, validate, generate_template
    - Optional: `optimization_targets` (array) - failure_rate, latency, throughput, cost
    - Optional: `event_source` (string) - Event source type for validation
    - Returns: Performance optimization recommendations

12. **esm_kafka_troubleshoot** - Troubleshoot Kafka ESM issues
    - Optional: `kafka_type` (string) - msk, self-managed, auto-detect
    - Optional: `issue_type` (string) - diagnosis or specific issue type
    - Returns: Kafka troubleshooting guidance and solutions

13. **search_schema** - Search EventBridge schemas
    - Required: `keywords` (string) - Search keywords
    - Required: `registry_name` (string) - Registry to search (use "aws.events")
    - Optional: `limit` (number) - Max results (1-100)
    - Returns: Matching event schemas

14. **describe_schema** - Get complete schema definitions
    - Required: `registry_name` (string) - Registry name
    - Required: `schema_name` (string) - Schema name
    - Optional: `schema_version` (string) - Version (latest by default)
    - Returns: Complete schema definition for type-safe development

15. **list_registries** - Browse schema registries
    - Optional: `scope` (string) - LOCAL or AWS
    - Optional: `limit` (number) - Max results
    - Returns: Available schema registries

16. **get_lambda_guidance** - Lambda platform suitability guidance
    - Required: `use_case` (string) - Description of use case
    - Optional: `include_examples` (boolean) - Include examples (default: true)
    - Returns: Lambda suitability analysis and recommendations

17. **get_iac_guidance** - Infrastructure as Code tool selection
    - Optional: `iac_tool` (string) - CloudFormation, SAM, CDK, Terraform
    - Optional: `include_examples` (boolean) - Include examples (default: true)
    - Returns: IaC tool selection guidance

18. **get_serverless_templates** - Example SAM templates
    - Required: `template_type` (string) - API, ETL, Web, etc.
    - Optional: `runtime` (string) - Lambda runtime
    - Returns: Example templates from Serverless Land

19. **get_lambda_event_schemas** - Lambda event schemas
    - Required: `event_source` (string) - api-gw, s3, sqs, sns, kinesis, dynamodb
    - Required: `runtime` (string) - go, nodejs, python, java
    - Returns: Event schema definitions for Lambda handlers

## Tool Usage Examples

### Initialize and Deploy a Serverless API

**Create new SAM project:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "sam_init", {
  "project_name": "todo-api",
  "runtime": "python3.12",
  "project_directory": "/path/to/projects",
  "dependency_manager": "pip",
  "application_template": "hello-world"
})
```

**Build the application:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "sam_build", {
  "project_directory": "/path/to/projects/todo-api"
})
```

**Deploy to AWS:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "sam_deploy", {
  "application_name": "todo-api",
  "project_directory": "/path/to/projects/todo-api",
  "region": "us-east-1"
})
```

### Deploy Full-Stack Web Application

**Deploy complete application:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "deploy_webapp", {
  "deployment_type": "fullstack",
  "project_name": "my-web-app",
  "project_root": "/path/to/web-app",
  "backend_configuration": {
    "runtime": "nodejs22.x",
    "port": 3000,
    "entry_point": "src/app.js"
  },
  "frontend_configuration": {
    "built_assets_path": "./dist"
  }
})
```

**Configure custom domain:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "configure_domain", {
  "project_name": "my-web-app",
  "domain_name": "myapp.example.com"
})
```

### Event Source Mapping Setup

**Get ESM guidance:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "esm_guidance", {
  "event_source": "dynamodb",
  "guidance_type": "setup"
})
```

**Optimize performance:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "esm_optimize", {
  "action": "analyze",
  "optimization_targets": ["throughput", "cost"],
  "event_source": "kinesis"
})
```

### Schema Management

**Search for S3 event schemas:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "search_schema", {
  "keywords": "aws.s3",
  "registry_name": "aws.events"
})
```

**Get complete schema definition:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "describe_schema", {
  "registry_name": "aws.events",
  "schema_name": "aws.s3@ObjectCreated"
})
```

### Monitoring and Debugging

**Get application metrics:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "get_metrics", {
  "project_name": "todo-api",
  "start_time": "2024-01-01T00:00:00Z",
  "end_time": "2024-01-01T23:59:59Z",
  "resources": ["lambda", "apiGateway"]
})
```

**Retrieve CloudWatch logs:**
```javascript
usePower("aws-serverless", "aws-serverless-mcp", "sam_logs", {
  "stack_name": "todo-api",
  "start_time": "1hour ago",
  "end_time": "now"
})
```

## Configuration

**Prerequisites:**
1. **AWS CLI**: Install and configure with credentials
2. **AWS SAM CLI**: Install via pip, npm, or package managers  
3. **Docker Desktop**: Required for local testing
4. **Python 3.10+**: With uv package manager

**Setup Steps:**
1. **Configure AWS Credentials:**
   ```bash
   aws configure
   # or use AWS SSO, environment variables, or IAM roles
   ```

2. **Install SAM CLI:**
   ```bash
   pip install aws-sam-cli
   # or via npm, homebrew, etc.
   ```

3. **Configure in mcp.json:**
   ```json
   {
     "mcpServers": {
       "aws-serverless-mcp": {
         "command": "uvx",
         "args": [
           "awslabs.aws-serverless-mcp-server@latest",
           "--allow-write",
           "--allow-sensitive-data-access"
         ],
         "env": {
           "AWS_PROFILE": "default",
           "AWS_REGION": "us-east-1"
         }
       }
     }
   }
   ```

## Best Practices

### ✅ Do:
- **Start with SAM templates** for consistent project structure
- **Use least privilege IAM roles** for Lambda functions
- **Enable X-Ray tracing** for distributed debugging
- **Implement proper error handling** and retry strategies
- **Monitor CloudWatch metrics** for performance insights
- **Use environment variables** for configuration
- **Test locally first** with sam_local_invoke
- **Right-size Lambda memory** based on workload
- **Use provisioned concurrency** for latency-sensitive functions
- **Implement structured logging** for better observability

### ❌ Don't:
- **Hardcode credentials** in Lambda functions
- **Use overly large deployment packages** (impacts cold starts)
- **Ignore CloudWatch alarms** and monitoring
- **Deploy without testing** locally first
- **Use default timeouts** without consideration
- **Forget to clean up** unused resources
- **Skip security reviews** of IAM policies
- **Use synchronous calls** for long-running processes
- **Ignore cost optimization** opportunities
- **Deploy to production** without proper CI/CD

---

**Package:** `awslabs.aws-serverless-mcp-server`
**Source:** AWS Labs
**License:** Apache 2.0
**Connection:** Local MCP server with AWS credentials
