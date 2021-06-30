pipeline
{
    agent { label 'first'}
    
    triggers{
        cron('H * * * 1-5')
    }   
    stages{
        
        stage('SCM')
        {
            steps
            {
                git 'https://github.com/Bharathandmia/dev-qa-release.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        
        }
        
        stage('post build')
        {
            steps{
                junit 'gameoflife-web/target/surefire-reports/*.xml'
                archiveArtifacts 'gameoflife-web/target/*.war'
                
            }
        }
        
    }
}

