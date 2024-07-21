pipeline {
agent any
stages {
stage ('Checkout') {
steps {
git branch:'master', url: 'https://github.com/denmire/Vulnerable-Web-Application.git'
}
}
stage('Code Quality Check via SonarQube') {
steps {
script {
def scannerHome = tool 'SonarQube';
withSonarQubeEnv('SonarQube') {
sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=OWASP -Dsonar.sources=. -Dsonar.host.url=http://localhost:9000 -Dsonar.token=sqp_83a2a8444fa0c8eb03aa9906cf07a92155745f40"
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
