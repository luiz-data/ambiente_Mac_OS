## **Comandos da Aula - MacOS**

### **Configuração do Git**

Crie um novo repositório ou clone um já existente e faça o seu primeiro commit para versionar o projeto.

1.  **Verificar se o Git está instalado:**
    ```bash
    git --version
    ```
    *Se não estiver instalado, o MacOS solicitará a instalação das ferramentas de linha de comando do Xcode.*

2.  **Clonar o repositório:**
    ```bash
    git clone git@github.com:GeovanyADCancio/aulas_empregadados.git
    ```
    *Ou, se preferir criar um novo:*
    ```bash
    git init
    ```

3.  **Acessar a pasta do projeto:**
    ```bash
    cd aulas_empregadados
    ```

4.  **Adicionar e salvar arquivos (`commit`):**
    ```bash
    git add .
    git commit -m "Adicionando o arquivo README."
    ```

5.  **Enviar as alterações para o repositório remoto:**
    ```bash
    git push origin main
    ```

6.  **Verificar o histórico de commits:**
    ```bash
    git log
    ```

7.  **Gerenciar branches para novas funcionalidades:**
    ```bash
    git branch dev
    git checkout dev
    git merge main
    ```

---

### **Ambiente Virtual Python (`venv`)**

Configure um ambiente virtual para isolar as dependências do seu projeto.

1.  **Verificar a versão do Python:**
    ```bash
    python3 --version
    ```
    *O MacOS vem com Python 3 pré-instalado. Se necessário, instale via Homebrew:*
    ```bash
    brew install python3
    ```

2.  **Criar o ambiente virtual:**
    ```bash
    python3 -m venv venv
    ```

3.  **Ativar o ambiente virtual:**
    ```bash
    source venv/bin/activate
    ```
    *Para desativar o ambiente virtual:*
    ```bash
    deactivate
    ```

4.  **Gerar o arquivo de dependências (`requirements.txt`):**
    ```bash
    pip freeze > requirements.txt
    ```

5.  **Instalar dependências (se o arquivo `requirements.txt` já existir):**
    ```bash
    pip install -r requirements.txt
    ```

---

### **PostgreSQL no MacOS**

Siga estes passos para instalar e configurar o PostgreSQL nativamente no MacOS usando Homebrew.

#### **Instalação do Homebrew (se ainda não tiver)**

1.  **Instalar o Homebrew:**
    ```bash
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

2.  **Verificar a instalação:**
    ```bash
    brew --version
    ```

#### **Instalação e Início do PostgreSQL**

1.  **Instalar o PostgreSQL:**
    ```bash
    brew install postgresql@16
    ```

2.  **Iniciar o serviço do PostgreSQL:**
    ```bash
    brew services start postgresql@16
    ```
    *Para parar o serviço:*
    ```bash
    brew services stop postgresql@16
    ```
    *Para verificar o status:*
    ```bash
    brew services list
    ```

3.  **Adicionar o PostgreSQL ao PATH (se necessário):**
    ```bash
    echo 'export PATH="/opt/homebrew/opt/postgresql@16/bin:$PATH"' >> ~/.zshrc
    source ~/.zshrc
    ```
    *Se você usar bash ao invés de zsh, substitua `~/.zshrc` por `~/.bash_profile`*

#### **Configuração de Usuário e Banco de Dados**

1.  **Acessar o terminal interativo do PostgreSQL (`psql`):**
    ```bash
    psql postgres
    ```
    *Ou, se preferir acessar com o usuário padrão:*
    ```bash
    psql -d postgres
    ```

2.  **Criar o usuário `geovany`:**
    ```sql
    CREATE USER geovany WITH SUPERUSER CREATEDB CREATEROLE LOGIN ENCRYPTED PASSWORD '123456789';
    ```

3.  **Criar o banco de dados `analise_funcionarios` e definir o proprietário:**
    ```sql
    CREATE DATABASE analise_funcionarios OWNER geovany;
    ```

4.  **Conceder permissões ao novo banco de dados:**
    ```sql
    GRANT ALL PRIVILEGES ON DATABASE analise_funcionarios TO geovany;
    ```

5.  **Sair do psql:**
    ```sql
    \q
    ```

#### **Configuração para Acesso de Aplicações**

Por padrão, o PostgreSQL no MacOS já aceita conexões locais. Caso precise ajustar:

1.  **Localizar o arquivo de configuração:**
    ```bash
    psql -d postgres -c "SHOW config_file;"
    ```

2.  **Editar o arquivo `postgresql.conf` (opcional):**
    ```bash
    nano /opt/homebrew/var/postgresql@16/postgresql.conf
    ```
    *O caminho pode variar. Use o resultado do comando anterior.*

    * Verifique se a linha `listen_addresses` está configurada:
        ```
        listen_addresses = 'localhost'
        ```
    *Para aceitar conexões externas (cuidado com segurança):*
        ```
        listen_addresses = '*'
        ```

3.  **Editar o arquivo `pg_hba.conf` (opcional):**
    ```bash
    nano /opt/homebrew/var/postgresql@16/pg_hba.conf
    ```

    * Adicione ou verifique se existe a linha para conexões locais:
        ```
        host    all             all             127.0.0.1/32            md5
        ```

4.  **Reiniciar o serviço do PostgreSQL para aplicar as alterações:**
    ```bash
    brew services restart postgresql@16
    ```

#### **Testando a Conexão**

1.  **Conectar com o novo usuário:**
    ```bash
    psql -U geovany -d analise_funcionarios -h localhost
    ```
    *Digite a senha quando solicitado: `123456789`*

2.  **Verificar a conexão:**
    ```sql
    SELECT version();
    ```

---

### **Conectando com DBeaver ou pgAdmin**

Use as seguintes credenciais para conectar suas ferramentas de gerenciamento:

* **Host:** `localhost`
* **Porta:** `5432`
* **Database:** `analise_funcionarios`
* **Usuário:** `geovany`
* **Senha:** `123456789`

---

### **Comandos Úteis do PostgreSQL no MacOS**

* **Iniciar PostgreSQL automaticamente no boot:**
    ```bash
    brew services start postgresql@16
    ```

* **Parar o serviço:**
    ```bash
    brew services stop postgresql@16
    ```

* **Reiniciar o serviço:**
    ```bash
    brew services restart postgresql@16
    ```

* **Ver logs do PostgreSQL:**
    ```bash
    tail -f /opt/homebrew/var/log/postgresql@16.log
    ```

* **Listar todos os bancos de dados:**
    ```bash
    psql -U geovany -d postgres -c "\l"
    ```

---

### **Observações Importantes**

* **Firewall:** O MacOS geralmente não bloqueia conexões locais por padrão. Não é necessário configurar firewall para uso local.
* **Caminhos:** Os caminhos podem variar entre Macs Intel (`/usr/local/`) e Macs com Apple Silicon (`/opt/homebrew/`).
* **Segurança:** Em ambiente de produção, nunca use senhas simples como `123456789`.


1️⃣ Em ambiente MacOS preciso do WSL?
NÃO! Definitivamente não precisa!
Por quê?

WSL = Windows Subsystem for Linux (é uma camada Linux dentro do Windows)
MacOS já é Unix-based (baseado em BSD/Unix)
No Mac você já tem terminal Unix nativo, então roda tudo direto!

Resumo:

Windows → Precisa de WSL para rodar PostgreSQL/ferramentas Linux
MacOS/Linux → Roda tudo nativamente, sem WSL

É como se o Mac já tivesse o "WSL embutido" por natureza! 🍎

2️⃣ O que é mais comum no mercado de análise de dados: Visual Studio Code ou Google Colab?
Depende do tipo de trabalho, mas:
🏢 Mercado corporativo/empresas:
VS Code + Jupyter Notebooks locais (70-80%)

Projetos estruturados, com Git
Dados sensíveis (não podem ir pra nuvem)
Integração com bancos de dados internos
Pipelines de produção

🎓 Academia/Pesquisa/Prototipagem:
Google Colab (muito usado)

Pesquisa rápida
Compartilhar análises
Usar GPU grátis (deep learning)
Ensino/tutoriais

📊 Realidade prática:
A maioria dos analistas de dados usa:

VS Code (ou PyCharm/Jupyter Lab) para desenvolvimento
Google Colab para testes rápidos ou compartilhar algo pontual

3️⃣ O que é processo?
Em computação, um processo é:
🔹 Definição simples: Um programa em execução na memória do computador.
Exemplo prático:

Você abre o PostgreSQL → cria um processo do banco de dados
Você roda um script Python → cria um processo Python
Cada aba do navegador → um processo separado

Características:

Tem seu próprio espaço de memória
Pode criar sub-processos (threads)
Sistema operacional gerencia (CPU, memória)

No contexto da aula:
Quando você faz sudo service postgresql start, está iniciando o processo do PostgreSQL que fica rodando em background esperando conexões.

4️⃣ O que é processo?
Em computação, um processo é:
🔹 Definição simples: Um programa em execução na memória do computador.
Exemplo prático:

Você abre o PostgreSQL → cria um processo do banco de dados
Você roda um script Python → cria um processo Python
Cada aba do navegador → um processo separado

Características:

Tem seu próprio espaço de memória
Pode criar sub-processos (threads)
Sistema operacional gerencia (CPU, memória)

No contexto da aula:
Quando você faz sudo service postgresql start, está iniciando o processo do PostgreSQL que fica rodando em background esperando conexões.

5️⃣ Qual a arquitetura do PostgreSQL?
O PostgreSQL tem uma arquitetura cliente-servidor:


Componentes principais:

* Postmaster: Processo principal que gerencia conexões
* Backend processes: Cada conexão de cliente cria um processo separado
* Shared Memory: Área compartilhada (cache, buffers)
* WAL (Write-Ahead Log): Sistema de recuperação/transações
* Storage: Arquivos físicos no disco

Por isso na aula você:

* Configura listen_addresses = '*' → permite conexões externas
* Libera firewall → deixa a porta 5432 acessível
* Cria usuário/banco → define permissões de acesso
