@Library('My-Jenkins-SharedLibrary') _ 

pipeline {
   agent any
   
   stages {
       
        stage('EnterUserInput') {
         steps {
             script {
                 
                 def userInputTxt = input(
                                     id: 'inputTextbox', message: 'Please enter JOB Description', parameters: [
                                     [$class: 'TextParameterDefinition', description: 'String or Integer etc..',name: 'input']
                                    ])
                    echo ("JOB Description is: ${userInputTxt}")
                     
             }}   
        }
        
         stage('Upload a CSV') {
         steps {
             script {
                 
                        def inputCSVPath = input message: 'Upload file', parameters: [file(name: 'Test.csv', description: 'Upload only CSV file')]
                        def csvContent = readFile "${inputCSVPath}"
                        
                         echo ("CSV FILE PATH IS : ${inputCSVPath}")
                         echo("CSV CONTENT IS: ${csvContent}") 
        }
                 
                 echo env.STAGE_NAME
                 echo '=========== Upload a CSV =============='
            
            stage{
               steps{
                  script{
                     archiveArtifacts artifacts: '*.csv', onlyIfSuccessful: true
                
                emailext to: "jeevan010202@gmail.com",
                subject: "jenkins build:${currentBuild.currentResult}: ${env.JOB_NAME}",
                body: "${currentBuild.currentResult}: Job ${env.JOB_NAME}\nMore Info can be found here: ${env.BUILD_URL}",
                attachmentsPattern: '*.csv
                     
                
                        
         }
      }
       
   }
  }
