pipeline{
  agent any
  stages{
    stage("Checkout"){
      steps{
        git "https://github.com/igaryanthakur/Last-jenkins.git"
      }
    }
    stage("Publish"){
      steps{
        publishHTML([
          allowmissing:true, 
          alwaysLinktoLastBuild:false,
          keepAll:false,
          reportDir:".",
          reportFiles:"Demo.html",
          reportName:"Last of Jenkins"
          ])
      }
    }
  }
}
