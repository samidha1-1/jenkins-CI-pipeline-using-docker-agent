# Jenkins CI pipeline using docker as agent 

## Project Overview 
This project demonstrates how to use **Docker agent in jenkins pipeline** to run in an isolated an 
consistent environment .Each jenkins build run inside a docker container , ensuring dependencies consistency and clean environment. 

## Technologies used 
- Jenkins 
- Docker
- Github 
- Python

## Key learnings 
- Install jenkins and docker on your system
- Create a new jenkins pipeline job
- Conne ct your guthub repoaitory with SCM (Source code management)
- Add the jenkinsfile
- Run the pipeline 

## Error encountered and resolution 
- Issue : During pipeline execution, the build failed with the following error:
 python: can't open file '/var/lib/jenkins/workspace/my-pipeline/app.py':
[Errno 2] No such file or directory

- Root cause
 Jenkins executes pipeline steps from the workspace root directory.
 However, the application file app.py was located inside a subdirectory:
 docker-agent-demo/app.py
 Since Jenkins was not automatically navigating into this folder, the file could not be found.

- Solution
 So i used dir() in my jenkinsfile to change into the current directory before exceuting the scripts .
dir('docker-agent-demo') {
    sh 'python app.py'
}
 
