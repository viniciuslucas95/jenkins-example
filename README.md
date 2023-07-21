# Jenkins Example

## Setup

##### 1. Start the containers with "docker-compose up -d"
##### 2. Access jenkins dashboard at localhost:8080
##### 3. Get jenkins admin password (with "cat jenkins_home/secrets/initialAdminPassword") and log into the dashboard
##### 4. Install the suggested plugins
##### 5. Skip the admin account configuration, specify jenkins url and finish the configuration
##### 6. Install .NET SDK Support plugin and enable it in Jenkins tools with the name "dotnet"
##### 7. Create a pipeline and in the pipeline section, set the definition to "Pipeline script from SCM" and configure it to match this github repository info. You can also add a periodic SCM consult, to check from time to time for a new update in the repository
