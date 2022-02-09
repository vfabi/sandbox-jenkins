@Library('jsl')_

def config = [
    projectType: "application",  # Values: "application", "library" only.
    buildTool: "none",  # Values: "gradle", "nodejs". Can be extended.
    releaseBranches: ['master', 'develop'],  # Values: any branch names.
    stages: ['Preparation', 'Compile', 'Deploy'],  # Values: only implemented stages. Can be extended.
    defaultDeployEnvironment: "develop"  # Values: any defined environment name.
]
Pipeline(config)
