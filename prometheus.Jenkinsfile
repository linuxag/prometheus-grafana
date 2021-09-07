def git_url = 'https://github.com/newbielinux1/prometheus-grafana.git'
def git_branch = 'main'

pipeline
{
    agent
    {
        label 'worker1'
    }

    stages
    {
        stage('env-setup')
        {
            
            steps{
                   sh '''
                   mkdir -p /opt/docker/prometheus /opt/docker/prometheus/conf
                   cp prometheus/etc-prometheus.yml /opt/docker/prometheus/conf/prometheus.yml
                   chmod -R 777 /opt/docker/prometheus/
                   '''
               }
        
        }
        stage('start-dockercompose')
        {
            
            steps{
                   sh '''
                   cd prometheus
                   docker-compose -f prometheus-compose.yml down | exit 0
                   docker-compose -f prometheus-compose.yml up -d
                   '''
               }
        
        }
    }
}
