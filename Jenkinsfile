pipeline{
agent any 
stages{

stage('Build the application'){
steps {
bat 'mvn clean install'
}
}

stage('Packaging to nexus'){
steps {
bat 'mvn clean package deploy -U -Dmaven.test.skip=true -s C:\\settings\\settings.xml'
}
}

stage('Deploy applicatio to cloud hub'){

environment {
        ANYPOINT_CREDENTIALS = credentials('anypoint.credentials')
      }
steps {
echo " user is ${ANYPOINT_CREDENTIALS_USR}"
echo "paw=swword is ${ANYPOINT_CREDENTIALS_PSW}" 
bat 'mvn clean package deploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -Dcloudhub.application.name=cicd-demo-app -Denvironment=Sandbox -Dworkers=1 -DworkerType=Micro -Dapp.runtime=4.3.0 -DmuleDeploy'
}
}


}

}