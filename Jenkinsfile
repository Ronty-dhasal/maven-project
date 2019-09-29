pipeline
{

agent any
{


stage "scm checkout" {
git 'https://github.com/Ronty-dhasal/maven-project.git'


}

stage "code test" {
withMaven(maven: 'LocalMaven') {
 sh 'mvn test'

}

}

}

}
