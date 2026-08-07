# 🚀 Como Rodar o Projeto Localmente (Docker & Python Local)

Este guia orienta o passo a passo para configurar o ambiente e executar o sistema **SIEI** na sua máquina local utilizando o Docker ou interpretadores Python diretos.

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

---

## 📦 3. Preparação do Ambiente Python (Além do Docker)

Caso precise configurar as dependências locais ou rodar o sistema diretamente pelo interpretador da máquina sem o Docker, siga as instruções da **Situação A** ou da **Situação B**, dependendo das ferramentas instaladas no computador atual:

### 🔹 Situação A: Usando o método tradicional (Pip + Venv)
Utilize estes comandos se a máquina possuir apenas a instalação padrão do Python:
```powershell
# 1. Cria o ambiente virtual na pasta do projeto
python -m venv venv

# 2. Ativa o ambiente no Windows
.\venv\Scripts\Activate.ps1

# 3. Instala as dependências listadas no arquivo
pip install -r requirements.txt
```
*(Nota: Certifique-se de que a virtualização do Windows e os compiladores de C++ do Visual Studio Build Tools estejam instalados caso o comando pip exija compilação de pacotes brutos).*

### 🔹 Situação B: Usando o método moderno (UV)
Utilize estes comandos se o computador possuir a ferramenta de alta performance `uv` instalada:
```powershell
# 1. Cria o ambiente virtual de forma ultra-rápida
uv venv .venv

# 2. Ativa o ambiente integrado no Windows
.\.venv\Scripts\Activate.ps1

# 3. Instala as dependências de forma otimizada
uv pip install -r requirements.txt
```

---

## 🔄 4. Como Rodar no Dia a Dia

Depois que o ambiente já foi preparado uma vez, escolha como deseja executar o sistema hoje:

### 🐳 Opção 1: Executando pelo Docker (Recomendado pelo Lab)
O Docker cria uma caixinha isolada com o banco de dados e o sistema idêntico ao dos servidores de homologação.
1. Abra o **Docker Desktop** e aguarde até a barra inferior ficar verde (`Engine running`).
2. Se for a **primeira vez** executando na máquina atual, monte o container com:
   ```bash
   docker-compose up --build
   ```
3. Nas **próximas vezes**, inicie o servidor instantaneamente executando apenas:
   ```bash
   docker-compose up
   ```

### 🐍 Opção 2: Executando direto no Windows (Sem Docker)
Se optar por rodar o servidor local do Django pelo terminal:
1. Abra o terminal do VS Code e **ative** o ambiente virtual correspondente à máquina atual:
   * Se usou Pip/Venv: `.\venv\Scripts\Activate.ps1`
   * Se usou UV: `.\.venv\Scripts\Activate.ps1`
2. Execute o servidor de desenvolvimento:
   ```bash
   python manage.py runserver
   ```

Após a inicialização completa por qualquer um dos métodos, o sistema estará disponível em:
👉 **[http://localhost:8000](http://localhost:8000)**

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
