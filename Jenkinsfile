node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

     stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                        //sh "git switch master"
                        sh "cat my-k8sapp-chart/values.yaml"
                        sh "sed -i 's+val717/k8s-app.*+val717/k8s-app:${DOCKERTAG}+g' my-k8sapp-chart/values.yaml"
                        sh "cat my-k8sapp-chart/values.yaml"
                        sh "git add ."
                        sh "git config user.name 'val1707'"
                        sh "git config user.email 'valentin.kurtev@amusnet.com'"
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push git push origin HEAD:main" 
   }
  }
 }
}