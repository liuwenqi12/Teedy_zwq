pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'mvn -B -DskipTests clean package'
      }  
    }
    stage('doc') {
      steps {
        bat 'mvn javadoc:jar --fail-never'
      }
    }
    stage('pmd') {
      steps {
        bat 'mvn pmd:pmd --fail-never'
      }
    }
    stage('Test Report') {
      steps {
        bat 'mvn test --fail-never'
      }
    }
  }

  post {
    always {
        archiveArtifacts artifacts: '**/target/site/**', fingerprint: true
        archiveArtifacts artifacts: '**/target/TEST-*.xml', fingerprint: true
        archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
        archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
        archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
        archiveArtifacts artifacts: '**/target/*.war', fingerprint: true
        archiveArtifacts artifacts: '**/target/site/apidocs/**', fingerprint: true
        archiveArtifacts artifacts: '**/target/surefire-reports/**', fingerprint: true
    }
  }
}
