    // Jenkinsfile
pipeline {
    agent any

    stages {
        stage('Checkout SCM') {
            steps {
                echo 'Cloning the Git repository...'
                sh 'ls -la' // Show what's in the workspace after cloning
                // Add some dummy files to your repo later and list them here
            }
        }
        stage('Clone Private Repo (with PAT)') {

steps {

echo "Attempting to clone a hypothetical private repo using PAT..."

// 'withCredentials' block to securely access the PAT

withCredentials([string(credentialsId: 'github-pat-balrajpasula', variable: 'GITHUB_PAT')]) {

// Using the PAT in the git clone URL.

// For a real private repo: https://github.com/balrajpasula/my-private-repo.git

// Replace 'your-private-repo' with a non-existent or real private repo for testing

sh 'git clone https://${GITHUB_PAT}@github.com/balrajpasula/my-test-private-repo-dummy.git dummy-private-repo-clone'

sh 'ls -la dummy-private-repo-clone || true' // To verify if it managed to create the directory

sh 'rm -rf dummy-private-repo-clone || true' // Clean up the cloned repo

}

echo "Finished cloning private repo (or tried to)."

}

}


        stage('Build Dummy App') {
            steps {
                echo 'Simulating building a dummy application...'
                sh 'echo "This is a dummy build step for my new repo!" > build_output.txt'
            }
        }
        stage('Run Dummy Tests') {
            steps {
                echo 'Simulating running dummy tests...'
                sh 'echo "Dummy tests passed!" >> test_results.txt'
            }
        }
        stage('Archive Artifacts') {
            steps {
                echo 'Archiving dummy artifacts...'
                archiveArtifacts artifacts: 'build_output.txt, test_results.txt', fingerprint: true
            }
        }
    }
    post {
        always {
            echo 'Pipeline run complete!'
        }
        success {
            echo 'All stages completed successfully for your custom repo!'
        }
        failure {
            echo 'Pipeline failed for your custom repo!'
        }
    }
}


// ... (previous stages) ...

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving dummy artifacts...'
                archiveArtifacts artifacts: 'build_output.txt, test_results.txt', fingerprint: true
            }
        }
        // =======================================================
        // NEW STAGE FOR ANSIBLE DEMO HERE
        // =======================================================
        stage('Run Ansible Playbook') {
            steps {
                echo 'Running Ansible playbook...'
                // Ensure you are in the workspace where playbook.yml, ansible.cfg, inventory.ini are located
                dir('./') { // 'dir' step ensures we are in the base of the cloned repo
                    sh 'ansible-playbook -i inventory.ini playbook.yml'
                }
            }
        }
        // =======================================================
        // END NEW STAGE
        // =======================================================
    }
    post {
        always {
            echo 'Pipeline run complete!'
        }
        success {
            echo 'All stages completed successfully for your custom repo!'
        }
        failure {
            echo 'Pipeline failed for your custom repo!'
        }
    }
}
