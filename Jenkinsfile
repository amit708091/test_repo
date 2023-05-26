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
  
  stage('Deploy on staging server') {
             sshagent(credentials: ['582ae2909ef36c0bf5e2f503b50c6cc4cc41484ee66e526c04b5000ee2162208']) {
      sh '''
          [ -d ~/.ssh ] || mkdir ~/.ssh && chmod 0777 ~/secret.key
          ssh-keyscan -t rsa,dsa 192.0.0.249 >> ~/secret.key
          ssh amit@192.0.0.249 ...
      '''
        }
            
     }
 }
 

