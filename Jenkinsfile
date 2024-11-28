pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                // Clone the GitHub repository containing your ZIP file
                git branch: 'main', url: 'https://github.com/Saravanabramman/fine_tuning_llama.git'
            }
        }

        stage('Unzip Files') {
            steps {
                script {
                    // Unzip the downloaded ZIP file into the workspace
                    sh 'unzip LLM_FT.zip -d ./unzipped_folder'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install dependencies from requirements.txt (if available)
                sh 'pip install -r unzipped_folder/LLM_FT/requirements.txt'
            }
        }

        stage('Run Main file') {
            steps {
                // Run the main file
                sh 'python unzipped_folder/LLM_FT/CI_CD/main.py'
            }
        }

    //     stage('Fine-tuning') {
    //         steps {
    //             // Run the fine-tuning step
    //             sh 'python unzipped_folder/training.py'
    //         }
    //     }

    //     stage('Validation') {
    //         steps {
    //             // Run the validation step
    //             sh 'python unzipped_folder/validation.py'
    //         }
    //     }

    //     stage('Archive Model') {
    //         steps {
    //             archiveArtifacts artifacts: 'unzipped_folder/new_llama3.2_model_v2/**', fingerprint: true
    //         }
    //     }
    // }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs for details.'
        }
    }
}
