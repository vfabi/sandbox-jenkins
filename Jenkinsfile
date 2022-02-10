@Library('jsl@k8s')_

def config = [
    projectType: 'application',
    buildTool: 'nodejs',
    releaseBranches: ['release-1', 'newbranch2'],
    stages: ['Preparation','Deploy'],
    defaultDeployEnvironment: 'dev'
]
Pipeline(config)
