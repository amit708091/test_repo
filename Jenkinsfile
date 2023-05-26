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
             sshagent(credentials: ['ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCfkkWUFdfpq1rTa793Yoqgun2LFqStrgkiObfVEhng6wX7xVIHDDr8AP9YkAMaBcEZQ059G28JPIcfJ73UqLnrXW2fkHPvO4xchX741n7adk79WDMS23qPI4kRrWoZ+22rHITIzrE06Ss6yO+Y65m+A0RY5PvZVK3jfQF+iO7GJ8XIEk1e0flfKbagZMTostK9zTGn73HRlwbTYV/YHPd7919Gj7Kc2iRIlQ02PhZmG4V4v3sJ0x6Eh6I8WuHNlXkhiJOni5yFU9RH8SxxE78ElCCtnLH1+N/lvvPuLssO4Fw3fqfoCtV9jIhfFMpuX35PBKY6kvXdPBhgBlLzX83Nmouf7uqezMQmBxHSr2SedsubHahwRTrG5rY652zdr4RqsKMF/wnEELO93lX8R+/v80TbRkbv7miY7rNgExSHzL5y5fPoT4qwup50LEItu4o9BPrFLSPzJB5mcDP0w6CFmxBRSUbcHQnwF3sKmPTWLOjUe+PCQSv9Un47UFFAPws=']) {
      sh '''
          [ -d ~/.ssh ] || mkdir ~/.ssh && chmod 0777 ~/.ssh
          ssh-keyscan -t rsa,dsa 192.0.0.249 >> ~/.ssh/is_rsa
          ssh amit@192.0.0.249 ...
      '''
        }
            
     }
 }
 

