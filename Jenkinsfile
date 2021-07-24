pipeline{
    agent any
     tools {
        jdk 'jdk-8.221'
    }
    stages{
      stage('Test'){
          steps{
          sh 'mvn test'
          }
      }
      stage('Build'){
          steps{
          sh 'mvn install'
          }
      }
         stage('Tool version Check') {
            steps {
                echo "Hello, Maven"
                sh "mvn --version"
            }
        }
    stage('SonarQube Analysis') {
      environment {
        SCANNER_HOME = tool 'sonar_scanner'
        ORGANIZATION = "sonarqube"
        PROJECT_NAME = "sonarqube"
      }
      steps {
        withSonarQubeEnv('sonarqube') {
            sh '''$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$ORGANIZATION \
            -Dsonar.projectKey=$PROJECT_NAME \
            -Dsonar.sources=.'''
        }
      }
    }
        stage('Stage 2') {
            steps {
                echo 'Stage2 Hello world!' 
                echo  'Stage2 $date'
            }
        }
        stage('Stage 3') {
            steps {
                echo 'Welcome to Stage3 ' 
                echo  'Stage3 '
            }
        }         
    }
}






