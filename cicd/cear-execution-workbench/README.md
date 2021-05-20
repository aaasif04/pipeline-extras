# Cear-Work bench Build and Deploy

Cear work bench is a Scala job which will be run via AWS Glue. Since AWS Glue is a server les service the jar file will be accessed from an S3 bucket.

## Approach
### Build and Deploy
1. Get the code from development branch\
2. Build the jar file\
3. Move the code to artifactory(s3://lsm-artifactory/dev/)\
4. deploy the the latest jar file from artifactory to the S3.\


### RollBack
1. Get the just previous build from Artifactory
2. Deploy the same to the the S3 

