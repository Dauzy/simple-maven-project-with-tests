node ("master"){

  def mvnTool = tool 'M3'

  stage("Checkout SCM"){
    checkout scm
  }

  stage("Build"){
    if (isUnix()){
      sh 'echo ${mvnTool}'
      //sh '${mvnTool}/bin/mvn -Dmaven.test.failure.ignore clean package'
    }
    else {
      bat '${mvnTool}/bin/mvn -Dmaven.test.failure.ignore clean package'
    }
  }

  stage("Results"){
    junit '**/target/surefire-reports/TEST-*.xml'
    archive 'target/*.jar'
  }

}

