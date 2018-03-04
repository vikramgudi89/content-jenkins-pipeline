pipeline {
 agent any
 stages {
 stage('build') {
 steps {
 sh 'javac -d . src/*.java'
 sh 'echo Main-Class: Rectangulator > MANIFEST.MF'
 sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
 }
 }
      stage ("Publish reports") {
     steps {
        sloccountPublish encoding: '', pattern: ''
    }
}
 stage('test') {
 steps {
 sh 'java -jar rectangle.jar 7 9'
 }
 }
     stage ("Analyse") {
      steps {
        sh "$WORKSPACE && pwd"
         sh 'sloccount --duplicates --wide --details . > sloccount.sc'
    }
     }
    }    
  post {
 success {
  sh "cat sloccount.sc"
 archiveArtifacts artifacts: 'rectangle.jar', fingerprint:
true
 }
 }
}
