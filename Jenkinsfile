pipeline {
 agent any
 stages {
 stage('start in acxiom') {
 steps {
 sh 'javac -d . src/*.java'
 sh 'echo Main-Class: Rectangulator > MANIFEST.MF'
 sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
 }
 }
 stage('next statefarm') {
 steps {
 sh 'java -jar rectangle.jar 7 9'
 }
 }
     stage ("Analyse") {
      steps {
        sh 'sloccount --duplicates --wide --details path-to-code/ > sloccount.sc'
    }
     }
    stage ("Publish reports") {
     steps {
        sloccountPublish encoding: '', pattern: ''
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
