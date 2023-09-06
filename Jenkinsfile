pipeline {
    agent any
    stages {
          stage('SCM') {
      options {
        timeout(time: 5, unit: 'MINUTES')
      }
      steps {
        echo "Checkout ${ghprbAuthorRepoGitUrl} branch ${ghprbActualCommit}"
        ci_git_branch="${ghprbActualCommit}"
        ci_git_url = "${ghprbAuthorRepoGitUrl}"
        cat Jenkinsfile
        /* Checkout CI Repo */
        checkout([$class: 'GitSCM',
                 branches: [[name: ci_git_branch]],
                 doGenerateSubmoduleConfigurations: false,
                 extensions: [[$class: 'WipeWorkspace'],
                 [$class: 'CleanCheckout'],
                 [$class: 'CleanBeforeCheckout']],
                 submoduleCfg: [],
                 userRemoteConfigs: [[credentialsId: 'afrtestuserpassword',
                 url: ci_git_url]]])
       
      }
    }
        stage('build') {
            steps {
                echo "uypdate 1"
                echo 'mvn --version'
                cat Jenkinsfile
            }
        }
    }
}