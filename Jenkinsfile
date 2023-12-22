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

    parameters{
        string(name:'NAME', defaultValue:'Guest', description:'What your names?')
        test(name:'DESCRIPTION', defaultValue:'', description:'Tell about you')
        booleanParam(name:'DEPLOY', defaultValue:false, description:'Need to deploye')
        choice(name:'SOCIAL_MEDIA', choices:['FACEBOOK','IG','TWITTER'], description:'What your social media?')
        password(name:'SECRET', defaultValue:'', description:'Secret Key')
    }

    stages{
        stage('Parameter'){
            steps{
                echo 'Hello ${params.NAME}'
                echo 'Description ${params.DESCRIPTION}'
                echo 'Deploy ${params.DEPLOY}'
                echo 'Social Media ${params.SOCIAL_MEDIA}'
                echo 'Password ${params.SECRET}'
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