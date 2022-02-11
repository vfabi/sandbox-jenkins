@Library('jsl@k8s')_

def config = [
    projectType: 'application',
    buildTool: 'nodejs',
    releaseBranches: ['release-1', 'newbranch2'],
    stages: ['BuildDocker','Deploy']
]
Pipeline(config)
