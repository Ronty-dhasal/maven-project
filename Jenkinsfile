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
	    
	    stage ('deploy to tomcat') {

steps {
  sshagent (['172.31.33.198']) {
    sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.33.198:/var/lib/tomcat/webapps'
  }
}
		    
		    stage ('Invoke Sonarqube validation') {
		steps {
		withSonarQubeEnv{'sonar'}
		{
		sh 'clean install sonar:sonar'
		}
		}
	    }
	    }
    }
		}
