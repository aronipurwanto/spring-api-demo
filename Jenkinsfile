pipeline{
    agent any

    stages{
        stage('Build') {
            steps{
                echo 'Start build';
                sh('./mvnw clean compile test-compile')
                echo 'Finish Build';
            }
        }
        stage('Test') {
            steps{
                echo 'Start Test';
                sh('./mvnw test')
                echo 'Finish Test';
            }
        }
        stage('Deploy'){
            steps{
                echo 'Start Deploy';
                sleep(10);
                echo 'Finish Deploy';
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