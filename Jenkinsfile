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
			steps{
				echo "building appl..."
	                    	sh 'mvn clean compile'
	                     }
	     
	     	            
	        }
	        
	 stage("Deploy"){
			 steps { 
				 echo 'deploying the application'
		           	// echo 'deploying version: ${params.VERSION}'
		               }
	       		 }
	        
	    }
	 }
