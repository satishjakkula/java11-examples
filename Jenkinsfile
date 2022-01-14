node('jdk11-mvn-3.8.4') {
    
        stage('upstream build')
        {
		  properties([pipelineTriggers([upstream('starterproject, ')])])
		}
        stage('source') {
            
            git 'https://github.com/satishjakkula/java11-examples.git'
           
        }   
		stage('build')
		{
		 	sh '''echo $PATH
			  /usr/local/apache-maven-3.8.4/bin/mvn clean package'''
		}
		stage('archive')
		{
		    archiveArtifacts artifacts: '*/*.jar', followSymlinks: false
		}
		
}