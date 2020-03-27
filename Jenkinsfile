import groovy.json.*

node () {
   def mvnHome, commitId
    
   stage('Checkout code from GitHub') { // for display purposes
      checkout scm
   }
   
   stage('Scan with Tidelift') {
      //sh "tidelift scan --team teamname --repo reponame --wait"
      sleep 5 //for demo only
   }
   
   stage('Build - compile source code into machine code') {
      sh "./mvnw  -B -Dmaven.test.failure.ignore clean package"
   }
   
   stage('Bake application into a Docker image') {
      //sh "docker build ..."
      sleep 5 //for demo only
   }
   
   stage('Deploy Docker image to a test environment') {
      //sh "docker run ..."
      sleep 5 //for demo only
   }
   
   stage('Run automated tests') {
      //sh .....
      sleep 5 //for demo only
   }
   stage('Deploy to production') {
      
   }
   
}

def postGitHub(commitId, state, context, description, target_url="http://localhost:8080") {
         def payload = JsonOutput.toJson(
           state: state,
           context: context,
           description: description,
           target_url: target_url
          )
        sh "curl -H \"Authorization: token ${gitHubApiToken}\" --request POST --data '${payload}' https://api.github.com/repos/${project}/statuses/${commitId}"
}
  

