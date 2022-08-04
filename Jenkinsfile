pipeline{
    agent any
    tools {
        maven 'Maven' 
    }
    stages{
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
               
            
                }
            }
        stage("Build"){
            steps{
                sh "mvn package"
                
            
                }
            }
        stage("Deploy on test"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcattest', path: '', url: 'http://13.233.1.105:8080')], contextPath: '/app', war: '**/*.war'
                
            
                }
            }
        stage("Deploy on prod"){
            steps{
                // deploy on container -> plugin
                deploy adapters: [tomcat9(credentialsId: 'tomcatprod', path: '', url: 'http://52.66.213.29:8080')], contextPath: '/app', war: '**/*.war'
                
            
                }
            }
        }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
