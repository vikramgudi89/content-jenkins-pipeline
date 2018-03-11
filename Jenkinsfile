pipeline {
 agent any
 stages {
 
      stage ("Publish reports") {
     steps {
        sloccountPublish encoding: '', pattern: ''
    }
}
      stage ("Analyse") {
      steps {
sh 'sloccount --duplicates --wide --details /$workspace/ > sloccount.sc'
    }
     }
    }    
  
}
