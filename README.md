# devops_challenge
Endava devops Challenge


# Devops Challenge - AWS Automation

Automate the following tasks with your own choice of scripting language

## Automated ECS deployments

## Core components

### AWS

The AWS infrastructure is setup using terraform in the [`./terraform`](./terraform).

The following components are deployed:

- Application Load Balancer ([`./lb.tf`](./terraform/lb.tf))
- ECS Cluster / ECS Service ([`./ecs.tf`](./terraform/ecs.tf))
- Elastic Container Registry ([`./ecr.tf`](./terraform/ecr.tf))
- IAM permissions ([`./iam.tf`](./terraform/iam.tf))
- VPC configuration ([`./vpc.tf`](./terraform/vpc.tf))

### CI/CD

The repository leverages the [AWS Github Actions](https://github.com/aws-actions/)
maintained by AWS.

The main goal is to provide an example configuration of the following workflow:

- Run the integration tests
- Build the Docker image
- Publish it to a private ECR
- Update the corresponding ECS Service (by editing the task image)

[ci-success]:

### Task 1

Automate the Build of a nginx application.

1. We have an app folder and inside it a file that has a simple index.html hello world
2. Create a Dockerfile
3. Start the github actions (CICD)


### Task 2

Create the terraform code to build the infraestructure

Automate the process of to create the infraestructure to deploy the service

1. Create the VPC/Subnets
2  Build ECR
3. Create the ECS cluster
4. Add the CICD to build this


For example:

```
resource "aws_ecs_cluster" "cluster" {
  name = "nafis-ecs-cluster"

  capacity_providers = ["FARGATE_SPOT", "FARGATE"]

  default_capacity_provider_strategy {
    capacity_provider = "FARGATE_SPOT"
  }

  setting {
    name  = "containerInsights"
    value = "disabled"
  }
}

```

### Task 3

Lets Automate the previuos step!

Now lets do some changes and redeploy!

### Task 4

How to deploy the same code to different environmets?

1. Deployment strategy
2. Docker tagging
3. Manual approvals?

### **Bonus Task**

Once you have the basic functionality implemented, try to do the following bonus exercises:

1. Write a cloudwatch alert with the following parameters:

   CPU utilization > 80%

   CPU Utilization < 60%


 
