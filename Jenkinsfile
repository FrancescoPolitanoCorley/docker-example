pipeline{
    let myVariable
    parameters {
        string(name: 'NAME', defaultValue: 'My_docker_image')
    }
    agent none
    stages{
        stage ("dependencies"){
            agent { 
                docker {
                    image 'node:alpine' 
                } 
            }
            steps{
             sh ("npm i")
             myVAriable= sh(script: "echo ciao", returnStdout: true)
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