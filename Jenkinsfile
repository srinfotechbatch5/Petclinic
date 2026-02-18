pipeline{
    
    
    stages{
        
        stage('clone'){
            
            steps{
                git branch: 'feature/2026.02.18', url: 'https://github.com/srinfotechbatch5/Petclinic.git'
                
            }
        }
        stage('Build'){
            
            steps{
             bat 'mvn install'
                
            }
        }

        stage('Test'){
            
            steps{
             bat 'mvn test'
                
            }
        }
		
		stage('Published  the Test Results'){
            
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
          
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'TomcatCredentials', path: '', url: 'http://localhost:8080/')], contextPath: 'SRINFOETCHSpringPetclinicApplication', war: 'target/*.war'
            }
        }
    }
}
