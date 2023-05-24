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

        stage('Deploy to staging server') {
             sshagent(credentials: ['
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
']) {
      sh '''
          [ -d ~/.ssh ] || mkdir ~/.ssh && chmod 0700 ~/.ssh
          ssh-keyscan -t rsa,dsa 192.0.0.252 >> ~/.ssh/id_rsa
          ssh amit@192.0.0.252 ...
      '''
    }
            
        }
     
  }
 

