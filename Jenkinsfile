pipeline {
    agent any
    // environment {
    //     BLACKDUCK_TRUST_CERT=true
    // }
    stages {
        stage("unit-test") {
            steps {
                echo 'UNIT TEST EXECUTION STARTED'
            }
        }
        stage("functional-test") {
            steps {
                echo 'FUNCTIONAL TEST EXECUTION STARTED'
            }
        }
        stage("synopsys-security-scan") {
           steps {
               echo 'SYNOPSYS SECURITY SCAN STARTED'
               script {
                   def status = synopsys_scan product: "polaris",
                       polaris_assessment_types: "SCA", 
                       polaris_branch_name: "main",
                       polaris_application_name: "test_jenkins",
                       polaris_project_name: "springboot-pipeline-test",
                       polaris_prComment_enabled: true
                       // mark_build_status: 'UNSTABLE'

                   echo 'Returned status is: ' + status;
               }
            }           
        }
        stage("build") {
            steps {
                echo 'BUILD EXECUTION STARTED'
                echo 'Pulling...' + env.BRANCH_NAME
            }
        }
    }
}
