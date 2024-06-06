pipeline {
    agent {
        label 'akib-linux'
    }
    stages {
        stage("synopsys-security-scan") {
            steps {
                script {
                    synopsys_scan product: 'polaris',
                     // Uncomment if below parameters are not set in global configuration
                     // polaris_server_url: 'POLARIS_SERVER_URL',
                     // polaris_access_token: 'POLARIS_TOKEN', 
                        polaris_assessment_types: 'SAST,SCA',

                     //Optional for multibranch pipeline

                     polaris_application_name: 'test_ado', 
                     polaris_project_name: 'test_ado',
                     polaris_branch_name: 'main',

                     // Pull Request Comments
                        polaris_prComment_enabled: true,
                     // bitbucket_token: 'BITBUCKET_TOKEN', // Use github_token for GitHub or gitlab_token for GitLab
                     // polaris_branch_parent_name: 'PARENT_BRANCH_NAME',
                     
                     project_directory: "/home/akib/Synopsys/node-goat-ado/node-goat",
                     // Uncomment below configuration for source code upload
                     polaris_assessment_mode: "SOURCE_UPLOAD",
                     project_source_archive: "/home/akib/Synopsys/node-goat-ado/node-goat.zip",
                     project_source_excludes: ".git,node_modules"

                     // SARIF report generation
                        // polaris_reports_sarif_create: true
                     // Optional parameters
                     // polaris_reports_sarif_file_path: 'SARIF_FILE_PATH',
                     // polaris_reports_sarif_groupSCAIssues: true,
                     // polaris_reports_sarif_issue_types: 'SAST, SCA',
                     // polaris_reports_sarif_severities: 'CRITICAL,HIGH'
                }
            }
        }
    }
}
