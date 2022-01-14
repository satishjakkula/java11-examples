node('jdk11-mvn-3.8.4') {
    
        stage('build') {
            git 'https://github.com/satishjakkula/java11-examples.git'
        }   
		stage('build')
		{
			cleanWs()
			sh '''echo $PATH
			/usr/local/apache-maven-3.8.4/bin/mvn clean package'''
		}
		
}