pipeline{
 environment {
imagename = "mjmanishdocker/couponservice"
registryCredential = 'docker_id'
dockerImage = ''
}
 agent any
 tools {
  maven 'maven3.6.3'
 }
 stages {
 stage('Build')
 {
  steps {
  script{
  sh "mvn clean install"
}
}
}
  stage('Build docker image') {
   steps{
    script{
     dockerImage = docker.build imagename
}
    }
   }
stage('Deploy Image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
//dockerImage.push("$BUILD_NUMBER")
dockerImage.push('latest')
}
}
}
}
}
}
