node ('master') {
   checkout scm
   stage('Build') {
      // Run the maven build
      withMaven(maven: 'M3') {
        if (isUnix()) {
           sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
        } else {
          bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
        }
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
}
