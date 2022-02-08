#!groovy


def getGitVariables = {
    def commit = sh(returnStdout: true, script: 'git rev-parse HEAD')
    git_author = sh(returnStdout: true, script: "git --no-pager show -s --format='%an' ${commit}").trim().replace("(", "").replace(")", "")
    git_author_email = sh(returnStdout: true, script: "git log -1 --pretty=%ae").trim()
    git_message = sh(returnStdout: true, script: 'git log -1 --pretty=%B').trim().replace("(", "").replace(")", "")
    git_hash = sh(returnStdout: true, script: 'git log -1 --pretty=%h').trim()
    git_branch = sh(returnStdout: true, script: 'git name-rev --name-only HEAD').split("/")[2].trim()
}


pipeline {
    agent any 
    options { timestamps () }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checkout..'
                script {
                    getGitVariables()
                    sh "mkdir artifacts && touch artifacts/cicd-dashboard-data.txt"
                    sh "echo git_branch=${git_branch} >> artifacts/cicd-dashboard-data.txt"
                    sh "echo git_author=${git_author} >> artifacts/cicd-dashboard-data.txt"
                    sh "echo git_author_email=${git_author_email} >> artifacts/cicd-dashboard-data.txt"
                    stash includes: 'artifacts/cicd-dashboard-data.txt', name: 'cicd-dashboard-data'
                }
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    
    post {
        always {
            script {
                archiveArtifacts artifacts: 'artifacats/*', fingerprint: true
            }
        }
    }
}
