node('jdk11-mvn-3.8.4') {
    
        stage('Branches')
        {
            properties([parameters([choice(choices: ['scripted_groovy', 'master', 'declarative_groovy'], name: 'Branch_Name')]), pipelineTriggers([upstream('Spring PetClinic, ')])])
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