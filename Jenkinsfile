def region_map = [
        "demo-dlp":     ['uksouth', 'ukwest'],
        "demo-dlp2":    ['uksouth', 'ukwest'],
        "demo-laa":     ['uksouth', 'ukwest'],
        "demo-push":    ['uksouth', 'ukwest'],
        "ptl-dev":      ['uksouth', 'ukwest'],
        "ptl-dep":      ['uksouth', 'ukwest'],
        "ptl-ref":      ['uksouth', 'ukwest'],
        "ptl-int":      ['uksouth', 'ukwest'],
        "ref":          ['uksouth', 'ukwest'],
        "pen-test":     ['uksouth', 'ukwest'],
        "ptl-train":    ['uksouth', 'ukwest'],
        "rfo":          ['uksouth', 'ukwest']
]

def replicated_dbs = ["ref"]
//def n3_connection =  ["ref"]

pipeline {
    agent any
    // By default, deploy the CI environment
    parameters {
        // Raw env names
        //choice(name: 'environment', choices: 'demo-dlp\ndemo-dlp2\ndemo-laa\ndemo-push\nptl-dev\nptl-ref\nptl-dep\nptl-int\nref\npen-test\nptl-train\nrfo', description: 'The environment to create')
        string(name: 'address_space', defaultValue: '172.20', description: 'The first two octets of the address space that will be created for each part of the infrastructure')
        booleanParam(name: 'globalInfrastructure', defaultValue: false, description: 'Deploy global infrastructure')
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '1'))
    }
    environment {
        // Credentials
        azure_sp = 'nhs_digital_subscription'
        github_credential = '42cd9098-46d6-4322-bded-d51f0aad8a68'
        azure_subscription = '74f01f0f-bf46-4285-9722-93c77918dc30'
        // Docker Credential
        azure_registry = '43db86c9-09fb-4c64-b658-81e5cb8f41e1'
        // Settings
        azure_global_region = 'uksouth'
    }

    stages {

        stage ('output build params')
        {
            steps
            {
                script 
                {
                    sh """
                        echo "\${environment}"
                    """
                }
            }
        }
    }
}




