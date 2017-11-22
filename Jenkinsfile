env.dockerimagename="devopsbasservice/buildonframework:buildon-jenkinsfile"
node {
   stage ('Oodle Code Checkout') {
    checkout scm
    sh 'mvn clean package -DskipTests=True'
  }
   stage ('Maven Code Build') {
    sh 'sleep 10s'
   }

   stage ('Maven Deploy') {
    sh 'mvn --version'
   }
}
