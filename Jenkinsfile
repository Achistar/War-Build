pipeline
{
    agent { label 'Build_Server' }
    stages
    {
        stage('Clean the Working Directory')
        {
            steps
            {
             deleteDir() // Clean the project directory
            }
        }
        stage('Fetch the project from GIT Repo')
        {
            steps
            {
                // Get some code from a GitHub repository
                git 'https://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@github.com/Achistar/mysql.git'

            }

        }
        stage('Build the code')
        {
            steps
            {
                 withMaven(maven: 'Maven')
                {
                    sh 'mvn clean package'
                    
                }
            }

        }
        stage('Ansible Push')
        {
            steps
            {
                ansiblePlaybook credentialsId: 'ansible_deploy', installation: 'Ansible', inventory: '/etc/ansible/hosts', playbook: '/etc/ansible/deploy.yaml'
            }
        }
    }
}
