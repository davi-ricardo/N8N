# N8N com PostgreSQL (Docker)

Este projeto contém uma configuração do **n8n** (ferramenta de automação de fluxo de trabalho) integrada com um banco de dados **PostgreSQL**, utilizando Docker Compose.

## 🚀 Serviços

O arquivo `docker-compose.yaml` orquestra os seguintes serviços:

*   **n8n**: A plataforma de automação.
    *   Porta: `5678`
    *   Timezone: `America/Cuiaba`
*   **db (PostgreSQL)**: Banco de dados dedicado para o n8n.
    *   Versão: `16-alpine`
    *   Porta interna: `5432`

## 📋 Pré-requisitos

*   [Docker](https://www.docker.com/get-started)
*   [Docker Compose](https://docs.docker.com/compose/install/)

## 🛠️ Como usar

1.  **Clone o repositório** (se estiver usando git):
    ```bash
    git clone <seu-repositorio>
    cd N8N
    ```

2.  **Inicie os containers**:
    ```bash
    docker-compose up -d
    ```

3.  **Acesse o n8n**:
    Abra seu navegador e acesse:
    *   URL Local: `http://localhost:5678`
    *   *Nota: A configuração atual menciona `https` e um domínio personalizado nas variáveis de ambiente. Para uso local, você pode precisar ajustar a variável `WEBHOOK_URL` ou acessar via localhost ignorando erros de certificado se aplicável.*

4.  **Parar os containers**:
    ```bash
    docker-compose down
    ```

## ⚙️ Configuração

As configurações atuais estão definidas diretamente no arquivo `docker-compose.yaml`.

**⚠️ Importante:** As credenciais de banco de dados estão expostas no arquivo de configuração. Para um ambiente de produção seguro, recomenda-se mover estas variáveis para um arquivo `.env` não versionado.

### Variáveis Principais (Atuais)
*   `POSTGRES_USER`: n8n_user
*   `POSTGRES_DB`: n8n_db
*   `WEBHOOK_URL`: https://seu-dominio.com.br/

## 💾 Persistência de Dados

Os dados são persistidos localmente nos seguintes diretórios (ignorados pelo git):
*   `./postgres_data`: Dados do banco PostgreSQL.
*   `./n8n_data`: Dados de configuração e fluxos do n8n.
