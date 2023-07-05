def remote = [:]
remote.name = 'test'
remote.host = '54.160.244.62'
remote.port = 22
remote.allowAnyHosts = true
pipeline {
    agent any 
        stages {
            stage ("remote access") {
                steps {
                    script {
                        withCredentials([usernamePassword(credentialsId: 'ec2-demo-cred', passwordVariable: 'pass', usernameVariable: 'user')]) {
                            remote.user = user
                            remote.password = pass
                            sshCommand remote: remote, command: "mkdir ~/jenkins"
                            sshCommand remote: remote, command: "touch jenkins/file2"
                            sshCommand remote: remote, command: "ls ~/jenkins"
                        }
                    }
                }
            }
        }
}
