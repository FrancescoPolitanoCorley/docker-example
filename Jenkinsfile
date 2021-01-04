def myVariable=""
pipeline{
    parameters {
        string(name: 'NAME', defaultValue: 'my_docker_image')
    }
    agent none
    stages{
        stage ("dependencies"){
            agent { 
                docker {
                    image 'node:alpine' 
                } 
            }
            environment { 
                MY_SECRET = credentials('9eb2d3ce-c260-4416-a8e7-44c0c1b64c49') 
            }
            steps{
                sh ("npm i")
                script {
                    myVAriable= sh(script: "echo ciao", returnStdout: true)
                }
                sh ("echo $MY_SECRET_PWD")
            }
        }
        stage ("build"){
            agent { 
                label 'master'  
            }
            steps{
             sh ("docker build -t ${params.NAME} .")
             sh "echo $myVAriable"
            }
        }
        stage ("deploy"){
            when{
                tag "release-*"
            }
            agent { 
                label 'master'  
            }
            steps{
             println "sto deployando"
            }
        }
    }
}