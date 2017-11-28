env.dockerimagename="devopsbasservice/buildonframework:buildon-jenkinsfile"
node {
   stage ('Code Checkout') {
    checkout scm
    
  }
   stage ('Code compile') {
    sh """pwd
          cd "${WORKSPACE}"
          mvn org.talend:ci.builder:6.3.1:generate -X  -Dcommandline.workspace="${WORKSPACE}/OODLE_GIT" -Dcommandline.host=34.200.55.25 -Dcommandline.port=8002 -Dcommandline.user=ankush.deshpande@cognizant.com
          """
    sh 'sleep 10s'
   }
 stage ('Code Build') {
    sh """pwd
          cd "${WORKSPACE}"
          mvn package -fn -e  -Dcommandline.workspace="${WORKSPACE}/OODLE_GIT" -Dcommandline.host=34.200.55.25 -Dcommandline.port=8002 -Dcommandline.user=ankush.deshpande@cognizant.com -DprojectsTargetDirectory="${WORKSPACE}/OODLE_GIT/target"
          """
    sh 'sleep 10s'
   }
   stage ('Code Deplou') {
    echo "Deploying code"
    sh"""
      mvn deploy –fn –e
    """
   }
}