node('jdk11-mvn-3.8.4') {
    
        stage('Branches')
        {
		   properties([parameters([choice(choices: ['scripted_groovy', 'master', 'declarative_groovy'], description: 'Select The Branch Name ', name: 'Branch_Name')])])
           
        }
        stage('source') {
            
            git url: 'https://github.com/satishjakkula/java11-examples.git', branch: "${params.Branch_Name}"
           
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