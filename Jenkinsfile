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
sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=OWASP -Dsonar.sources=. -Dsonar.host.url=http://localhost:9000 -Dsonar.token=sqp_343fa97b65851472892ed15cdb4a493758c05461"
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
