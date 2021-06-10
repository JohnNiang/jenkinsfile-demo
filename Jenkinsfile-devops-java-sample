pipeline {
  agent {
    node {
      label 'maven'
    }
  }

    stages {
        stage ('checkout scm') {
            steps {
                git(url: 'https://github.com/johnniang/devops-java-sample', branch: 'master', changelog: true, poll: false)
            }
        }

        stage ('unit test') {
            steps {
                container ('maven') {
                    sh 'mvn -B -gs `pwd`/configuration/settings.xml clean test'
                }
            }
        }
 
        stage ('build') {
            steps {
                container ('maven') {
                    sh 'mvn -B -Dmaven.test.skip=true -gs `pwd`/configuration/settings.xml clean package'
                }
            }
        }
    }
}
