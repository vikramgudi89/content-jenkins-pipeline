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
       stage ("Analyse") {
      steps {
       sh "pwd"
         sh 'sloccount --duplicates --wide --details /var/lib/jenkins/$jobs/ > sloccount.sc'
        sh "cat sloccount.sc"
    }
     }
    } 
}   
