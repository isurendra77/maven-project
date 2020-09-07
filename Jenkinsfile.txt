pipeline {
  agent any
  stages {
    stage('Checkout Scm') {
      steps {
        git 'https://github.com/isurendra77/maven-project'
      }
    }

    stage('Maven Build 0') {
      steps {
        bat 'mvn clean package'
      }
    }
    stage('deploy') {
      steps {
         echo 'deployment started'
         bat '''copy C:\\WINDOWS\\system32\\config\\systemprofile\\AppData\\Local\\Jenkins.jenkins\\workspace\\testpipeline1\\webapp\\target\\webapp.war D:\\RCBTRAINING\\apache-tomcat-instance1\\webapps\\'''
      }
    }
  }
  tools {
    maven 'localmaven'
  }
  post {
    always {
      step(artifacts: '**/*.war', followSymlinks: false, $class: 'ArtifactArchiver')
      echo 'No converter for Publisher: hudson.plugins.deploy.DeployPublisher'
    }

  }
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  triggers {
    pollSCM('* * * * *  ')
  }
}

