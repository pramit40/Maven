node('built-in') {
    stage('ContinuoursDownload') {
   git 'https://github.com/IntelliqDevops/maven.git'
}
  stage('ContinuousBuild') {
    sh 'mvn package'
}
   stage('ContinuourDeployment'){
       deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '4380c52c-9a00-4f0a-b0e5-d2733c44b589', path: '', url: 'http://10.0.0.31:8080')], contextPath: 'testapp', war: '**/*.war'
   }
   stage('ContinuourTesting'){
       git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
       sh 'java -jar /var/lib/jenkins/workspace/ScriptedPipeline1/testing.jar'
   }
   stage('ContinuousDelivery')
   {
       steps
   deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '4380c52c-9a00-4f0a-b0e5-d2733c44b589', path: '', url: 'http://10.0.0.94:8080')], contextPath: 'app', war: '**/*.war'
   }
}
