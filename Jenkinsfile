pipeline{
    tools{
        jdk "myMavenJDK"
        maven "myMaven"
    }
    agent none
    stages{
        
        stage("compile"){
            agent any
            steps{
                sh "mvn compile"
            }
        }
        stage("test"){
            agent any
            steps{
                sh "mvn test"
            }
            post{
                always{
                    junit "gameoflife-web/target/surefire-reports/*.xml"
                }
            }
        }
        stage("package"){
            agent{
                label "linux-slave"
            }
            steps{
                git "https://github.com/sandeepg84/game-of-life.git"
                sh "mvn package"
            }
        }
    }
}
