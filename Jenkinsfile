#!/usr/bin/env groovy

@Library('jenkins_shared_library')_

pipeline{
    agent any

 stages {
     
     	stage('create-project') 
      {
            steps {
                
              createProjectTesting()
            }
        }
        	stage('create-repo') 
      {
            steps {
                
              createRepoTesting()
            }
        }
        
        
        stage('code-push')
        {
            steps{
                
                sh label: '', script: '''rm -rf ./* && git clone https://github.com/amanchourasia/JenkinsWar.git
                git clone http://rig:${rig_password}@18.224.68.30:7990/scm/DEM/web_1.git
                cp -r ./JenkinsWar/* ./web_1
                cd web_1
                git init
                git add --all
                git commit -m"initial commit"
                git push -u origin master'''
            }
        }
         stage('create-DEV') 
      {
            steps {
                
              createDevBranchTesting()
            }
      }
        
         stage('create-QA') 
      {
            steps {
                
              createQABranchTesting()
            }
       }
        
 }
}
