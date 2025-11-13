

# 🚀 Airflow no Coolify com Docker Compose

Este repositório contém a configuração necessária para subir uma instância do **Apache Airflow** utilizando **Docker Compose** diretamente no **Coolify**.

***

## ✅ Pré-requisitos

*   **Coolify** instalado e configurado.
*   **Docker** e **Docker Compose** disponíveis no ambiente.
*   Um domínio ou subdomínio configurado para acessar os serviços.

***

## 📂 Estrutura do Projeto

    .
    ├── docker-compose.yaml   # Configuração dos serviços Airflow, Postgres e Redis
    ├── .env                  # Variáveis de ambiente
    ├── dags/                 # Seus DAGs personalizados
    ├── logs/                 # Logs do Airflow
    ├── plugins/              # Plugins adicionais
    └── config/               # Configurações extras do Airflow

***

## ⚙️ Configuração das Variáveis de Ambiente

No arquivo `.env`:

```env
AIRFLOW_UID=50000
_AIRFLOW_WWW_USER_PASSWORD=a1b2c3d4e5
SERVICE_FQDN_AIRFLOW_APISERVER=http://airflow-lkg08w4c4cwc84s0gs8g40kk.77.237.238.32.sslip.io
```

Você pode ajustar conforme necessário, especialmente a senha e o domínio.

***

## 🐳 Subindo os Serviços

1.  Clone este repositório no seu servidor Coolify.
2.  Configure as variáveis no arquivo `.env`.
3.  Execute:

```bash
docker-compose up -d
```

Isso irá subir os seguintes serviços:

*   **Postgres** (banco de dados do Airflow)
*   **Redis** (broker para Celery)
*   **Airflow Webserver**
*   **Airflow Scheduler**
*   **Airflow Worker**
*   **Airflow Triggerer**
*   **Airflow DAG Processor**
*   **Flower** (monitoramento do Celery)

***

## 🔑 Credenciais Padrão

*   **Usuário:** `airflow`
*   **Senha:** definida em `_AIRFLOW_WWW_USER_PASSWORD` no `.env`.

***

## 🌐 Acesso

*   **Airflow UI:** `${SERVICE_FQDN_AIRFLOW_APISERVER}`
*   **Flower:** `${SERVICE_FQDN_FLOWER}` (se configurado no Coolify)

***

## 🛠 Personalização

*   Adicione seus DAGs na pasta `dags/`.
*   Plugins adicionais podem ser colocados em `plugins/`.
*   Ajuste configurações no arquivo `config/airflow.cfg` se necessário.

***

## 📌 Observações

*   Este setup utiliza **CeleryExecutor** para execução distribuída.
*   Certifique-se de que os volumes persistentes estão configurados corretamente no Coolify.