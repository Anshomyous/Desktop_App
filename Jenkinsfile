pipeline{
    agent any 

    stages{
        stage("Pre-Build Notification"){
            steps{
                echo "WILL CODE SOON"
            }
            
        }
        stage("Static Code Analysis"){
            steps{
                withSonarQubeEnv(credentialsId: 'Sonarcloud-Jenkins') {
                  bat  'mvn verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=Anshomyous_Desktop_App'
                }
            }
        }
        stage("Build"){
            steps{
                dir ("demo"){
                    bat 'mvn -Dmaven.repo.local=C:\\Users\\sohamr\\.m2\\repository clean install'
                }
            }
            post{
                always{
                    bat 'copy demo\\target\\myapp.exe msix_files\\VFS\\ProgramFilesX86\\MyApp /y'
                }
            }
        }
		stage("App Packaging"){
            steps{
                bat '''
                    "C:\\Program Files (x86)\\VB6VirtualRegistry\\Vb6VirtualRegistry.exe"  pack "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Manual MSIX Packaging\\msix_files" "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\Manual MSIX Packaging\\myapp.msix"
                    '''
            }
        }
        stage("Archving artifacts"){
            steps{
                archiveArtifacts artifacts: '*.msix', followSymlinks: false
                archiveArtifacts artifacts: 'demo\\target\\*.exe', followSymlinks: false
            }
        }
        stage("Post-Build Notification"){
            steps{
                //Code here
                echo 'CODE IS COMING SOON'
            }
        }
		
    }
}