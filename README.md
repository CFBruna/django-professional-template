# Django Professional Template

[![Django CI](https://github.com/CFBruna/django-professional-template/actions/workflows/ci.yml/badge.svg)](https://github.com/CFBruna/django-professional-template/actions/workflows/ci.yml)

> Um boilerplate opinativo e de nível profissional para iniciar novos projetos Django rapidamente, com foco em boas práticas e produtividade.

Este template encapsula uma arquitetura robusta para desenvolvimento de aplicações web com Django, utilizando um ambiente conteinerizado com Docker. Ele vem pré-configurado com ferramentas de alta qualidade para formatação de código, testes automatizados e integração contínua.

---

## 🛠️ Stack de Tecnologias

* **Backend:** Django
* **Banco de Dados:** PostgreSQL
* **Ambiente:** Docker, Docker Compose
* **Qualidade de Código:** Ruff, Pre-commit
* **Testes:** Pytest, pytest-django, pytest-cov, factory-boy
* **Frontend:** HTML, Tailwind CSS (via CDN no `base.html`), HTMX, Alpine.js

---

## ✅ Qualidade e Automação

Este template já vem com um fluxo de trabalho de Integração Contínua (CI) configurado através do **GitHub Actions**. A cada `push` ou `pull request` para a branch `main`, o seguinte pipeline é executado automaticamente:

1.  **Instalação de Dependências:** O ambiente é criado e as dependências do `requirements.txt` são instaladas.
2.  **Verificação de Linting:** O `Ruff` é executado para garantir que o código segue os padrões de estilo e qualidade.
3.  **Execução dos Testes:** A suíte de testes completa é executada com `pytest` para garantir que todas as funcionalidades existentes continuam operando como esperado.

---

## 🚀 Como Usar Este Template

Siga os passos abaixo para iniciar um novo projeto a partir deste template.

### 1. Criação do Projeto

1.  **Crie seu repositório a partir deste template:**
    Clique no botão verde **"Use this template"** -> "Create a new repository" no topo da página.

2.  **Clone seu novo repositório:**
    ```bash
    git clone [https://github.com/CFBruna/SEU-NOVO-PROJETO.git](https://github.com/CFBruna/SEU-NOVO-PROJETO.git)
    cd SEU-NOVO-PROJETO
    ```

3.  **Configure o Ambiente Virtual e Dependências:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # ou .\\venv\\Scripts\\activate no Windows
    pip install pip-tools
    pip-compile requirements.in
    pip install -r requirements.txt
    ```

4.  **Crie o Projeto Django:**
    Use o comando `startproject` para criar os arquivos de configuração. Substitua `nome_do_projeto` pelo nome que desejar.
    ```bash
    django-admin startproject nome_do_projeto src
    ```
    *Este comando criará a pasta `src/nome_do_projeto` e o arquivo `manage.py`.*

### 2. Configuração Pós-Criação

1.  **Ajuste o `settings.py`:**
    * Mova o conteúdo relevante do `settings.py` do template (como a configuração de `DATABASES`, `INSTALLED_APPS` com `src.apps...`, etc.) para o novo arquivo `src/nome_do_projeto/settings.py`.
    * **Importante:** Verifique se os caminhos como `ROOT_URLCONF` e `WSGI_APPLICATION` estão usando o `nome_do_projeto` correto.

2.  **Ajuste o `pyproject.toml`:**
    * Abra o arquivo `pyproject.toml` e atualize a linha `DJANGO_SETTINGS_MODULE` com o nome do seu projeto.
    * **DE:** `DJANGO_SETTINGS_MODULE = "src.petcare.settings"`
    * **PARA:** `DJANGO_SETTINGS_MODULE = "src.nome_do_projeto.settings"`

3.  **Crie o arquivo de ambiente:**
    Copie o arquivo de exemplo e gere uma nova `SECRET_KEY` para o arquivo `.env`.
    ```bash
    cp .env.example .env
    ```

### 3. Execução com Docker

1.  **Construa e suba os containers:**
    ```bash
    docker-compose up --build
    ```

2.  **Rode as migrações (em um novo terminal):**
    ```bash
    docker-compose exec web python manage.py migrate
    ```

3.  **Execute os testes para verificar a instalação:**
    ```bash
    docker-compose exec web pytest
    ```

4.  **Acesse a aplicação:**
    Abra seu navegador e acesse `http://127.0.0.1:8000/`.

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.
