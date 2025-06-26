# 🔐 API de Autenticação e Autorização com JWT (AV2)

Este projeto faz parte da avaliação AV2 e foca na criação de uma API segura com autenticação via JWT, testes automatizados, monitoramento com Prometheus e Actuator, e deploy com Docker.

---

## 📦 Dependências do Projeto

Adicione ao `pom.xml` as seguintes dependências:

- **spring-boot-starter-web** – Para construção de APIs REST.
- **spring-boot-starter-security** – Autenticação e controle de acesso.
- **spring-boot-starter-oauth2-resource-server** – Validação de tokens JWT.
- **spring-boot-starter-data-jpa** – Persistência com JPA.
- **h2** – Banco em memória para testes.
- **springdoc-openapi-ui** – Geração automática da documentação via Swagger UI.
- **spring-boot-devtools** – Ferramentas para desenvolvimento.
- **lombok** – Reduz código repetitivo (getters/setters, etc).
- **spring-boot-starter-test** – JUnit 5 e Mockito.
- **spring-boot-starter-actuator** – Monitoramento da API.
- **micrometer-registry-prometheus** – Integração com Prometheus.

---

## ⚙️ Configuração do Ambiente (`application.yml`)

- Defina as propriedades do banco de dados.
- Configure o Spring Security e a chave secreta do JWT.
- Ative o Actuator com os endpoints `/actuator/health`, `/actuator/metrics`, etc.

---

## 🛡️ Implementação da Autenticação

- Crie os endpoints:  
  - `POST /auth/login`  
  - `POST /auth/register`  
- Geração e validação de tokens JWT.
- Proteja rotas com filtros do Spring Security.

---

## 🔑 Proteção dos Endpoints CRUD

- Integre a autenticação JWT com os endpoints existentes.
- Use regras de autorização para separar acessos de usuários e admins.

---

## ✅ Testes Unitários

- Escreva testes para os serviços de autenticação.
- Utilize JUnit 5 e Mockito para criar mocks e validar fluxos.

---

## 📈 Testes de Carga com JMeter

1. Instale o JMeter e execute o programa.
2. Configure um **Thread Group** com 200 usuários, 20s de ramp-up e 10 loops.
3. Adicione um **HTTP Request** com:
   - Método: POST  
   - Path: `/auth/login`  
   - Body: JSON com usuário/senha
4. Visualize os resultados com o **Summary Report**.

---

## 📖 Documentação da API

- Use o SpringDoc para gerar documentação OpenAPI automaticamente.
- Acesse o Swagger em:  
  👉 `http://localhost:8080/swagger-ui.html`

---

## 🩺 Monitoramento

- Configure o **Spring Boot Actuator** para expor métricas e saúde.
- Use o endpoint `/actuator/prometheus` para integração com Prometheus.
- Crie dashboards no **Grafana** para visualização das métricas.

---

## 🚚 Deploy com Docker

1. Crie um `Dockerfile` para o projeto.
2. Construa a imagem com:  
   ```bash
   docker build -t jwt-api .
Rode o container com:

bash
Copiar
Editar
docker run -p 8080:8080 jwt-api
