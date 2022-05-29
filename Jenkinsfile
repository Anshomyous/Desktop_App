pipeline{
    agent any 

    stages{
        stage("Build"){
            steps{
                dir ("demo"){
                    bat 'mvn clean install'
                }
            }
        }
    }
}