node {
   def mvnHome
   
   stage('Checkout'){
        checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: '8327a163-908e-4ae2-9dc8-429677781816', url: 'https://github.com/bharathchitraju/java_application.git']]])
    }
   
      stage('Build') {
      // Run the maven build
      if (isUnix()) {
          sh returnStatus: true, script: 'mvn install'

       //  sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Deploy') {
      build 'deployment_job'
   }
   
}
