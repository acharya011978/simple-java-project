

pipeline {
 agent any
	environment{
		
		NEW_VERSION = '1.1'
	}
	parameters{
		
		string(name: 'HostIP', defaultValue: '${HostIP}', description: 'Host ipv4 address i.e.  public ip')
		
	}
	 
	 stages { 
		 
		 stage("get_Dest_IP") {
  				steps {
					{HostIP} == sh 'curl ipinfo.io/ip'
					  }
					}

		stage("Checkout") {
	           
			steps { 
				echo 'Job Name: ${params.JOB_NAME}'
				git branch: 'master', url: 'https://github.com/acharya011978/simple-java-project.git'
				} 
	        	 }
	    
		 stage ("Build") { 
			
			steps{
				echo "building appl..."
				echo "Build version is: ${NEW_VERSION}"
	                    	sh 'mvn clean compile install'
	                     }
	     
	     	            
	        }
	        
	 stage("Deploy"){
			 steps { 
				 echo 'deploying the application...'
				 echo '...'
		           	 sshagent(['deploy_user1']) {
  				 sh 'scp -o StrictHostKeyChecking=no "/var/lib/jenkins/workspace/Buddy_Works/target/works-with-heroku-1.0.war" ec2-user@${params.HostIP}:/home/ec2-user/apache-tomcat-9.0.39/webapps/'
				 		}
		               }
	      		 }
	        
	    }
	
	
	post {
		always{
			echo "send email about build status"
		}	
		success{
			echo "build succeed."
		}
	}
	
	 
	
	 }
