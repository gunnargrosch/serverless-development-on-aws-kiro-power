---
name: "aws-serverless"
displayName: "AWS Serverless Development"
description: "Build and deploy serverless applications with AWS Lambda, SAM, API Gateway, and comprehensive serverless tooling"
keywords: ["serverless", "lambda", "sam", "api gateway", "aws", "deployment", "cloudformation", "event-driven", "microservices", "backend", "web app"]
author: "Gunnar Grosch"
---

# AWS Serverless Development Power

Accelerate serverless application development with AWS Lambda, SAM, and comprehensive tooling for the entire serverless lifecycle.

## Overview

This power provides AI-assisted serverless development with AWS best practices built-in. It integrates with the [AWS Serverless MCP Server](https://awslabs.github.io/mcp/servers/aws-serverless-mcp-server/) to give you access to the complete serverless development lifecycle.

## When to Use This Power

- Building new serverless applications with AWS Lambda and SAM
- Deploying full-stack web applications to AWS Serverless
- Setting up event-driven architectures with DynamoDB, Kinesis, SQS, or Kafka
- Optimizing Lambda function performance and cost
- Troubleshooting serverless application issues
- Implementing serverless best practices and security patterns
- Managing CloudWatch logs and metrics for serverless apps

## Available MCP Tools

This power provides access to the aws-serverless-mcp-server with comprehensive serverless tooling:

### SAM CLI Integration
- `sam_init` - Initialize new serverless projects with templates
- `sam_build` - Build applications for deployment
- `sam_deploy` - Deploy to AWS CloudFormation
- `sam_local_invoke` - Test functions locally with Docker
- `sam_logs` - Retrieve CloudWatch logs for debugging

### Web Application Deployment
- `deploy_webapp` - Deploy full-stack applications with Lambda Web Adapter
- `configure_domain` - Set up custom domains with Route 53 and ACM
- `update_webapp_frontend` - Update frontend assets with CloudFront invalidation
- `get_metrics` - Retrieve performance metrics from CloudWatch

### Event Source Mapping Tools
- `esm_guidance` - ESM setup and configuration guidance
- `esm_optimize` - Performance optimization for event processing
- `esm_kafka_troubleshoot` - Kafka-specific troubleshooting and resolution

### Schema & EventBridge Tools
- `search_schema` - Find event schemas in AWS registries
- `describe_schema` - Get complete schema definitions for type-safe development
- `list_registries` - Browse available schema registries

### Guidance and Templates
- `get_lambda_guidance` - Lambda use case recommendations and best practices
- `get_iac_guidance` - Infrastructure as Code tool selection guidance
- `get_serverless_templates` - Example SAM templates from Serverless Land
- `get_lambda_event_schemas` - Event schemas for different Lambda event sources

## Getting Started

### Prerequisites Validation
Before using AWS Serverless tools, the power will help validate:
- AWS CLI configuration and credentials
- AWS SAM CLI installation
- Docker Desktop for local testing
- Python 3.10+ with uv package manager

### Quick Start Examples

**Create a new serverless API:**
```
I want to build a serverless REST API for a todo application using Python and AWS Lambda. Help me set up a new SAM project with DynamoDB integration.
```

**Deploy a web application:**
```
I have a React frontend in ./frontend/dist and an Express.js backend in ./backend. Deploy this as a full-stack serverless application on AWS.
```

**Optimize performance:**
```
My Lambda function processing DynamoDB streams is experiencing high iterator age. Help me analyze and optimize the Event Source Mapping configuration.
```

**Troubleshoot issues:**
```
My serverless API is returning 5XX errors intermittently. Help me check the CloudWatch logs and metrics to identify the root cause.
```

## Core Capabilities

### 🚀 Serverless Application Lifecycle
- Project initialization with SAM templates and best practices
- Local development and testing with Docker containers
- Build, package, and deploy to AWS with CloudFormation
- Comprehensive monitoring with CloudWatch logs and metrics

### 🌐 Web Application Deployment
- Full-stack applications with Lambda Web Adapter (no code changes needed)
- Frontend asset management with S3 and CloudFront
- Custom domain configuration with Route 53 DNS and ACM certificates
- Hot-swap frontend updates with cache invalidation

### ⚡ Event-Driven Architecture
- Event Source Mapping configuration for DynamoDB, Kinesis, SQS, Kafka
- Type-safe EventBridge integration with schema registry
- Performance optimization and cost analysis
- Comprehensive troubleshooting for connectivity and performance issues

### 📊 Observability & Security
- CloudWatch integration for logs, metrics, and alarms
- X-Ray tracing for distributed debugging
- IAM roles with least privilege principles
- VPC configurations and security best practices

## Best Practices Included

The power incorporates AWS Well-Architected principles:

- **Security**: IAM least privilege, VPC endpoints, secrets management
- **Performance**: Right-sizing, cold start optimization, connection pooling
- **Cost Optimization**: Provisioned vs on-demand concurrency, lifecycle policies
- **Reliability**: Error handling, retry strategies, dead letter queues
- **Operational Excellence**: Structured logging, monitoring, automation

## Workflow-Specific Guidance

For complex scenarios, the power provides detailed steering files:

- **SAM Project Setup**: Template selection, configuration, and project structure
- **Event Source Mappings**: ESM configuration, optimization, and troubleshooting
- **Web App Deployment**: Full-stack deployment patterns and best practices
- **Performance Optimization**: Memory sizing, concurrency, and cost optimization
- **Troubleshooting**: Systematic approaches to common serverless issues

## Example Workflows

### Initialize and Deploy a Serverless API
1. Use `sam_init` to create a new project with Python runtime
2. Modify the SAM template for your API requirements
3. Use `sam_build` to compile and prepare deployment artifacts
4. Use `sam_deploy` to deploy to AWS with proper IAM capabilities
5. Use `sam_logs` to monitor and debug the deployed application

### Deploy a Full-Stack Web Application
1. Use `deploy_webapp` with fullstack configuration
2. Configure custom domain with `configure_domain`
3. Monitor performance with `get_metrics`
4. Update frontend assets with `update_webapp_frontend`

### Optimize Event Processing
1. Use `esm_guidance` to understand current configuration
2. Use `esm_optimize` to analyze performance trade-offs
3. Apply recommended optimizations for throughput and cost
4. Use `esm_kafka_troubleshoot` for Kafka-specific issues

This power transforms your AI assistant into a serverless expert, handling AWS complexity while you focus on building great applications.
