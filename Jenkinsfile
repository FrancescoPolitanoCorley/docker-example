@Library('MyLibrary') _
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
                    println("il mio valore è decisamente: ${returnZero()}")
                    myLibrary.printHello pluto: "Francesco", pippo: "ciao"
                }
                sh ("echo $MY_SECRET_PSW > my_secret.txt")
                sh ("cat my_secret.txt")

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
int returnZero(){
    return 0
}