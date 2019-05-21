pipeline {
    agent {
        label "master"
    }

	environment {
		WINRM_PASS ='7O(KytgaH?Fb8?L@fW.d-RKw(LF3XPVZ'
	}

    stages {
       	stage('Run ansible') {
            steps {                 
				//sh "ansible-playbook -i hosts ansible-winrm.yml"
				sh "ansible-playbook -i hosts "+
				   "--extra-vars='ansible_winrm_server_cert_validation=ignore "+
				   "ansible_user=Administrator "+
				   "ansible_password=${winrm_pass} "+
				   "ansible_connection=winrm "+
				   "ansible_port=5985 "+ 
				   "ansible_winrm_operation_timeout_sec=120 "+
				   "ansible_winrm_read_timeout_sec=180' ansible-winrm.yml -vvv"
            }
        }    
    }
}


