pipeline {
    agent any

    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                sh 'cd bootup'
                sh 'sed -i -e "s/spring-boot-api-example:latest/spring-boot-api-example:latest/g" boot.yaml'
		sh 'now=$(date +"%m/%d/%Y")'
		sh 'echo $now > log.data'
		sh 'git add --all'
                sh 'git commit -m "updated tag"'
                sh 'git push'
            }
        }
        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }
    }
}
