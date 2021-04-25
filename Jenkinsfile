pipeline{
agent any 
stages{

stage('Build the application'){
steps {
bat 'mvn clean install'
}
}

stage('Deploy applicatio to cloud hub'){
steps {
bat 'mvn clean package deploy -Dusername=cgk1 -Dpassword=Thomas11$ -Dcloudhub.application.name=cicd-demo-app -Denvironment=sandbox -Dworkers=1 -DworkerType=Micro -Dapp.runtime=4.3.0 -DmuleDeploy'
}
}


}

}