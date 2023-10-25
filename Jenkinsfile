pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Environment setup') {
            steps {
                sh "sudo tools/installers/essentials.sh"
            }
        }
        stage('Configure CMake') {
            parallel {
                stage('Debug') {
                    steps {
                        sh "ls"
                        sh "cmake -B build/masscalculator-cli-Debug -G Ninja -DCMAKE_BUILD_TYPE=Debug"
                    }
                }
                stage('Release') {
                    steps {
                        sh "cmake -B build/masscalculator-cli-Release -G Ninja -DCMAKE_BUILD_TYPE=Release"
                    }
                }
            }
        }
        stage('Build') {
            parallel {
                stage('Debug') {
                    steps {
                        sh "cmake --build build/masscalculator-cli-Debug --config Debug"
                    }
                }
                stage('Release') {
                    steps {
                        sh "cmake --build build/masscalculator-cli-Release --config Release"
                    }
                }
            }
        }
        stage('Run') {
            parallel {
                stage('Debug') {
                    steps {
                        // @todo(jimmyhalimi): Update stages that are in progress.
                        echo 'Run stage (Debug) is in progress'
                    }
                }
                stage('Release') {
                    steps {
                        // @todo(jimmyhalimi): Update stages that are in progress.
                        echo 'Run stage (Release) is in progress'
                    }
                }
            }
        }
        stage('Package') {
            steps {
                // @todo(jimmyhalimi): Update stages that are in progress.
                echo 'Package stage is in progress'
            }
        }
        stage('Deploy') {
            steps {
                // @todo(jimmyhalimi): Update stages that are in progress.
                echo 'Deploy stage is in progress'
            }
        }
    }
}
