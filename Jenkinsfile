pipeline{
    agent any

    stages{
        stage('Build') {
            steps{
                echo 'Build Step 1';
                echo 'Build Step 2';
                echo 'Build Step 3';
            }
        }
        stage('Test') {
            steps{
                echo 'Test Step 1';
                echo 'Test Step 2';
                echo 'Test Step 3';
            }
        }
        stage('Deploy'){
            steps{
                echo 'Deploy Step 1';
                echo 'Deploy Step 2';
                echo 'Deploy Step 3';
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