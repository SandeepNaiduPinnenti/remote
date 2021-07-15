pipeline {
  agent any {
     stages{
         stage('One') {
           steps {
              echo "Hi!!This is sandeep running Pipeline"
           }
         }
         stage('two') {
             input("do you want to proceed")
         }
         stage('three') {
            when {
               not {
                     branch "master"
                    }
               }
               steps {
                       echo "Hello"
               }
            }
        stage('four') {
             parallel {
                   stage('Unit Test') {
                                        steps {
                                                echo "Running the unit test"
                                        }
                   }
                    stage('Integration Test') {
                                                agent {
                                                      docker {
                                                               reuseNode false
                                                               image 'ubuntu'
                                                      }
                                                }
                    } 
                    steps {
                           echo "Runing the integration Test"
                    }    
             }
        }
         }
     }
  } 
}
