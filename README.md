# 📝 Minha Rotina - Gerenciador de Tarefas Pessoal

"Minha Rotina" é uma aplicação web completa para gerenciamento de tarefas, desenvolvida como um PWA (Progressive Web App) para oferecer uma experiência de usuário rica e moderna tanto no desktop quanto em dispositivos móveis. O projeto conta com um back-end robusto em Java com Spring Boot e um front-end dinâmico e interativo construído com HTML, CSS e JavaScript puros.

## ⚠️ Atenção

* **Banco de Dados:** A versão online do projeto utilizava um plano gratuito de hospedagem de banco de dados que não está mais ativo. Se você clonar e executar este projeto, ele funcionará perfeitamente, mas precisará que você configure sua própria instância de banco de dados (como PostgreSQL ou H2) no arquivo `application.properties`.
* **Chaves de API:** As chaves secretas (JWT, VAPID para notificações) estão expostas nos arquivos (`application.properties`, `script.js`) para fins de demonstração. Se você for utilizar este código em produção, **é crucial que você proteja essas chaves**, por exemplo, utilizando variáveis de ambiente.

## ✨ Funcionalidades Principais

* **Autenticação Segura de Usuários:** Sistema completo de registro e login com autenticação baseada em tokens JWT (JSON Web Token).
* **Gerenciamento Completo de Tarefas (CRUD):** Crie, leia, atualize e exclua tarefas com informações detalhadas como título, descrição, data, horário, categoria e prioridade.
* **Notificações Push em Tempo Real:** Receba lembretes de tarefas diretamente no seu dispositivo (desktop ou móvel) 5 minutos antes, na hora exata e 5 minutos após o vencimento da tarefa.
* **Tarefas Recorrentes (Rotinas):** Crie tarefas que se repetem diariamente, ideais para construir hábitos. Elas são reativadas automaticamente todos os dias à meia-noite.
* **Perfil de Usuário Personalizável:** Edite seu nome, idade e adicione uma foto de perfil, que é armazenada como uma string Base64 no banco de dados.
* **Dashboard Interativo:**
    * Visualize estatísticas de tarefas (Total, Concluídas, Pendentes, Atrasadas).
    * Filtre tarefas por período e por categoria.
    * Widget de clima e relógio que detecta a localização do usuário.
    * Cronômetro integrado para gerenciamento de tempo (Técnica Pomodoro, etc).
* **Progressive Web App (PWA):** Instale a aplicação diretamente no seu computador ou celular para uma experiência semelhante a um aplicativo nativo, com suporte a cache offline para recursos essenciais.
* **Design Moderno e Responsivo:** Interface com tema claro e escuro, totalmente adaptável a diferentes tamanhos de tela.

## 🛠️ Tecnologias Utilizadas

* **Back-end:**
    * Java 17
    * Spring Boot 3
    * Spring Security (com Autenticação JWT)
    * Spring Data JPA (Hibernate)
    * PostgreSQL / H2 Database
    * Maven
* **Front-end:**
    * HTML5
    * CSS3
    * JavaScript (puro, sem frameworks)
    * Progressive Web App (PWA) com Service Worker
* **Notificações:**
    * Web Push Protocol (com biblioteca `web-push`)
* **Deploy:**
    * Docker

## 🚀 Como Executar o Projeto Localmente

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
    cd seu-repositorio
    ```

2.  **Configure o Banco de Dados:**
    * Abra o arquivo `src/main/resources/application.properties`.
    * Comente ou remova as linhas do PostgreSQL.
    * Para usar um banco de dados em memória (H2), adicione as seguintes linhas:
        ```properties
        spring.datasource.url=jdbc:h2:mem:testdb
        spring.datasource.driverClassName=org.h2.Driver
        spring.datasource.username=sa
        spring.datasource.password=password
        spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
        spring.h2.console.enabled=true
        ```

3.  **Atualize as Chaves (Opcional, mas recomendado):**
    * No mesmo arquivo `application.properties`, você pode gerar novas chaves `jwt.secret` e VAPID (em [vapidkeys.com](https://vapidkeys.com/)) para maior segurança.
    * Se gerar uma nova chave VAPID pública, atualize-a também no arquivo `src/main/resources/static/script.js`.

4.  **Execute a aplicação com Maven:**
    ```bash
    ./mvnw spring-boot:run
    ```

5.  **Acesse a aplicação:**
    Abra seu navegador e acesse `http://localhost:8080`. Se configurou o H2, o console do banco de dados estará disponível em `http://localhost:8080/h2-console`.
