pipeline {
    agent {
        docker {
            image 'ryzebo/cnnho_node:v1.0'  
        }
    }
    stages {
        stage('install modules') { 
            steps {
                sh 'npm install' 
            }
        }
        stage('build') { 
            steps {
                sh 'npm run build' 
            }
        }
        stage('check build') { 
            steps {
                sh 'cat ./build/manifest.json' 
            }
        }
        stage("scp"){
            steps { 
                sh 'cd ./build && sshpass -p Cnnho@2019 scp -P 1709 -o StrictHostKeyChecking=no -r ./ root@103.239.152.214:/root/Projects/filemanager_wx/public/' 
            }
        }
 
    }
}