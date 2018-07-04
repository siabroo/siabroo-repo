properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '10')), disableConcurrentBuilds(), pipelineTriggers([cron('* * * * * ')])])
node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      try {
      er = git 'https://github.com/siabroo/siabroo-repo.git'
      echo "--------------------- ${er.toString()} "
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      
      } catch (rrr) {
          echo " --------------------------------------" + rrr.toString()
          error "failded to get sources from the git"
      }
      
   }
   stage('RUN script') {
       
       sh "cat result.properties "
       def props = readProperties  file: 'result.properties'
       if (props['EXIT_CODE']!='200'){
           print props['EXIT_CODE']
           error "build failed!"
       }
   }
   stage('Results') {
    //   junit '**/target/surefire-reports/TEST-*.xml'
    //   archiveArtifacts 'target/*.jar'
    echo "Results echo"
   }
}
