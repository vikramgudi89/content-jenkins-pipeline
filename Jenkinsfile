pipeline {
 agent any
 stages {
 stage('down') {
 steps {
 sh 'javac -d . src/*.java'
 sh 'echo Main-Class: Rectangulator > MANIFEST.MF'
 sh 'jar -cvmf MANIFEST.MF rectangle.jar *.class'
 }
 }
 stage('on way to hell') {
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
