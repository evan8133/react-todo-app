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
	stage('Deploy') {
  	steps {
    	git 'https://github.com/evan8133/react-todo-app.git'
    	bat 'docker build -t reactappjenkins .'
    	bat 'docker run -d -p 3000:3000 reactappjenkins'
  	}
	}
        stage('Hello') {
            steps {
                jiraComment body: 'hELLO 👋 ', issueKey: 'SCP-2'
            }
        }
    }
}
