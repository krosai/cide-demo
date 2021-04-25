pipeline{
agent any 
stages{

stage('Build the application'){
steps {
bat 'mvn clean install'
}
}

stage('Deploy applicatio to cloud hub'){

environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
steps {
bat 'mvn clean package deploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -Dcloudhub.application.name=cicd-demo-app -Denvironment=Sandbox -Dworkers=1 -DworkerType=Micro -Dapp.runtime=4.3.0 -DmuleDeploy'
}
}


}

}