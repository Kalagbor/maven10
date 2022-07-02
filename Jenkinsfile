node('built-in') 
{
    stage('ContinuousDownload') 
    {
         git 'https://github.com/Kalagbor/maven10.git'
    }
    stage('ContinuousBuild') 
    {
         sh 'mvn package'
    }
    stage('ContinuousDeployment') 
    {
         deploy adapters: [tomcat9(credentialsId: '30ff89f3-3472-418e-8179-07bebdfa690c', path: '', url: 'http://172.31.8.8:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting') 
    {
          git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
          sh 'java -jar /home/ubuntu/.jenkins/workspace/EniPipeline/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
       
          deploy adapters: [tomcat9(credentialsId: '30ff89f3-3472-418e-8179-07bebdfa690c', path: '', url: 'http://172.31.13.122:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}

