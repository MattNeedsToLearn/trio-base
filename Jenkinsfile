pipeline {
    agent any
    stages {
        stage('Appease the Machine Spirit - Build') {
            steps { 
                script{
                    sh '''
                    docker build -t mattneedstolearn/trio-redo-db:latest ./db
                    docker build -t mattneedstolearn/trio-redo-nginx:latest ./nginx
                    docker build -t mattneedstolearn/trio-redo-flask:latest ./flask-app
                    '''
                }
            }
        }
        stage('Recite the Centicle of Communication - Push') {
            steps {
                script {
                    sh '''
                    docker push mattneedstolearn/trio-redo-db:latest
                    docker push mattneedstolearn/trio-redo-nginx:latest
                    docker push mattneedstolearn/trio-redo-flask:latest
                    '''
                }
            }
        }
        stage('Empower the Machine Spirit - Deploy') {
            steps {
                script {
                        sh '''
                        kubectl apply -f ./k8s -n dev
                        kubectl rollout restart deployment flask-deployment  --namespace=dev
                        kubectl rollout restart deployment nginx-deployment  --namespace=dev
                        '''
                }
            }
        }
        stage('Apply Sacred Unguents - Clean Up') { 
            steps {
                sh '''
                echo "nothing here yet"
                '''
            }
        }
    }
}

