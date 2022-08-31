node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email purushottamthakur57@gmail.com"
                        sh "git config user.name Purush"
                        //sh "git switch master"
                        sh "cat deployment.yaml"
                        sh "sed -i 's+168812268746.dkr.ecr.us-east-1.amazonaws.com/purush.*+168812268746.dkr.ecr.us-east-1.amazonaws.com/purush:${DOCKERTAG}+g' deployment.yaml"
                        sh "cat deployment.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}: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/${GIT_USERNAME}/kubernetesmanifest.git HEAD:main"
      }
    }
  }
}
}
