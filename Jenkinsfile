pipeline {
    agent {
        label "master"
    }

	environment {
		WINRM_PASS = '7O(KytgaH?Fb8?L@fW.d-RKw(LF3XPVZ'
	}

    stages {
       	stage('Run ansible') {
            steps {                 
				sh "ansible-playbook -i hosts -m ansible-winrm.yml -vvv"
            }
        }    
    }
}


