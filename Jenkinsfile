pipeline{
    agent any

    environment {
        AUTHOR = "Roni Purwanto"
        COMPANY = "SGI Asia"
        APP = credentials("user_roni")
    }

    options{
        disableConcurrentBuilds()
        timeout(time:10, unit:'SECONDS')
    }

    triggers{
        cron("* * * * *")
        //pullSCM("*/5 * * * *")
    }

    stages{
        stage('input'){
            input{
                message "can we deploy?"
                ok "Yes, of course"
                submitters "roni,irfan,mugi,fariz"
                parameters {
                    choice(name:'TARGET_ENV', choices:['DEV','UAT','PROD'], description:'Will deploy to')
                }
            }
            steps{
                echo "Deploy to: ${TARGET_ENV}"
            }

        }
        stage('Preparation'){
            steps{
                echo "AUTHOR: ${AUTHOR}"
                echo "COMPANY: ${COMPANY}"
                echo "Username : ${APP_USR}"
                sh('echo "Password : $APP_PSW" > "rahasia.txt"')
                echo "Start Job: ${env.JOB_NAME}"
                echo "Start Build: ${env.BUILD_NUMBER}"
                echo "Branch Name: ${env.BRANCH_NAME}"
            }
        }

        stage('Build') {
            steps{
                script{
                    for(int i = 0; i < 10; i++){
                        echo "SCRIPT ke ${i}";
                    }
                }

                echo 'Start build';
                //sh "./mvnw clean compile test-compile"
                echo 'Finish Build';
            }
        }
        stage('Test') {
            steps{
                script{
                    def data = [
                        "firstName":"Ahmad",
                        "lastName":"Roni",
                        "email":"ahmadroni@gmail"
                    ]

                    writeJSON(file:"data.json", json:data)
                }
                echo 'Start Test';
                //sh "./mvnw test"
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