pipeline {
    agent none 
	    stages {
//          stage ('Git Checkout') {
// 			steps {
// 				echo "Checking out from Git Repo";
// 				git 'https://github.com/sunilitsme84/Jenkins-Learning.git'
//             }
// 	      }
	   stage ('Non-Parallel Stage') {
			agent {
						label 'Linux_Agent'
						 }
				  
          steps{     
             echo "Running JUnit Tests";
            //  sh label: '', script: 'sh Third_Deploy_Job.sh'
               }
        } 
		stage ('Run_Test') {
			    parallel {
					stage ('Test on Linux') {
        	 	     agent {
							
					label 'Linux_Agent'
					       }
					   steps{
						echo "Running on Linux Agent!";
				// 		sh label: '', script: 'sh First_Build_Job.sh'           
							}
					}		                   
      
      stage ('Windows-Quality-Gate') {
		        agent {
				 label 'Windows_Agent'
				}
          steps {
              echo "Verifying Quality Gates";
            //   bat label: '', script: 'First_Build_Job_Windows.bat'
               
          }
	  }
  
              }  
      } 	   
  }
  post {
     always {
         echo 'This will always run'
     } 
      success {
          echo 'This will run only if the build successful'
      }   
    
     failure {
         echo 'This will run if the build is failed'
         
     }
     unstable {
         echo 'This will run only if the build is marked as Unstable'
     }
    changed {
        echo 'This will run only if the state of the pipeline is changed'
        echo 'for example, this pipeline was previously failed and now it is successful'
        
    }
   }    
  }
