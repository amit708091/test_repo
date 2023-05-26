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
    
    script {
                    sshCommand remote: [
                        allowAnyHosts: true,
                        host: '192.0.0.252',
                        port: 22,
                        user: 'amit',
                        password: 'welcome'
                    ], script: '''
                        # Commands to execute on the remote server
                        echo "Hello, remote server!"
                        # ...
                    '''
                }
//              sshagent(credentials: ['ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDBE/ix7jb/ggZ1p5X5eRydB9ZEzOrUPwnZ/Tyk4zWNC9LTUWyC2wTG5WwiP4V7Rx/8xMhOS4gsWbgCjWW0K0dk30D5ZtYcPBgAfGEe/pzIj9ua0JoCurnNJUVik1S0k3EbvsYKeV1nm+PwE4M7UC+FryL0Wc18Q5WmKUL6oWf6MzqLHL4Icui7YmQieaIM/iGx4BJWVAdB0tFREkp5+H41sph62v0SgjvKS4wlj6BlGoPFpVqCQjjnAawGQjVxAhmFKtyCe/tz0rAitEaMDPkHuB0Mz/lRVpvVIQyy6zC6p4eCulTTpAvPsvs+HKiGV52+/Moa9BBrklY3YoR8oHsEAGCtoetPJLCH035zCvfVHKqBb+W667TiW5yowCNqmXXyMG4AzYqUj5g5tLHxKOd7qRnYL55UblY9uOGdNdMpFZgTzRVZYBLBXjbkAux8/Dz/HKMkfw+NUV/mov6xztfUyqB1qbTzcj60L7CN7H0AB0pzxD9kT8ZXTmiQsMkUg6U=']) {
//       sh '''
//           [ -d ~/.ssh ] || mkdir ~/.ssh && chmod 0777 ~/.ssh
//           ssh-keyscan -t rsa,dsa 192.0.0.249 >> ~/.ssh/id_rsa
//           ssh amit@192.0.0.249 ...
//       '''
//         }
            
  }
 }
 

