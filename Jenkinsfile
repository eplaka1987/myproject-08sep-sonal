pipeline{

agent any 

tools{
 maven 'mymaven'
}

stages{

stage('Clone the repo')
{
steps{
  git 'https://github.com/Sonal0409/DevOpsCodeDemo.git'
}
}

stage('Parallel Execution'){
parallel{

stage('Code Review')
{
   steps{
     sh 'mvn pmd:pmd'
   }
   post{
   success{
      recordIssues sourceCodeRetention: 'LAST_BUILD', tools: [pmdParser(pattern: '**/pmd.xml')]
   }
   }
}

stage('Test Code')
       {
       steps{
          sh 'mvn test'
       }
       }
}
}


}

}
