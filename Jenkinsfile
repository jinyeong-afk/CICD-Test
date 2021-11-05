node {
  stage('========== Clone repository ==========') {
   checkout scm
  }
  stage('========== Build image ==========') {
   app = docker.build("jenkins-docker-pipeline/my-image")
}
  stage('========== Push image ==========') {
   docker.withRegistry('YOUR_REGISTRY', 'YOUR_CREDENTIAL') {
    app.push("${env.BUILD_NUMBER}")
    app.push("latest")
   }
  }
 }
