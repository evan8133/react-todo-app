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
    }
	stage('Execute JMeter') {
            steps {
                
            sh '''
               #!/bin/bash -c cd /opt/apache-jmeter-5.5/bin
               #!/bin/bash -c ./jmeter -n -t TestPlans/PetStore-End-to-End-Flow.jmx -p TestPlans/data/PetStore_LoadTest.properties -JTOTAL_THREADS=1 -JTEST_DURATION=60 -l MyRun1.jtl
               '''
            }
        }
        stage('Publish JMeter Report') {
            steps {
            
                perfReport filterRegex: '', sourceDataFiles: 'TestPlans/Installing.jtl'
            
            }
        }
}
