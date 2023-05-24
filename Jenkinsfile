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
    stages {
        stage('Connect to Staging server') {
            steps {
                script {
                    def remote = [:]
                    remote.name = 'Ubuntu server'
                    remote.host = '192.0.0.252'
                    remote.user = 'amit'
                    remote.identityFile = credentials('ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCjEC8DghquYnJPzj1dQLcJoL/gpxrhc0rh2msRhW+KLwI/3IOc92tKvT2yLo5WA7wCqAapSq73CiPbeNJ5iuE3CQJyqtbYcN7vSoE5kghyBnWdRv19rsyz/BrzYa3pSpnR4ZviQOHC8O7m4JonmZwNrL8xeShNxgGrIOlpE5DqqP99Ydhw8P8nbj+SFPW3RZ9tIeVpuOAYb1dqGXr7HxnItwojQDJRBSbRsYNr1SowbAZLFTr3p2lreCXkFvCsunBfJnSLj80XVIzBev4zee4JVUgcDJYc9A2XvYOWOFsqAFNb9qwb3X+gEWjoBJm8HQe9iPoBoJCMu8iFJEhTUq96i+wnH0tOh0TY3RzzbtPU1evreMpCVdSXFuDyDQ/FOWw3gI1zPkB1g5dpZ+JVzLjdmJNVZ+pViKqHJonXYIAo6UcHVyWp7kpVSX4G2XRx6ZDFdSSXRub5BETL+iy3MLaU6SlQuiWyJ8acOOqXuHLSveTRZ287PeiEpyx7cIplCC7kh/9pUf6KOMAuoENuh/Je1YUq7bnnYOAaYD12/pefwOhp3okEKYvckC3TawdGP+jBcaGrMYyI9tRsmSeH/FDSJLWzJV5PJ0+GCFBqqLXO26ORqUMXvSwv9cNfUHDYzOdXSvUJKVoQPF9uhKVBG9lyKYTynCuAcadwQh7TdL8gQQ== root@stpl-server')
                    remote.allowAnyHosts = true

                    withCredentials([sshUserPrivateKey(credentialsId: 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCjEC8DghquYnJPzj1dQLcJoL/gpxrhc0rh2msRhW+KLwI/3IOc92tKvT2yLo5WA7wCqAapSq73CiPbeNJ5iuE3CQJyqtbYcN7vSoE5kghyBnWdRv19rsyz/BrzYa3pSpnR4ZviQOHC8O7m4JonmZwNrL8xeShNxgGrIOlpE5DqqP99Ydhw8P8nbj+SFPW3RZ9tIeVpuOAYb1dqGXr7HxnItwojQDJRBSbRsYNr1SowbAZLFTr3p2lreCXkFvCsunBfJnSLj80XVIzBev4zee4JVUgcDJYc9A2XvYOWOFsqAFNb9qwb3X+gEWjoBJm8HQe9iPoBoJCMu8iFJEhTUq96i+wnH0tOh0TY3RzzbtPU1evreMpCVdSXFuDyDQ/FOWw3gI1zPkB1g5dpZ+JVzLjdmJNVZ+pViKqHJonXYIAo6UcHVyWp7kpVSX4G2XRx6ZDFdSSXRub5BETL+iy3MLaU6SlQuiWyJ8acOOqXuHLSveTRZ287PeiEpyx7cIplCC7kh/9pUf6KOMAuoENuh/Je1YUq7bnnYOAaYD12/pefwOhp3okEKYvckC3TawdGP+jBcaGrMYyI9tRsmSeH/FDSJLWzJV5PJ0+GCFBqqLXO26ORqUMXvSwv9cNfUHDYzOdXSvUJKVoQPF9uhKVBG9lyKYTynCuAcadwQh7TdL8gQQ== root@stpl-server', keyFileVariable: 'KEYFILE')]) {
                        remote.command = "ssh -i $KEYFILE ${remote.user}@${remote.host} 'command-to-be-executed'"
                        sshCommand remote: remote
                    }
                }
            }
        }
    }
}
