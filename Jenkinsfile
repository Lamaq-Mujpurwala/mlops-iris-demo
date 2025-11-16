pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // This assumes your repo is named 'Exp10' or similar
                // Update the URL to match your GitHub repo
                git branch: 'main', url: 'https://github.com/Lamaq-Mujpurwala/mlops-iris-demo.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                // 'sh' is okay here if your Jenkins agent has git-bash/cygwin,
                // but 'bat' is safer on Windows.
                bat 'pip install -r requirements.txt'
            }
        }
        stage('Retrain Model') {
            steps {
                bat 'python retrain.py'
            }
        }
        stage('Deploy Model') {
            steps {
                // --- THIS IS THE UPDATED BLOCK ---
                // We use 'bat' for Windows and escape the backslashes
                bat 'copy iris_model.pkl C:\\Users\\lamaq\\OneDrive\\Desktop\\Devops\\Exp10\\'
                // --- END OF UPDATE ---
            }
        }
    }
}