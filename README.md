### DevOps & CLoud Sheetsheat

### AWS
# AWS Amplify yml deployment (amplify.yml):
version: 1
frontend:
  phases:
    preBuild:
      commands:
        - npm ci --cache .npm --prefer-offline
    build:
      commands:
        - npm run build
  artifacts:
    baseDirectory: dist
    files:
      - '**/*'
  cache:
    paths:
      - .npm/**/*

# Environment Variables (.env):
1. in GitHub from: Repo > setting > Secrets and variables > Actions > Actions secrets and variables.
2. in AWS Amplify from: All apps > select-shop-website > Manage environment variables => Environment Variables
3. in AWS ECS (Elastic Container Service) from: Amazon Elastic Container Service > Task definitions > projectname-backend-td > Revision 61 > Create revision => search for Container-1 then Environment variables 
4. in AWS ECR (Elastic Container Registry from: Amazon ECR > Private registry > Repositories > backend

# Key Insights in each Workflow:
1. ECR (Elastic Container Registry): Your application’s Docker image is built and pushed to ECR.
2. ECS (Elastic Container Service): The workflow deploys the Docker image from ECR to an ECS service defined by projectname-backend-service in the main cluster.
3. Docker: The application is packaged in a Docker container, which ECS manages.

### Aurora Database
From RDS > Databases you can create or manage your database
from Database table you will found DB identifier so from there you can add main and main-instance-1 and from RDS > Databases > main > main-instance-1 in the Connectivity & Security you can copy the Endpoint & port witch you will use in you .env file to connect with this DB instance you just create:

// Endpoint & port
Endpoint: main-instance-1.cl8yaii468na.us-east-1.rds.amazonaws.com
Port: 3306

// .env
DATABASE_URL=mysql://admin:Admin@123@main-instance-1.cl5rodii468na.us-east-1.rds.amazonaws.com/erp
DATABASE_URL=mysql://root:123456@localhost:3306/erp


