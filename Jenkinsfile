    pipeline{
        agent any
        tools {
        maven 'Maven' 
    }
        stages{
            stage("test"){
                steps{
                    sh "mvn test"
                }
            }
            stage("build"){
                steps{
                    sh "mvn package"
                }
            }
             stage("deploy-on-test"){
                steps{
                   deploy adapters: [tomcat9(credentialsId: 'tomcatdetail', path: '', url: 'http://34.204.49.50:8080')], contextPath: null, war: '**/*.war'
                }
            }
            stage("deploy on prod"){
                steps{
                   deploy adapters: [tomcat9(credentialsId: 'tomcatdetail', path: '', url: 'http://54.227.104.77:8080')], contextPath: null, war: '**/*.war'
                }
            }
        }
}
