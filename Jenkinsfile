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
        bat 'mvn -U pmd:pmd'
      }
    }
    stage('doc') {
      steps {
        bat 'mvn -U javadoc:jar'
      }
    }
    stage('test') {
      steps {
        bat 'mvn test'
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
