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
                   synopsys_scan product: "blackduck",
                       blackduck_scan_full: true,
                       blackduck_prComment_enabled: true,
                       mark_build_if_issues_are_present: 'UNSTABLE'
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
