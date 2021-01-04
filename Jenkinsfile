pipeline{
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
             sh ("docker build .")
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