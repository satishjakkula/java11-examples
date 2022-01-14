node('jdk11-mvn-3.8.4') {
    try {
        stage('Build') {
            git branch: 'scripted_groovy', url: 'https://github.com/satishjakkula/java11-examples.git'
        }
    }
    catch (err) {
        currentBuild.result = 'FAILURE'
    }
    finally {
        mail to: 'qtdevops@gmail.com',
        subject: "Status of the pipeline: ${currentBuild.fullDisplayName}",
        body: "${env.BUILD_URL} has result ${currentBuild.result}" 
    }
    
}