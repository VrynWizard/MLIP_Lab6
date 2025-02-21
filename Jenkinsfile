pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''#!/bin/bash
                echo "Build Step: In C/Java you might compile code. In Python, you might build your package or skip this step."
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''#!/bin/bash
                echo "Test Step: Setting up virtual environment and running tests..."

                # Create the virtual environment if it doesn't exist using python3
                if [ ! -d "venv" ]; then
                    python3 -m venv venv
                fi

                # Activate the virtual environment
                source venv/bin/activate

                # Upgrade pip and install dependencies.
                # Note: If you run into issues with pip complaining about an externally-managed environment,
                # you can add the --break-system-packages flag.
                pip install --upgrade pip
                pip install -r requirements.txt

                # Run tests with pytest
                pytest

                echo "pytest completed successfully"
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy Step: Deploying the project artifact or uploading files as required."
            }
        }
    }
}
