pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''#!/bin/bash
                echo 'In C or Java, we can compile our program in this step'
                echo 'In Python, we can build our package here or skip this step'
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''#!/bin/bash
                echo 'Test Step: We run testing tool like pytest here'

                # Set up pyenv using the shared installation in your home directory
                export PYENV_ROOT="/home/chenkai2/.pyenv"
                export PATH="$PYENV_ROOT/bin:$PATH"
                eval "$(/home/chenkai2/.pyenv/bin/pyenv init --path)"
                eval "$(/home/chenkai2/.pyenv/bin/pyenv virtualenv-init -)"

                # Activate your pyenv virtual environment using the full path
                /home/chenkai2/.pyenv/bin/pyenv activate recommend_service

                # Run pytest
                pytest

                echo 'pytest completed successfully'
                '''

            }
        }
        stage('Deploy') {
            steps {
                echo 'In this step, we deploy our porject'
                echo 'Depending on the context, we may publish the project artifact or upload pickle files'
            }
        }
    }
}
