pipeline {
    agent {
        label "master"
    }

    stages {
       	stage('Run ansible') {
            steps {                 
				sh "ansible-playbook -i hosts ansible-winrm.yml"
            }
        }    
    }
}


