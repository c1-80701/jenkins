pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/c1-80701/jenkins.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_OnNidJboTqLSJjQgvB9tEOIABQM | /usr/bin/docker login -u piyush557 --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t piyush557/mywebsite .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push piyush557/mywebsite'
            }
        }
        stage ('docker remove service') {
            steps {
                sh '/usr/bin/docker service rm myservice'
            }
        }
        stage ('docker create service') {
            steps {
                sh '/usr/bin/docker service create --name myservice -p 9090:80 --replicas 5 piyush557/mywebsite'
            }
        }
    }
}
