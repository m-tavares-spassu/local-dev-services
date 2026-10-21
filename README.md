# Local Dev Services

Este repositório contém um arquivo Docker Compose com ferramentas utilizadas no desenvolvimento de software no Ateliê de Software Spassu, centralizando sua configuração e execução no ambiente local dos desenvolvedores.

## Pré-requisitos

- Docker instalado e disponível na máquina.
- Docker Compose V2.

## Serviços

| Serviço | Descrição | Porta padrão |
|---|---|---:|
| SonarQube | Análise de qualidade de código. | 9000 |
| Keycloak | Gerenciamento de identidade e acesso. | 8080 |
| RedisInsight | Interface para gerenciamento de bancos Redis e compatíveis. | 5520 |

## Configuração do Ambiente

Crie um arquivo `.env` na raiz do projeto:

```dotenv
SONARQUBE_PORT=9000

KEYCLOAK_PORT=8080
KEYCLOAK_ADMIN=admin
KEYCLOAK_ADMIN_PASSWORD=change-me-local

REDISINSIGHT_PORT=5520
```

As portas podem ser alteradas conforme a necessidade. Não versione o arquivo `.env` caso contenha credenciais.

Os dados dos serviços são persistidos em volumes Docker, preservando as configurações entre reinicializações.

## Utilização

Inicie os serviços:

```bash
docker compose up -d
```

Acesse os serviços:

- SonarQube: http://localhost:9000
- Keycloak: http://localhost:8080
- RedisInsight: http://localhost:5520

Verifique o estado dos contêineres:

```bash
docker compose ps
```

Consulte os logs:

```bash
docker compose logs -f
```

Pare e remova os contêineres sem excluir os dados persistidos:

```bash
docker compose down
```

Para remover também os volumes e os dados armazenados:

```bash
docker compose down -v
```

**Atenção:** o último comando apaga os dados persistidos dos serviços.
