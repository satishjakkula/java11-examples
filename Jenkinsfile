pipeline
{
	agent{ label 'jdk11-mvn-3.8.4' }
	triggers { 
	upstream(upstreamProjects: 'starterproject', threshold: hudson.model.Result.SUCCESS)
	pollSCM('*/5 * * * *')
	}
	parameters {
	choice(name: 'branch', choices: ['scripted_groovy', 'declarative_groovy', 'master'], description: 'Select The Branch To Build')
	}
	stages {
        stage('scm') {
            steps {
                 git url: 'https://github.com/satishjakkula/java11-examples.git', branch: "${params.branch}"
            }}
		stage('build') {
            steps {
                 sh '''echo $PATH
			  /usr/local/apache-maven-3.8.4/bin/mvn clean package'''
            }
        }
}}