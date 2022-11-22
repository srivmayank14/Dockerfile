pipeline {
environment {
registry = "srivmayank1408/jenkinstest"
registryCredential = 'srivmayank1408'
dockerImage = 'nginx'
}
agent any
stages {
stage('Cloning our Git') {
steps {
git 'https://github.com/srivmayank14/Dockerfile.git'
}
}
stage('Building our image') {
steps{
script {
dockerImage = docker.build registry + ":$BUILD_NUMBER"
}
}
}
stage('Deploy our image') {
steps{
script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push()
}
}
}
}
stage('Cleaning up') {
steps{
sh "docker rmi $registry:$BUILD_NUMBER"
}
}
}
}
