CODE_CHANGES = getGitChanges()

pipeline {
 agent any
	 
	 stages { 
		stage("Checkout") {
	           
			steps { 
				echo 'Job Name: ${params.JOB_NAME}'
				git branch: 'master', url: 'https://github.com/acharya011978/simple-java-project.git'
				} 
	        	 }
	    
		 stage ("Build") { 
			 when{
				 expression{
					  BRANCH_NAME = 'master' && CODE_CHANGES == true
				 }
			 }
			steps{
				echo "building appl..."
	                    	sh 'mvn clean install'
	                     }
	     
	     	            
	        }
	        
	 stage("Deploy"){
			 steps { 
				 echo 'deploying the application'
		           	// echo 'deploying version: ${params.VERSION}'
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
