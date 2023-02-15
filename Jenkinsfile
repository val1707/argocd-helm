node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                        sh "cat my-k8sapp-chart/values.yaml"
                        sh "sed -i 's+val717/k8s-app.*+val717/k8s-app:${DOCKERTAG}+g' my-k8sapp-chart/values.yaml"
                        sh "cat my-k8sapp-chart/values.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://github.com/val1707/argocd-helm.git HEAD:main"   
    }
  }
 }
}