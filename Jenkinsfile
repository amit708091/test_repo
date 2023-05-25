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
             sshagent(credentials: ['ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDC0GegvenePEmCQFsnbGGocnfwOSCRxZY2eLa1qfnD3XR0fancaRvj/Vl4PGsKIqFnXWrJakV15Ykz0uYcc4Rksix4JYQuNJUEMLc6nLZ5rNdt3mcUbsKJDEozo2Bv34RpMQ73I0EkSk5bh8UiUHy98lYomIPhWprqv5kPj8MJ8Zr0eCRH2z3CwimGsVS89Yb6tLqdTpAtmVPJYywvyN0rXUDzEKR4NWLPDozWS0mCFJe5n4B9i4tpt7kokz/SbPGML2aMJzTNcL8ji5WmKz5Juj6E0AL2/VzWz/rlRSt29hzDQhDrLtml7ZRFKAUv/szQfq4Ff+yy9PhwalYcrKBV web_server']) {
      sh '''
          [ -d ~/.ssh ] || mkdir ~/.ssh && chmod 0777 ~/.ssh
          ssh-keyscan -t rsa,dsa 3.111.157.115 >> ~/.ssh/
          ssh -i ubuntu@3.111.157.115 ...
      '''
        }
            
     }
     
  }
 

