pipeline{
    agent any 

    stages{
        stage("Build"){
            steps{
                dir ("demo"){
                    bat 'mvn -Dmaven.repo.local=C:\Users\sohamr\.m2\repository clean install'
                }
            }
        }
    }
}