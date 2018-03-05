pipeline {
 agent any
 stages {
 stage('start in acxiom') {
 steps {
 sh 'javac -d . src/*.java'
 sh 'echo main-class: rectangulator > manifest.mf'
 sh 'jar -cvmf manifest.mf rectangle.jar *.class'
    }
    }
 stage('next statefarm') {
 steps {
 sh 'java -jar rectangle.jar 7 9'
    }
    }
    }
  post {
 success {
 archiveArtifacts artifacts: 'rectangle.jar', fingerprint:
    true
    }
     }
    }

    test
