pipeline {
    agent {
        label 'AGENT-1'
    }
    options{   //TIMEOUT COUNTER STARTS BEFORE AGENT IS ALLOCATED
        timeout(time: 30, unit: 'SECONDS')
        disableConcurrentBuilds()
        ansiColor("xterm")
    }
    

    environment{
        def appVersion = '' //variable declaration

    }

    stages {
        stage('read the version'){
            steps{
                script{
                    def packageJson = readJSON file: 'package.json'
                    appVersion = packageJson.version
                    echo "application version: $appVersion"
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                sh """
                npm install
                ls -ltr
                echo "application version: $appVersion"

                """
            }
        }
        stage('Build'){
            steps{
                sh """
                zip -q -r backend-${appVersion}.zip * -x Jenkinsfile -x backend-${appVersion}.zip
                ls -ltr
                """
            }
        }
        // stage('Plan') {
        //     steps {
        //         sh 'echo "this is test"'
                
        //     }
        // }
        // stage('Deploy') {
        //     steps {
        //         sh 'echo "this is deploy"'
        //     }
        // }

    }   
        
    post{
        always {
            echo 'I will always say hello again!'
            //deleteDir()
            
        }
        success {
            echo 'I will run when pipeline is success'
        }
        failure {
            echo 'I will run when pipline is failure'
        }
        }    
        }
    

            
            
    
