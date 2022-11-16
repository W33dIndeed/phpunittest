pipeline {
agent any
stages {
stage ('Checkout') {
steps {
git branch:'master', url: 'https://github.com/OWASP/Vulnerable-Web-Application.git'
}
}
stage('Code Quality Check via SonarQube') {
steps {
script {
def scannerHome = tool 'SonarQube';
withSonarQubeEnv('SonarQube') {
sh "${scannerHome}/bin/sonar-scanner -Dsonar.projectKey=OWASP -Dsonar.sources=. -Dsonar.login=sqp_e0aea515616318ac69d39ea6912516a60a8cdf1f"
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
