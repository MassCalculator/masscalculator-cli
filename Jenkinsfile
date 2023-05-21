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
                        // @todo(jimmyhalimi): Update stages that are in progress.
                        // sh "cmake -B build/masscalculator-cli-Debug -G Ninja -DCMAKE_BUILD_TYPE=Debug"
                        echo 'Configure stage (Debug) is in progress'
                    }
                }
                stage('Release') {
                    steps {
                        // @todo(jimmyhalimi): Update stages that are in progress.
                        // sh "cmake -B build/masscalculator-cli-Release -G Ninja -DCMAKE_BUILD_TYPE=Release"
                        echo 'Configure stage (Release) is in progress'
                    }
                }
            }
        }
        stage('Build') {
            parallel {
                stage('Debug') {
                    steps {
                        // @todo(jimmyhalimi): Update stages that are in progress.
                        // sh "cmake --build build/masscalculator-cli-Debug --config Debug"
                        echo 'Build stage (Debug) is in progress'
                    }
                }
                stage('Release') {
                    steps {
                        // @todo(jimmyhalimi): Update stages that are in progress.
                        // sh "cmake --build build/masscalculator-cli-Release --config Release"
                        echo 'Build stage (Release) is in progress'
                    }
                }
            }
        }
        stage('Test') {
            parallel {
                stage('Debug') {
                    steps {
                        // @todo(jimmyhalimi): Update stages that are in progress.
                        echo 'Test stage (Debug) is in progress'
                    }
                }
                stage('Release') {
                    steps {
                        // @todo(jimmyhalimi): Update stages that are in progress.
                        echo 'Test stage (Release) is in progress'
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
