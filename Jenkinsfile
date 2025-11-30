pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Prepare Out Folder') {
      steps {
        bat """
        if exist out rmdir /s /q out
        mkdir out
        copy index.html out\\index.html
        """
      }
    }

    stage('Run') {
      steps {
        bat """
        echo Simulating serving index.html
        echo Build_OK > artifact.txt
        """
      }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'artifact.txt, out/**', allowEmptyArchive: false
    }
  }
}
