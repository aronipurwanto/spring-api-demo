pipeline{
    agent any

    environment {
        AUTHOR = "Roni Purwanto"
        COMPANY = "SGI Asia"
    }

    options{
        disableConcurrentBuilds()
        timeout(time:10, unit:'SECONDS')
    }

    triggers{
        cron("* * * * *")
        //pullSCM("*/5 * * * *")
    }

    parameters {
        string(name: "NAME", defaultValue: "Guest", description: "What is your name?")
        text(name: "DESCRIPTION", defaultValue: "Guest", description: "Tell me about you")
        booleanParam(name: "DEPLOY", defaultValue: false, description: "Need to Deploy?")
        choice(name: "SOCIAL_MEDIA", choices: ['Instagram', 'Facebook', 'Twitter'], description: "Which Social Media?")
        password(name: "SECRET", defaultValue: "", description: "Encrypt Key")
    }

    stages{
        stage('input'){
            input{
                message "can we deploy?"
                ok "Yes, of course"
                submitter "roni,irfan,mugi,fariz"
                parameters {
                    choice(name:'TARGET_ENV', choices:['DEV','UAT','PROD'], description:'Will deploy to')
                }
            }
            steps{
                echo "Deploy to: ${TARGET_ENV}"
            }

        }
        stage('Preparation'){
            environment {
                APP = credentials("user_roni")
            }

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
        stage("Release") {
              when {
                expression {
                  return params.DEPLOY
                }
              }
              steps {
                echo "Release it"
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