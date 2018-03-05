pipeline {
 agent any
       stage ("Publish reports") {
     steps {
        sloccountPublish encoding: '', pattern: ''
    }
}
    stage ("Analyse") {
        sh 'sloccount --duplicates --wide --details /var/lib/jenkins/workspace/ > sloccount.sc'
    }
    stage ("Publish reports") {
        sloccountPublish encoding: '', pattern: ''
    }
}
