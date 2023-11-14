pipeline {
agent any
stages {
stage ('Checkout') {
steps {
git branch:'main', url: 'https://github.com/yuanhan123/jenkins-phpunit-test.git'
}
}
stage('Code Quality Check via SonarQube') {
steps {
script {
def scannerHome = tool 'SonarQube';
withSonarQubeEnv('SonarQube') {
sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=phpunittest -Dsonar.sources=. -Dsonar.host.url=http://sonarqube:9000 -Dsonar.token=sqp_fc83ff87fa6bba764643c5941a00b20726cf29a0"
}
}
}
}
}
post {
always {
recordIssues enabledForFailure: true, tool: sonarQube()
}
}
}
