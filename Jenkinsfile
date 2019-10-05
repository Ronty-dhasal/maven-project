pipeline {
    agent any


    stages 
    {  
        
        stage ('SCM Checkout') {
          git 'https://github.com/prakashk0301/maven-project'
         }
    
    }
    {
                            
        
        stage ('Testing Stage') {


            steps {
                withMaven(maven : 'Local_Maven')
                {
                    sh 'mvn test'
                }
                  }
                                 
        }
		stage ('Package Stage') {
		steps {
		withMaven(maven : 'Local_Maven')
		{
		sh 'mvn package'
		}
		}
		}
		stage ('Install Stage') {


            steps {
                withMaven(maven : 'Local_Maven')
                {
                    sh 'mvn install'
                }
                  }
                                 
        }
		stage ('build && SonarQube analysis') {
            steps {
		withSonarQubeEnv('sonar') {
                    withMaven(maven : 'LocalMaven') {
                        sh 'mvn clean package sonar:sonar'
                    }
		}	
            }
        }		
		
		}
		}
