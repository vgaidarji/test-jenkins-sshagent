node {
   checkout scm 
   stage('Git tag') {
        sshagent(['ad928936-41d1-4395-a9db-4d6aa46d35ed']) {
            sh "curl -O https://gist.githubusercontent.com/m14t/3056747/raw/2e0d5df6d141400640c8f768e5c3603533812cf6/fix_github_https_repo.sh"
            sh "chmod +x fix_github_https_repo.sh"
            sh "./fix_github_https_repo.sh"

            sh "git config user.email android+slave@test.com"
            sh "git config user.name jenkins"
            sh "git config --list"
            def tag = "test-from-jenkins-$BUILD_NUMBER"
            sh "git tag -a $tag -m \"Jenkins Git plugin tagging with $tag\""
            sh "git push origin $tag"
        }
    }
}
