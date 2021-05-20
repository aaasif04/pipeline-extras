# Cear-workbench Build and Deploy
Cear-workbench is an built on Ract. This repository contains Jenkins pipeline code and Ansible playbook and inventory  to run npm build and deploy the latest build to the web server.

## Approach

### Build and Deploy
1. Clone the latest code to the Jenkins server
2. Run the build using npm run build:<environemnt>
3. Archive the Build directory and move to Artifactory(s3://lsm-artifactory/dev/)
4. Deploy the latest build into the webroot of the servers

## RollBack
1. Get the just previous build from Artifactory
2. Deploy the build into the webroot of the servers