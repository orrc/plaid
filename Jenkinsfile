pipeline {
  agent {
    docker {
      image 'mreichelt/android:28'
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }
  stages {
    stage('Build') {
      steps {
        sh './gradlew compileDebugSources'
      }
    }
    stage('Test') {
      steps {
        sh './gradlew test'
        junit '**/TEST-*.xml'
      }
    }
    stage('Archive') {
      steps {
        archiveArtifacts '**/*.apk'
      }
    }
  }
}
