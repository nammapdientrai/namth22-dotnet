pipeline {
    agent {
        label "master"
    }

    parameters {
		string(name: 'aws_key', defaultValue: 'namth22', description: '')
		string(name: 'build_version', defaultValue: '0.1', description: '')
		string(name: 'Release', defaultValue: 'Latest', description: '')

		string(name: 'source_ami', defaultValue: 'ami-08289040f56a29bdb', description: '')
		string(name: 'source_ami_name', defaultValue: 'windows2019-base', description: '')
		string(name: 'OS_Version', defaultValue: 'windows2019-base', description: '')

 		string(name: 'vpc_id', defaultValue: 'vpc-44c4f323', description: '')
        string(name: 'subnet_id', defaultValue: 'subnet-71727d37', description: '')
        string(name: 'region', defaultValue: 'ap-southeast-1', description: '')
		string(name: 'instance_type', defaultValue: 't2.micro', description: '')
		string(name: 'security_group_id', defaultValue: 'sg-03e17c8d67ad2accf', description: '')

		string(name: 'ami_owners', defaultValue: '716001311520', description: '')
		string(name: 'ami_users', defaultValue: '716001311520', description: '')

		string(name: 'winrm_port', defaultValue: '5985', description: '')
		string(name: 'winrm_host', defaultValue: 'packer', description: '')
		string(name: 'winrm_insecure', defaultValue: 'true', description: '')
		string(name: 'winrm_use_ssl', defaultValue: 'true', description: '')
		string(name: 'ssh_interface', defaultValue: 'private_ip', description: '')
        string(name: 'disable_stop_instance', defaultValue: 'false', description: '')
		
        //string(name: 'ansible_inventory', defaultValue: '/etc/ansible/hosts', description: '')
		//string(name: 'user_data_file', defaultValue: 'userdata/windows-winrm.ps1', description: '')
    }
	environment {
		  PACKER = 'packer'

		  aws_access 			  =  credentials('aws_access')
		  winrm_access		      =  credentials('winrm_access')

		  aws_access_key		  = "${aws_access_usr}"
		  aws_secret_key		  = "${aws_access_psw}"

		  winrm_username		  = "${winrm_access_usr}"
		  winrm_password		  = "${winrm_access_psw}"

		  build_version			  = "${params.build_version}"
		  Release			      = "${params.Release}"
	      source_ami			  = "${params.source_ami}"
	      source_ami_name		  = "${params.source_ami_name}"
	      OS_Version			  = "${params.OS_Version}"
	      instance_type		      = "${params.instance_type}"
	      aws_key	        	  = "${params.aws_key}"
	      region		          = "${params.region}"
	      vpc_id		          = "${params.vpc_id}"
          subnet_id		          = "${params.subnet_id}"
          security_group_id		  = "${params.security_group_id}"  
          winrm_host			  = "${params.winrm_host}"
	      ami_owners			  = "${params.ami_owners}"
	      ami_users			      = "${params.ami_users}"
	      winrm_port			  = "${params.winrm_port}"
	      winrm_insecure		  = "${params.winrm_insecure}"
	      winrm_use_ssl			  = "${params.winrm_use_ssl}"
	      ssh_interface			  = "${params.ssh_interface}"
          disable_stop_instance	  = "${params.disable_stop_instance}"

	      //ansible_inventory		  = "${params.ansible_inventory}"
	      //user_data_file		  = "${params.user_data_file}"
    }

    stages {
        stage('Validate') {
            steps {                 
                sh " ${PACKER} validate packer.json"

                echo "Validate"
            }
        } 

        stage('Build IMA with packer') {
            steps {
                sh "PACKER_LOG=1 PACKER_LOG_PATH=packerlog.txt packer build -machine-readable packer.json"

                echo "Build IMA with packer"
            }
        }   

       	stage('Run ansible') {
            steps {                 
				// sh "ansible-playbook -i hosts ansible-winrm.yml"

                echo "Run ansible"
            }
        }  


    }
}


