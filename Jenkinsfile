node {
    def app
    
    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'b7bb2e28-2a32-40db-9943-311e959c2d5d', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        sh "git config user.email mirovanek@icloud.com"
                        sh "git config user.name Miroslav1234"
                        sh "cat vote-ui-deployment.yaml"
                        sh "sed -i 's+mirek1234/vote.*+mirek1234/vote:${DOCKERTAG}+g' vote-ui-deployment.yaml"
                        sh "cat vote-ui-deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job deployment: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/vote-deploy.git HEAD:master"
      }
    }
  }
}
}
