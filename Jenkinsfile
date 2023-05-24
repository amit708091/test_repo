node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def scannerHome = tool 'SonarqubeScanner4.8';
    withSonarQubeEnv() {
      sh "${scannerHome}/bin/sonar-scanner"
    }
  }
   stage('Deploy on ubuntu server'){
       sh 'ssh amit@192.0.0.252 "echo "hii""'
  }
}
