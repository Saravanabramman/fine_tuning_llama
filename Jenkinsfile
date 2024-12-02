stage('Clone Repository') {
    steps {
        git branch: 'main', url: 'https://github.com/Saravanabramman/fine_tuning_llama.git'
    }
}

stage('Unzip Files') {
    steps {
        script {
            sh 'unzip LLM_FT.zip -d ./unzipped_folder'
        }
    }
}


stage('Install Dependencies') {
    steps {
        sh 'pip install -r unzipped_folder/LLM_FT/requirements.txt'
    }
}

// pipeline {
//     agent any
//     stages {
//         stage('Run Python Script') {
//             steps {
//                 bat '"C:\\Users\\saravana.kumar\\AppData\\Local\\Programs\\Python\\Python312\\python.exe" "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\test1\\test.py"'
//             }
//         }
//     }
// }


stage('Run Main file') {
    steps {
        bat '"C:\\Users\\saravana.kumar\\AppData\\Local\\Programs\\Python\\Python312\\python.exe" "unzipped_folder\\LLM_FT\\CI_CD\\main.pyy"'

        // sh 'python unzipped_folder/LLM_FT/CI_CD/main.py'
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

