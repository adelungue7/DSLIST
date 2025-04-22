<div align="center">

# 🎮 DSList API 🎮

[![Java](https://img.shields.io/badge/Java-17+-orange.svg)](https://www.java.com)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x.x-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![Maven](https://img.shields.io/badge/Maven-3.8+-blue.svg)](https://maven.apache.org/)

</div>

> Projeto de um sistema backend para agregação e organização de listas de jogos, desenvolvido como parte do capítulo "Sistema de Agregação de Jogos" do curso **Java Spring Professional** da [DevSuperior](https://devsuperior.com.br/) 🎓.

---

## 📝 Sobre o Projeto

DSList é uma API REST construída com **Spring Boot** que permite gerenciar uma coleção de jogos e organizá-los em listas personalizadas. A aplicação permite consultar jogos, listas, os jogos contidos em cada lista e reordenar os jogos dentro de uma lista específica.

---

## 💻 Tecnologias Utilizadas

* ☕ **Linguagem:** Java 17+
* 🍃 **Framework:** Spring Boot 3
* 🕸️ **Módulos Spring:** Spring Web, Spring Data JPA
* 🛠️ **Gerenciador de Dependências:** Maven
* 💾 **Banco de Dados:**
    * H2 (Ambiente de Teste/Desenvolvimento - Padrão)
    * PostgreSQL (Configurado para Produção)
* ✅ **Validação:** Jakarta Bean Validation

---

## ✨ Funcionalidades Principais

* 🎮 **Listar** todos os jogos cadastrados.
* 🔍 **Buscar** detalhes de um jogo específico pelo ID.
* 🧾 **Listar** todas as listas de jogos criadas.
* 📑 **Consultar** os jogos pertencentes a uma lista específica (ordenados!).
* 🔄 **Reordenar** jogos dentro de uma lista.

---

## 🚀 Como Executar Localmente

### Pré-requisitos Mínimos

* ♨️ JDK 17 ou superior instalado.
* 📦 Maven instalado.
* 🐙 Git instalado.
* (Opcional) Um cliente de API como Postman ou Insomnia.
* 🐘 (Opcional) PostgreSQL rodando (se for usar o perfil `prod`).

### Passos para Rodar

1.  **Clone o repositório:**
    ```bash
    git clone [https://github.com/adelungue7/DSLIST.git](https://github.com/adelungue7/DSLIST.git)
    ```
2.  **Entre na pasta do projeto:**
    ```bash
    cd DSLIST
    ```
3.  **Execute a aplicação (usando perfil `test` com H2):**
    ```bash
    mvn spring-boot:run
    ```

### 🌍 Acessando a Aplicação

Após a inicialização, a API estará tinindo em `http://localhost:8080` ✨.

O perfil `test` (padrão) usa o banco **H2** em memória e carrega dados iniciais de `src/main/resources/import.sql`.

---

## ⚙️ Configuração do Banco de Dados

### H2 (Padrão - Perfil `test`)
* Ativado por padrão com `mvn spring-boot:run`.
* Configurações: `src/main/resources/application.properties`.
* Console H2: `http://localhost:8080/h2-console` (verifique credenciais e URL JDBC no `.properties`).

### PostgreSQL (Perfil `prod`)
* Configurações comentadas em `src/main/resources/application.properties`.
* **Para ativar:**
    1.  Tenha um servidor PostgreSQL ativo e um banco de dados criado.
    2.  Ajuste as propriedades `spring.datasource.*` no `application.properties` (descomente e configure).
    3.  Comente ou remova as propriedades do H2.
    4.  Execute com o perfil `prod`:
        ```bash
        mvn spring-boot:run -Dspring-boot.run.profiles=prod
        ```
* ⚠️ **Atenção:** O `import.sql` é mais voltado ao H2. No perfil `prod`, o schema do banco (`CREATE TABLE`, etc.) é gerenciado pela propriedade `spring.jpa.hibernate.ddl-auto` (geralmente `update` ou `validate` em produção) ou por ferramentas de *migration* (não usadas aqui).

---

## 🔗 Endpoints da API (Exemplos)

* `GET /games`
    * Lista simplificada de todos os jogos.
    * *Exemplo:* `[{"id": 1, "title": "Mass Effect Trilogy", ...}, ...]`

* `GET /games/{id}`
    * Detalhes completos de um jogo.
    * *Exemplo (`/games/1`):* `{"id": 1, "title": "Mass Effect Trilogy", "score": 4.8, ...}`

* `GET /lists`
    * Lista todas as "prateleiras" de jogos.
    * *Exemplo:* `[{"id": 1, "name": "Aventura e RPG"}, ...]`

* `GET /lists/{listId}/games`
    * Lista os jogos de uma "prateleira" específica.
    * *Exemplo (`/lists/1/games`):* `[{"id": 1, "title": "Mass Effect Trilogy", ...}, ...]`

* `POST /lists/{listId}/replacement`
    * Move um jogo dentro da lista.
    * *Corpo da Requisição (JSON):*
        ```json
        {
            "sourceIndex": 2,      // Posição atual (base 0)
            "destinationIndex": 0  // Nova posição (base 0)
        }
        ```
    * *Resposta:* `204 No Content` (Sucesso!)

---

## 👤 Autor

Feito com ❤️ por **Rafael Adelungue**

* [![GitHub](https://img.shields.io/badge/GitHub-adelungue7-181717?style=for-the-badge&logo=github)](https://github.com/adelungue7)
* [![LinkedIn](https://img.shields.io/badge/LinkedIn-Rafael%20Adelungue-0077B5?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/adelungue-rafael/)

---

## 🙏 Agradecimentos

* Um agradecimento especial à **[DevSuperior](https://devsuperior.com.br/)** pelo curso e pela base deste projeto!

---
