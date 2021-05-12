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
            when {
                equals expected: "crea_directorios", actual: "${accion}"
            }
            steps {
                sh '/bin/bash ./bin/08-directorios_crea.sh'
            }
        }
        
        stage('Borra directorios') {
            when {
                equals expected: "borra_directorios", actual: "${accion}"
            }
            steps {
                sh '/bin/bash ./bin/09-directorios_borra.sh'
            }
        }
        
        stage('Clona repositorio git') {
            when {
                equals expected: "clona_repositorio", actual: "${accion}"
            }
            
            steps {
                sh '/bin/bash ./bin/10-git_clona.sh'
            }
        }
        
        stage('Copia archivos') {
            when {
                equals expected: "copia_archivos", actual: "${accion}"
            }
            
            steps {
                sh '/bin/bash ./bin/13-archivos_copia.sh'
            }
        }
        
    }    
}

