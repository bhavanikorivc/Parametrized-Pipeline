pipeline {
	agent any
        triggers { cron { 'H/15 * * * *' } }
         environment { Name = 'Jagadevi' }
         parameters { 
        string { name: 'NAME' , description: 'Ener your project name here:' }}
	stages {
		stage ('BUILD') 
			{
			parallel {
    				stage ('C_Build') {
                                        
                                  
 
			steps {
				sh 'echo this is the build job for ${params.NAME} by $Name'
				
                        
                                sh '''   cd /var/lib/jenkins/workspace/c-build-project/
                                         ls -lrt
                                         make clean
                                         make TASK.exe
                                         echo The build for C Project is completed
			            '''
					} }
				stage ('Java_Build') {
 			
				 steps {
 					 sh ''' echo The present working directory is : 
						pwd
                                             echo switching directory to jenkins java project.......
                                              cd /var/lib/jenkins/workspace/'Java Project'
                                               pwd
					       mvn compile
                                               mvn package
                                               
                                               		
				          '''		 }				}
                           }
			}

		stage ('TEST') {
                        environment { stagename = 'TEST' }
   			steps {
				sh '''
				  echo  This is the  $stagename  phase
                                     
				df -h
				''' } 
 		}	
		stage ('DEPLOY') {
			steps {
				sh '''
					echo This job is to deploy the builds
					echo check system size
					free -h
				'''
				}
			}	
	}
}	

