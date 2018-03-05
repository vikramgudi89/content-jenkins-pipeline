pipeline {
 agent any
 stages {
 stage('test') {
 steps {
 sh 'javac -d . src/*.java'
 sh 'echo Main-Class: Rectangulator > MANIFEST.MF'
 sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
 }
 }
 stage('build') {
 steps {
 sh 'java -jar rectangle.jar 7 9'
 }
 }
  stage ("Analyse") {
        sh 'sloccount --duplicates --wide --details /var/lib/jenkins/jobs/ > sloccount.sc'
    }
    stage ("Publish reports") {
        sloccountPublish encoding: '', pattern: ''
    }
    }
    }
