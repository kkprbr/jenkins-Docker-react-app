node {
  stage('Clone Github repository') {
     git credentialsId: 'git-creds', url: 'https://github.com/kkprbr/jenkins-Docker-react-app.git'
}
  
stage('Build image') {
    dockerImage = docker.build("9963565745/react-app:latest")
}
  
stage('Push image') {
     withDockerRegistry([ credentialsId: "dockerhub-creds", url: "" ]) {
     dockerImage.push()
     }
}
stage('Stop and Kill existing container with same name if any') {
     sh "docker rm -f react-app"

}

stage('Run the container Locally on the Jenkins server') {
    sh "docker run -itd --name react-app -p 80:81 cloudwithraghu/react-app:latest"
    }
}
