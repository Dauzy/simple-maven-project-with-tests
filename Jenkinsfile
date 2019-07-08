node ("master"){

  def mvnHome

  stage("Checkout SCM"){
    checkout scm
  }

  stage("Build"){
    mvnHome = tool 'M3'
    sh "'${mvnTool}/bin/mvn' -Dmaven.test.failure.ignore clean package"

  }

  stage("Results"){
    junit '**/target/surefire-reports/TEST-*.xml'
    archive 'target/*.jar'
  }

}

