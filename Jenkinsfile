node{
    stage('SCM Checkout'){
      git 'https://github.com/faruk88/maven-project'

    }
    stage('Compile-Package'){
       // Get maven home path
       def mvnHome = tool name: 'MAVEN', type: 'maven'
       sh "${mvnHome}/bin/mvn package"
       sh 'mvn clean package'
    }
}
