# Trabalho de Computação Distribuída - Loja de Livros com API e Microserviço de QR Code

Este projeto é uma aplicação de loja de livros construída com Flask, que simula a compra de livros e a geração de QR Codes para as transações. O projeto é dividido em três serviços principais:

- API principal (Loja de Livros)
- Microserviço de geração de QR Code
- Servidor RabbitMQ para troca de mensagens entre a API e o microserviço

## Pré-requisitos

- **Docker**: Certifique-se de ter o Docker instalado em sua máquina. [Instale o Docker aqui](https://docs.docker.com/get-docker/).
- **Docker Compose**: Docker Compose também deve estar instalado para orquestrar os serviços. [Instale o Docker Compose aqui](https://docs.docker.com/compose/install/).

## Configuração e Execução

1. Clone este repositório em sua máquina:
   ```bash
   git clone <URL_DO_REPOSITORIO>
   cd <NOME_DO_DIRETORIO>

Verifique o arquivo docker-compose.yml. Esse arquivo orquestra os três serviços:

- **flask_api**: A API principal da loja de livros.
- **microservico_qr**: O microserviço para geração de QR Code.
- **rabbitmq**: O servidor RabbitMQ para troca de mensagens entre os serviços.

2. Inicie os serviços com o Docker Compose:
   ```bash
   docker-compose up

3. Acessando a Aplicação
- Acesse em http://<SEU_ENDERECO_DE_REDE>:5000/ para visualizar a loja de livros.
- O Microserviço de QR Code é acessado internamente pela API principal, mas você pode testá-lo diretamente em http://<SEU_ENDERECO_DE_REDE>:5001/gerar_qr_code.
- A RabbitMQ Management UI pode ser acessada em http://<SEU_ENDERECO_DE_REDE>:15672 com as devidas credenciais.

**Nota**: O <SEU_ENDERECO_DE_REDE> deve ser substituído pelo endereço de rede da máquina onde os contêineres estão sendo executados, acessível pelos usuários externos.

4. Exemplo de Fluxo de Uso
- Abra a loja de livros (http://<SEU_ENDERECO_DE_REDE>:5000/) no navegador.
- Escolha um livro e clique em "Comprar".
- A aplicação solicitará ao microserviço de QR Code a geração de um QR code para a compra.
- O microserviço retorna o QR code, que é exibido na tela de confirmação de compra.
- Os registros de troca de mensagens podem ser visualizados no painel de gerenciamento do RabbitMQ.
