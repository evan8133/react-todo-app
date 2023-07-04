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
    	bat 'docker run -d -p 3000:3000 reactappjenkins'
  	}
	}
        stage('Jira Comment') {
            steps {
                jiraComment body: 'hELLO 👋 ', issueKey: 'SCP-2'
            }
        }
		stage('Execute JMeter') {
            steps {
                
				bat '''C:
				cd C:\\Program Files\\jmeter\\bin
				jmeter -n -t C:\\Program Files\\jmeter\\bin\\SMTP_Sampler.jmx -l C:\\Program Files\\jmeter\\bin\\SMTP_Sampler_logfile.jtl'''
            }
        }
    }
	
}
