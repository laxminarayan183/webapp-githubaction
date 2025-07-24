# Deploying Application Using Github Action

# Requirements
- index.html file
- aws IAM role for S3 Full access
- github action yaml file

# Step 1 : Create a web app Repo
# Step 2 : Go to aws create user using IAM and assign s3 full access
# Step 3 : Go to github action set up workflow yourself
# Step 4 : Create yml file here for access aws

# yml file

```
name: Portfolio Deployment

on:
  push:
    branches:
    - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout
      uses: actions/checkout@v1

    - name: Configure AWS Credentials
      uses: aws-actions/configure-aws-credentials@v1
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: ap-south-1

    - name: Deploy static site to S3 bucket
      run: aws s3 sync . s3://bucket-name --delete
   
 ```
# Step 5 : Setup environment variable for current repo to access aws credentials - settings - secret and varicbles - actions
# Step 6 : Give permission to S3 bucket to public access using bucket policy
# Step 7 : In S3 enable static website hosting
# Step 8 : Copy S3 url and paste in browser to test
