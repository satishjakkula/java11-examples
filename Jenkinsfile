node('jdk11-mvn3.8.4') {
    try {
        properties([parameters([choice(choices: ['scripted', 'master', 'declarative'], description: 'branch to be built', name: 'BRANCH_TO_BUILD')])])
        stage('Build') {
            git 'https://github.com/spring-projects/spring-petclinic.git'
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