pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                jiraComment body: 'hELLO 👋 ', issueKey: 'SCP-2'
            }
        }
    }
}
