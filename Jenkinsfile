node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'jenkins-pet', usernameVariable: 'GIT_USERNAME', passwordVariable: 'GIT_PASSWORD')]){
                        sh "cat my-k8sapp-chart/values.yaml"
                        sh "sed -i 's+val717/k8s-app.*+val717/k8s-app:${DOCKERTAG}+g' my-k8sapp-chart/values.yaml"
                        sh "cat my-k8sapp-chart/values.yaml"
                        sh "git add ."
                        sh "git config --local credential.helper "if() { echo username=\\$GIT_USERNAME; echo password=\\$GIT_PASSWORD; }; f"
                        sh "git push origin HEAD:main" 
      }
    }
  }
}
}