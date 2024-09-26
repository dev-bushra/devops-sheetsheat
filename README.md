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
in Amplify from: All apps /select-shop-website/ Manage environment variables => Environment Variables
