pipeline {
    agent any

    stages {
        stage('Install') {
  	steps {
    	git 'https://github.com/evan8133/react-todo-app.git'
    	bat 'npm install'
  	}
	}
	stage('Build') {
  	steps {
    	git 'https://github.com/evan8133/react-todo-app.git'
    	bat 'npm run build'
  	}
	}
	stage('Test') {
  	steps {
    	git 'https://github.com/evan8133/react-todo-app.git'
    	bat 'npm run test'
  	}
	}
	stage('Deploy to Docker') {
            steps {
                git 'https://github.com/evan8133/react-todo-app.git'
                bat 'docker build -t reactappjenkins .'

                script {
                    def containerName = 'my-react-app'

                    // Check if a container with the same name already exists
                    def existingContainer = bat(returnStdout: true, script: "docker ps -aqf name=${containerName}").trim()
                    if (existingContainer) {
                        // Stop and remove the existing container
                        bat "docker stop ${existingContainer}"
                        bat "docker rm ${existingContainer}"
                    }

                    // Run the container
                    bat "docker run -d -p 3000:3000 --name ${containerName} reactappjenkins"
                }
            }
        }
        stage('Jira Comment') {
            steps {
                jiraComment body: 'hELLO 👋 ', issueKey: 'SCP-2'
            }
        }
		stage('Execute JMeter') {
            steps {
                bat '''c: jmeter\\bin\\jmeter -j jmeter.save.saveservice.output_format=xml -n -t
						c: jimeter\\bin\\jenkins.io.imx -l c:\\jmeter\\reports\\jenkins.io.report.jtl'''
            }
        }
		stage('JMeter Report') {
            steps {
                perfReport filterRegex: '', showTrendGraphs: true, sourceDataFiles: 'C:\\jmeter\\reports\\jenkins.io.report.jtl'
            }
        }
    }
	
}
