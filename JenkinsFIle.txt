pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Baixa o código do repositório
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Exemplo de comando para construir o projeto
                // Para projetos web simples, isso pode não ser necessário
                echo 'Build stage is not necessary for HTML/CSS/JS projects'
            }
        }

        stage('Test') {
            steps {
                // Comando para executar testes
                // Exemplo: executar testes de JavaScript usando uma ferramenta como Jest
                // sh 'npm test'
                echo 'Testing stage (if applicable) - No tests defined for this example'
            }
        }

        stage('Deploy') {
            steps {
                // Comando para fazer o deploy do site
                // Exemplo: copiar arquivos para um servidor ou para um diretório específico
                echo 'Deploying to the server...'
                // Exemplo de cópia de arquivos (ajuste conforme necessário)
                // sh 'scp -r * user@server:/path/to/deployment'
            }
        }
    }

    post {
        always {
            // Ações a serem executadas após o pipeline, como notificações
            echo 'Pipeline completed'
        }
        success {
            // Ações a serem realizadas se o pipeline for bem-sucedido
            echo 'Pipeline succeeded'
        }
        failure {
            // Ações a serem realizadas se o pipeline falhar
            echo 'Pipeline failed'
        }
    }
}
