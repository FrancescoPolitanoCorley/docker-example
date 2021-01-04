pipeline{
    parameters {
        string(name: 'NAME', defaultValue: 'My docker image')
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
            }
        }
        stage ("build"){
            agent { 
                label 'master'  
            }
            steps{
             sh ("docker build -t ${params.NAME} .")
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