pipeline{
    agent {
        docker{
            image "node:alpine"
        }
    }
    stages{
        stage ("say hello"){
            steps{
             sh ("npm --v")
            }
        }
    }
}