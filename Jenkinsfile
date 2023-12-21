pipeline{
    agent any

    stages{
        stage('Build'){
            steps{
                echo 'Build Step 1';
            }
            steps{
                echo 'Build Step 2';
            }
            steps{
                echo 'Build Step 3';
            }
        }
        stage('Test'){
            steps{
                echo 'Tes Step 1';
            }
            steps{
                echo 'Tes Step 2';
            }
            steps{
                echo 'Tes Step 3';
            }
        }
        stage('Deploy'){
            steps{
                echo 'Deploy Step 1';
            }
            steps{
                echo 'Deploy Step 2';
            }
            steps{
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