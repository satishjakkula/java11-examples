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
}
	post{
		always
		{
		  mail from: "vamshi.jullu@test.com",
		  to: "satish.jk@test.com",
		  subject: "${env.JOB_NAME}-${env.BUILD_NUMBER} Status Is ${currentBuild.result}",
		  body: "${env.BUILD_URL} has a result ${currentBuild.result}"
		  
		  emailext attachLog: true,
                body: """<p> Executed: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER}\'
                </b></p><p>View console outpe at "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}
                </a>"</p> <p><i>Build log is attached </i> </p>""",
                compressLog: true,
                replyTo: "do-not-reply@qt.com",
                to: "qtdevops@gmail.com",
                subject: "${env.JOB_NAME} - Build ${env.BUILD_NUMBER} -Status ${currentBuild.result}"

		}
	}

}