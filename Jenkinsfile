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
         sh '''#!/bin/bash
SAVEIFS=$IFS
IFS=$(echo -en "\\n\\b")
rm -rf files || true
for i in `find /var/lib/jenkins/jobs -name config.xml -exec egrep -ile \'workflow-job|flow-defination\'  {} \\;`
do
  #echo $i
  #cat $i
  grep -w \'workflow\' $i > /dev/null 2>&1
  if [ $? -eq 0 ]
  then
     echo $i >> files     
  fi  
done
IFS=$SAVEIFS
#sed -i \'s/\\/config.xml//g\' files
#sed -i \'s/\\/var\\/lib\\/jenkins\\/jobs\\///g\' files
#sed -i \'\' -e \'$ d\' files
#head -n -1 files > temp; mv temp files
#sort files | uniq -u > temp; mv temp files
#cat files
sh `sloccount --duplicates --wide --details /var/lib/jenkins/jobs/ > sloccount.sc`
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
