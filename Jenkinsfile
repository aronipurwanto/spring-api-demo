pipeline{
    agent any

    stages{
        stage('Build') {
            steps{
                echo 'Build Step 1';
            }
        }
        stage('Test') {
            steps{
                echo 'Tes Step 1';
            }
        }
        stage('Deploy'){
            steps{
                echo 'Deploy Step 1';
            }
        }
    }

    post{
        always{
            echo "Always running";
        }
        success{
            echo "When Success or OK";
        }
        failure{
            echo "When error happen";
        }
        cleanup{
            echo "After all happen";
        }
    }
}