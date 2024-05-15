pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'mvn -B -DskipTests clean package'
      }  
    }
    stage('pmd') {
      steps {
        bat 'mvn pmd:pmd'
      }
    }
    stage('doc') {
      steps {
        bat 'mvn javadoc:jar'
      }
    }
    stage('test') {
      steps {
        bat 'mvn test --fail-never'
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: '**/target/site/**', fingerprint: true
      archiveArtifacts artifacts: '**/target/**/*.jar', fingerprint: true
      archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
      archiveArtifacts artifacts: '**/target/**/*javadoc.jar', fingerprint: true
      archiveArtifacts artifacts: '**/target/**/*tests.jar', fingerprint: true
      archiveArtifacts artifacts: '**/target/**/*.html', fingerprint: true
      archiveArtifacts artifacts: '**/target/**/*.war', fingerprint: true
      archiveArtifacts artifacts: '**/target/**/*.xml', fingerprint: true
    }
  }
}
