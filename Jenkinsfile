pipeline {

    agent any

    options {
      ansiColor('xterm')
    }

    parameters {
        choice(choices: ['Crear', 'Borrar'], description: 'Selecciona la acción para los directorios', name: 'directorios')
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
        

        stage("Ejecutando acciones sobre los directorios") {
            steps {
                
                script{

		    if (params.directorios == "Crear")
		    {
                       sh '/bin/bash ./bin/08-directorios_crea.sh'
                    }

		    if (params.directorios == "Borrar")
		    {
                       sh '/bin/bash ./bin/09-directorios_borra.sh'
                    }
		}
            }
        }
        
    }    
}

