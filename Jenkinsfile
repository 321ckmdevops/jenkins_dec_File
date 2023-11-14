pipeline 
{
    agent any     
    stages
    {
        stage('Chandan_Download')
        {
            steps
            {
               git 'https://github.com/321ckmdevops/maven.git' 
            }
        }
        stage('Chandan_Build')
        {
            steps
            {
                sh'mvn package'
            }
        }
        stage('Chandan_Deployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '1d0ee918-382e-4f31-9077-35699c36aeb9', path: '', url: 'http://192.168.29.237:8080')], contextPath: 't123', war: '**/*.war'
            }
        }
        stage('Chandan_Testing')
        {
            steps
            {
                git'https://github.com/321ckmdevops/FunctionalTesting.git'
                sh'java -jar /var/lib/jenkins/workspace/Final_Declarative/testing.jar'
            }
        }
        stage('Chandan_Delevery')
        {
            steps
            {
             deploy adapters: [tomcat9(credentialsId: '1d0ee918-382e-4f31-9077-35699c36aeb9', path: '', url: 'http://192.168.29.99:8080')], contextPath: 'p123', war: '**/*.war'
            }
        }
    }
}
