pipeline {
    agent any
    
    environment {
        FILE_NAME1 = 'meuarquivo.txt'
        FILE_NAME2 = 'file.txt'
        //ZIP_FILE_NAME = 'zipFinal3.tar'
    }
    
    stages {
        
        stage('Clear WorkSpace') {
            steps {
                cleanWs()
            }
        }
        stage('Parallel'){
        parallel {
            stage('Stage A - file.txt') {
              //  when {
              //      environment
                agent any
                steps {
                    writeFile file: "$FILE_NAME2", text: 'Este é o ficheiro file.txt da Pipeline'
                }
            }
            stage('Stage B - meuarquivo.txt') {
                agent any
                steps {
                    writeFile file: "$FILE_NAME1", text: 'Este é o ficheiro meuarquivo.txt da Pipeline'
             }
           }
        }
    }
        stage('Criação de ZIP') {
            steps {
                zip dir: '/var/jenkins_home/workspace/pipeline-aula_18-02-2021@2', zipFile: 'zipfinal.zip'
                archiveArtifacts artifacts: "zipfinal.zip", followSymlinks: false
                //sh 'tar "$ZIP_FILE_NAME" ./'
            }
        }
    } 
}