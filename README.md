# Jenkins Pipeline
This project includes a Jenkins pipeline defined in the Jenkinsfile. The pipeline performs the following steps:

## Setting Up Jenkins

To run this project using Jenkins, follow these steps:
### 1. Install Jenkins using docker compose : 
Clone this repo :

``` sh
git clone https://github.com/fal7w/automation.git
cd automation/docker-compose/Jenkins/
```

### 2. Create a New Job:
After install `Jenkins` do this :
      - Open Jenkins in your web browser.
      - Click on "New Item".
      - Enter a name for your job and select "Pipeline", then click "OK".

### 3. Configure the Pipeline:

   - In the job configuration page, go to the "Pipeline" section.
   - Select "Pipeline script from SCM".
   - Choose "Git" as the SCM.
   - Enter the repository URL: `https://github.com/fal7w/jenkins-pipline.git`.
   - Set the branch to build (e.g., `main`).
   - Ensure the Jenkinsfile path is `Jenkinsfile`.

### 4. Save and Build:
   - Save the job configuration.
   - Click "Build Now" to start the pipeline.


## Project Structure

my-nodejs-project/
├── tests/

│   └── server.test.js

├── .gitignore

├── Jenkinsfile

├── README.md

├── package.json

├── server.js
