pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Saravanabramman/fine_tuning_llama.git'
            }
        }

        stage('Unzip Files') {
            steps {
                script {
                    // Use the 'bat' command for Windows instead of 'sh' for unzip
                    bat 'powershell -Command "Expand-Archive -Path LLM_FT.zip -DestinationPath ./unzipped_folder"'
                }
            }
        }


        stage('Install Dependencies') {
            steps {
                bat '"C:\\Users\\saravana.kumar\\AppData\\Local\\Programs\\Python\\Python312\\Scripts\\pip.exe" install -r unzipped_folder/LLM_FT/requirements.txt'
            }
        }

        
        // stage('Install Dependencies') {
        //     steps {
        //         // Use 'bat' instead of 'sh' for pip install on Windows
        //         bat 'pip install -r unzipped_folder/LLM_FT1/requirements.txt'
        //     }
        // }

        stage('Run Main File') {
            steps {
                // Use 'bat' instead of 'sh' for running Python script on Windows
                bat '"C:\\Users\\saravana.kumar\\AppData\\Local\\Programs\\Python\\Python312\\python.exe" unzipped_folder/LLM_FT/CI_CD/main.py'
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
