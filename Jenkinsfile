pipeline{

    agent any

    stages{
        stage('Clone Project'){

            steps{
                git branch: 'feature/2026.02.18', url: 'https://github.com/srinfotechbatch5/Petclinic.git'
            }
        }
        stage('Build'){

            steps{

                bat 'mvn clean install'
            }
        }

        stage('Test'){

            steps{

                bat 'mvn test'
            }
        }

        stage('Package'){

            steps{

                bat 'mvn package'
            }
        }

        stage('Generated the Tets Results'){

            steps{

                junit 'target/surefire-reports/*.xml'
            }
        }

        stage('Generated Artifacts'){

            steps{

                archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }

        stage('Deploy'){

            steps{

                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'TomcatCredentialsNew', path: '', url: 'http://localhost:8080/')], contextPath: 'PetRegistration', war: 'target/*.war'
            }
        }
    }
}