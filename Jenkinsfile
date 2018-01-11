env.dockerimagename="buildon/buildon:v2"
node {
   stage ('Code Checkout') {
    checkout scm
     echo "Listing the files in the current dir"
       sh """ls -ltr
       pwd
       """
    
  }
   stage ('Code compile') {
    sh """pwd
          cd "${WORKSPACE}"
          mvn org.talend:ci.builder:6.3.1:generate -f pom.xml -Dcommandline.workspace="${WORKSPACE}/" -Dcommandline.host=34.200.55.25 -Dcommandline.port=8002 -Dcommandline.user=ankush.deshpande@cognizant.com
          ls -ltr
          """
    sh 'sleep 10s'
   }
 stage ('Code Build') {
    sh """pwd
          ls -ltr
          cd "${WORKSPACE}/"
          mvn package -f pom.xml -Dcommandline.workspace="${WORKSPACE}/" -Dcommandline.host=34.200.55.25 -Dcommandline.port=8002 -Dcommandline.user=ankush.deshpande@cognizant.com -DprojectsTargetDirectory="${WORKSPACE}/target"
          """
    sh 'sleep 10s'
   }
   stage ('Code Deploy') {
    echo "Deploying code"
    sh"""
      cd "${WORKSPACE}/target/"
      ls -ltr
      pwd
      set +e
      mvn deploy -fn -e
      set +e
    """
   }
}
