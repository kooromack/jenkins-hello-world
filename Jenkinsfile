pipeline {
    agent any
    environment {
        // Setting JAVA_HOME and PATH for Unix (Linux)
        JAVA_HOME = isUnix() ? "/usr/lib/jvm/java-11-openjdk-amd64" : 
        "C:\\Program Files\\Java\\jdk1.8.0_202"
        PATH = isUnix() ? "${env.PATH}:${JAVA_HOME}/bin:/usr/bin" : "${env.PATH};${JAVA_HOME}\\bin;C:\\Users\\rehou\\AppData\\Local\\Microsoft\\WindowsApps"
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kooromack/jenkins-hello-world.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'echo "Running on Unix"'
                        sh 'javac HelloWorld.java'
                        sh 'java HelloWorld'
                        sh 'python3 hello.py'
                    } else {
                        bat 'echo "Running on Windows"'
                        bat 'javac HelloWorld.java'
                        bat 'java HelloWorld'
                        bat 'python hello.py'
                    }
                }
            }
        }
    }
}
