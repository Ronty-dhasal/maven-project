pipeline
{

agent any


stages
{

stage ('scm checkout'){
git 'https://github.com/Ronty-dhasal/maven-project.git'


}
}
{

stage ('Test Stage') {




steps {
	withMaven(maven: 'LocalMaven') 
{
 sh 'mvn test'

}

}

}

}
}
