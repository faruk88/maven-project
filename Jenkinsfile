node{
    stage('SCM Checkout'){
      git 'https://github.com/faruk88/maven-project'

    }
    stage('Compile-Package'){
       sh 'mvn package'
    }
}
