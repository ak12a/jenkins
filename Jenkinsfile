pipeline {
    agent { node 'master' }
    
    parameters {
        string(defaultValue: "", description: 'Enter the user name', name: 'username')
    }
    
    stages{
        stage('Prepare') {
            steps {
                sh 'git clone https://github.com/4iglance/ansible.git'
            }
        }
    stage('After Checkout') {
            steps {
                sh 'pwd; ls'
            }
        }
    stage('Run Playbook') {
        steps {
            sh 'ansible-playbook ansible/httpd.yaml -u centos -b -e "user=$username"'
        }
    }
    stage('Wipe out workspace') {
            steps {
                deleteDir()
            }
        }
    }
}
