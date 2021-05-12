pipeline {

    agent any

    options {
      ansiColor('xterm')
    }

    stages {

        stage('Clona repositorio') {
            steps {
                git branch: 'main', url: 'https://github.com/HugoAquinoNavarrete/ansible_scripting'
            }
        }
        
        stage('Copia llave e inventario del pipeline-05') {
            steps {
                sh 'cp ../pipeline-05/key_lab_jenkins .'
                sh 'cp ../pipeline-05/ansible_inventario.txt .'
            }
        }
        
        stage('Crea directorios') {
            steps {
                sh '/bin/bash ./bin/08-directorios_crea.sh'
            }
        }
        
    }    
}

