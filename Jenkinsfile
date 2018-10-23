pipeline {
environment {
    BUILD_SCRIPTS_GIT="https://github.com/sr1890/java-tomcat-maven-example.git"
    BUILD_SCRIPTS='mypipeline'
    BUILD_HOME='/var/lib/jenkins/workspace'
}
agent any
  stages {
  stage('Checkout: Code') {
steps {
      sh "mkdir -p $WORKSPACE/repo;\
      git config --global user.email 'santosh.ray@hotmail.com';\
      git config --global user.name 'sr1890';\
      git config --global push.default simple;\
      git clone $BUILD_SCRIPTS_GIT repo/$BUILD_SCRIPTS"
      sh "chmod -R +x $WORKSPACE/repo/$BUILD_SCRIPTS"
      }
    }
stage('Yum: Updates') {
      steps {
      sh "sudo chmod +x $WORKSPACE/repo/$BUILD_SCRIPTS/scripts/update.sh"
      sh "sudo $WORKSPACE/repo/$BUILD_SCRIPTS/scripts/update.sh"
     }
    }
  }
post {
        always {
            echo 'One way or another, I have finished'
            deleteDir() /* clean up our workspace */
        }
        success {
            echo 'I succeeeded!'
        }
        unstable {
            echo 'I am unstable :/'
        }
        failure {
            echo 'I failed :('
        }
        changed {
            echo 'Things were different before...'
        }
    }
}
