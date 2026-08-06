# 🚀 Como Rodar o Projeto Localmente (Docker)

Este guia orienta o passo a passo para configurar o ambiente e executar o sistema **SIEI** na sua máquina local utilizando o Docker.

---

## 🛠️ Pré-requisitos

Antes de começar, certifique-se de ter instalado em seu computador:
*   [Git](https://git-scm.com)
*   [Docker Desktop](https://docker.com) *(com suporte a WSL2 ativado)*
*   [VS Code](https://visualstudio.com)

---

## 💻 Passo a Passo para Inicialização

### 1. Clonar o Repositório
Abra o terminal na pasta onde deseja salvar seus projetos e execute:
```bash
git clone https://github.com
cd siei
```

### 2. Configurar as Variáveis de Ambiente
O projeto depende de um arquivo `.env` na raiz para funcionar. 
1. Crie um arquivo chamado `.env` na pasta raiz do projeto.
2. Copie o conteúdo padrão do arquivo de exemplo (solicite ao time caso não encontre o `.env.example`).
3. Certifique-se de salvar o arquivo antes de prosseguir.

### 3. Executar o Docker pela Primeira Vez
Abra o **Docker Desktop** e certifique-se de que o motor está rodando (`Engine running`). No terminal do VS Code, execute o comando abaixo para baixar as imagens e construir o container:
```bash
docker-compose up --build
```

Após a inicialização completa, o sistema estará disponível no seu navegador através do endereço:
👉 **[http://localhost:8000](http://localhost:8000)**

---

## 🔄 Como Rodar no Dia a Dia

Nas próximas vezes que for programar, você não precisa reconstruir o ambiente do zero. Basta seguir estes 3 passos rápidos:

1. Abra o **Docker Desktop** (deixe rodando em segundo plano).
2. Abra o projeto no **VS Code**.
3. Inicie o servidor instantaneamente executando apenas:
   ```bash
   docker-compose up
   ```

---

## 📥 Atualizando seu Código Local

Sempre antes de iniciar uma nova tarefa no laboratório, lembre-se de atualizar seu código com as últimas alterações feitas pelo time:
```bash
git pull
docker-compose up --build
```

---

## 🖧 Nova Dinâmica de Servidores UFN

Documentação interna sobre a infraestrutura e termos essenciais utilizados no laboratório.

### Ferramentas de Gerenciamento
*   **Portainer**: Interface gráfica de usuário utilizada para gerenciar e monitorar nossos containers, imagens, volumes e redes do Docker de forma simplificada no servidor da UFN.

### Expressões a se Estudar

*   **Docker**: Tecnologia de virtualização a nível de sistema operacional que permite empacotar uma aplicação e todas as suas dependências em um container isolado.
*   **Container**: Uma imagem em execução. É o ambiente isolado, leve e seguro onde a aplicação realmente roda.
*   **Imagem**: Arquivo estático (projeto, molde ou receita). É o código empacotado do seu aplicativo junto com todas as dependências (bibliotecas, variáveis de ambiente) em um único arquivo de leitura.
*   **Volume**: Mecanismo de armazenamento de dados persistentes do Docker (funciona como um "HD externo virtual"), garantindo que os dados do banco não sumam quando o container for reiniciado.
*   **Stack**: Conjunto de containers interconectados que formam uma aplicação completa. Gerencia múltiplos serviços que trabalham juntos em um ambiente de orquestração.
*   **Dockerfile**: Receita detalhada da imagem. Tem como objetivo criar as instruções e os passos para gerar um molde (imagem) dentro de um único container.
*   **Docker Compose**: Ferramenta que define e roda aplicações multi-container. Gerencia, conecta e configura múltiplos containers de forma unificada através de um arquivo YAML.


