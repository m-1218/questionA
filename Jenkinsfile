pipeline{
    agent any
        stages{
            stage('Checkout'){
                steps{
                    git branch:'main', url: 'https://github.com/m-1218/questionA.git'
                }
            }
            stage('compile'){
                steps{
                    echo "Compile"
                    bat 'javac Factorial.java TestFactorial.java'
                }
            }
            stage('Test'){
                steps{
                    echo "Test"
                    bat 'java TestFactorial'
                }
            }
            stage('Run'){
                steps{
                    echo "Run"
                    bat 'java Factorial'
                }
            }
            stage('Package JAR'){
                steps{
                    
                    bat 'jar cfm factorial.jar manifest.txt Factorial.class'
                }
            }
            stage('Archive JAR'){
                steps{
                    echo "Deploy"
                    archiveArtifacts artifacts: 'factorial.jar'
                }
            }
        }
            post{
                success{
                    echo 'Build,test,run and JAR creation succesfull!'
                }
                failure{
                    echo 'Failed!'
                }
            }
    }
