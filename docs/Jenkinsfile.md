## 🛠️ Create a Pipeline Job

You can create a new Jenkins pipeline job by using the following Jenkinsfile structure:

```bash
pipeline {
    agent any

    tools {
        jdk 'jdk17'
        nodejs 'nodejs'
    }

    environment {
        SCANNER_HOME = tool 'mysonar'
    }

    stages {
        stage("Clean") {
            steps {
                cleanWs()
            }
        }

        stage("Code") {
            steps {
                git branch: 'main', url: 'https://github.com/charan-kilana/nodejs-aws-cicd-k8s-pipeline.git'
            }
        }

        stage("Sonarqube Analysis") {
            steps {
                withSonarQubeEnv('mysonar') {
                    sh '''
                        ${SCANNER_HOME}/bin/sonar-scanner \
                        -Dsonar.projectName=zomato \
                        -Dsonar.projectKey=zomato
                    '''
                }
            }
        }

        stage("Quality Gates") {
            steps {
                script {
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonar-password'
                }
            }
        }

        stage("Install dependencies") {
            steps {
                sh 'npm install'
            }
        }

        stage("OWASP") {
            steps {
                dependencyCheck additionalArguments: '--scan ./ --disableYarnAudit --disableNodeAudit', odcInstallation: 'Dp-Check'
                dependencyCheckPublisher pattern: '**/dependency-check-report.xml'
            }
        }

        stage("Trivy scan") {
            steps {
                sh 'trivy fs . > trivyfs.txt'
            }
        }

        stage("Build Dockerfile") {
            steps {
                sh 'docker build -t image1 .'
            }
        }

        stage("Docker Build & Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'DockerHub-Credentials') {
                        sh 'docker tag image1 charansuryakilana/zomato:mydockerimage'
                        sh 'docker push charansuryakilana/zomato:mydockerimage'
                    }
                }
            }
        }

        stage("Scan image") {
            steps {
                sh 'trivy image charansuryakilana/zomato:mydockerimage'
            }
        }
    }

    post {
        always {
            echo 'Slack Notifications'
            slackSend (
                channel: '#ezdeploy-prototype',
                message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} \n" +
                         "Build ${env.BUILD_NUMBER} \n" +
                         "More info at: ${env.BUILD_URL}"
            )
        }
    }
}

```
