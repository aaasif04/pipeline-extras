# General Info
This is the AWS CI/CD pipeline files for sds-qa-airflow

# Code Build
## Project Configuration
        - Enter the project name in "Project name" field.
        - Give a Description to brief the project
        - Keep the rest of the configurations as default
  
## Source
        - Source files are taken from AWS CodeCommit
        - We have 2 sources for airflow
### Source 1 - Primary
            > - Set "Source provider" as "AWS CodeCommit"
            > - Set "Repository" to <source repository name>. Here it is "sds-orchestration"
            > - Choose "Reference type" as "Branch", since we are taking source version reference type that contains the source code as git branch
            > - Choose the branch name of the source repository
            > - Keep the rest of the configurations as default
### Source 2
            - Specify the "Source identifier" for Source 2 as "sdsconfig"
            - Set "Source provider" as "AWS CodeCommit"
            - Set "Repository" to <source repository name>. Here it is "sds-config"
            - Choose "Reference type" as "Branch", since we are taking source version reference type that contains your source code as git branch
            - Choose the branch name of the source repository
            - Keep the rest of the configurations as default
        - Keep the rest of the configurations as default
  
## Environment
        - Choose the "Operating system". Here it is "Amazon Linux 2"
        - Select the "Runtime(s)" as "Standard"
        - Select the "Image" as "aws/codebuild/amazonlinux2-x86_64-standard:2.0"
        - Keep the rest of the configurations as default
  
## Buildspec
        - We are using a buildspec file for build
        - Give the buildspec file location. Here it is "devops/aws-code-pipeline/buildspec.yml"
  
## Batch Configuration
        - Keep the configurations as default
  
## Artifacts
        - AWS S3 is used as Artifact
        - Needs only 1 Artifact
        - Choose Type as "Amazon S3"
        - Give the Bucket Name
        - "Enable semantic versioning" should be checked for each Artifact to use the artifact name specified in the **buildspec file**
        - "Path - optional" is set to "codebuild-orchestration", which specifies a path to store the file in S3 Artifact
        - "Artifacts packaging" is set to "Zip", which specifies that aws codebuild will upload artifacts into a compressed file that is put into the specified bucket
        - Keep the rest of the configurations as default
  
## Logs
        - Set the Group name as "codebuild-sds-qa-orchestration"
        - Keep the rest of the configurations as default

# Code Deploy
## Applications
        - Create an application. Here application name is "sds-qa-orchestration"
        - Select the Compute platform as "EC2/On-premises"
  
## Deployment Group
        **Environment configuration**
            - Check "Amazon EC2 instances"
            - Select the instances to which the deployment must be targeted
  
## Deployments
        **Revision details**
            - Revision location is of the form S3://<artifact-bucket-name>/codebuild-orchestration/sds-qa-airflow.zip
            - Select Revision file type as ".zip"
  
## Appspec
        - appspec file should be placed in the root directory
        **Before Install**
            - Take an archived backup of installed airflow and store it in backup location
            - Remove the older backup files from backup location if more than 10 backup are available
            - Stop the running airflow services
            - Remove the replacing files and directories
                - /opt/airflow/dags
                - /opt/airflow/logconfig
                - /opt/airflow/plugins
                - /opt/airflow/airflow.cfg
                - /opt/airflow/variable.json
                - /opt/airflow/requirements.txt

## After Install
            - Source the airflow venv
            - Change to root directory of airflow
            - pip install -r requirements.txt
            - airflow variables -i variable.json
            - deactivate from airflow venv
            - Change the ownership of files to airflow user