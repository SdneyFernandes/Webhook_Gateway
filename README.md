# 🔗 Webhook Gateway - Event Dispatcher API

Um **gateway de entrada de eventos** (webhooks) que recebe requisições HTTP de sistemas externos, filtra com base em headers e despacha os dados para **tópicos Kafka** específicos de forma assíncrona, segura, observável e escalável.

---

## 🎯 Objetivo

Oferecer uma API simples e performática que centraliza o recebimento de webhooks, aplicando **boas práticas de arquitetura, mensageria, segurança, testes e monitoramento**.

---

## 🧠 Caso de uso real

Sistemas modernos recebem dados externos o tempo todo (ex: Stripe, GitHub, bancos). Este gateway permite:

- Ter **um único ponto de entrada de eventos**
- Aplicar **regras de roteamento**
- **Distribuir eventos via Kafka** para microserviços corretos
- Adicionar **observabilidade, segurança e testes**

---

## 🧱 Tecnologias aplicadas

| Categoria       | Tecnologias                                                        |
|-----------------|---------------------------------------------------------------------|
| Backend         | Java 21, Spring Boot, Spring Web, Spring Kafka                     |
| Mensageria      | Apache Kafka                                                       |
| Segurança       | Spring Security (JWT)                                              |
| Observabilidade | Micrometer, Prometheus, Grafana, Spring Actuator                   |
| Testes          | JUnit 5, Testcontainers, Mockito                                   |
| DevOps          | Docker, Docker Compose, GitHub Actions (CI/CD)                    |
| Arquitetura     | Clean Architecture, SOLID, Separação de Camadas                    |

---

## 🗺️ Diagrama de Arquitetura

```mermaid
graph TD
    Client[Serviço Externo (ex: Stripe)] -->|Webhook| API[Webhook Gateway API]
    API -->|Roteamento baseado em headers| Kafka[Apache Kafka]
    Kafka -->|Mensagem| Consumer1[Microserviço 1]
    Kafka -->|Mensagem| Consumer2[Microserviço 2]
    API --> Prometheus
    Prometheus --> Grafana
    API -->|Autenticação| SpringSecurity[JWT Security]
````

---

## 🚀 Como rodar localmente

```bash
# 1. Clone o projeto
git clone https://github.com/SdneyFernandes/webhook-gateway.git
cd webhook-gateway

# 2. Suba os containers
docker-compose up -d

# 3. Execute a aplicação local (Java)
./mvnw spring-boot:run
```

Acesse:

* `http://localhost:8080/webhook` → Endpoint que recebe eventos
* `http://localhost:9090` → Prometheus
* `http://localhost:3000` → Grafana (admin/admin)

---

## 🧪 Testes

* `WebhookControllerTest`: Testes unitários da API
* `KafkaIntegrationTest`: Testes com Kafka real via Testcontainers

---

## 🛡️ Segurança

* Endpoint `/webhook` protegido por **JWT**
* Geração e verificação de tokens
* Exemplo de uso via Postman incluso

---

## 📈 Observabilidade

* `Micrometer` + `Prometheus` expõe métricas HTTP/Kafka
* `Grafana` importando dashboard pronto
* Tracing distribuído pode ser ativado com Jaeger/OpenTelemetry

---

## 📌 Futuras melhorias

* UI administrativa com Spring Boot Admin
* Suporte a múltiplos brokers Kafka
* Configuração externa de regras de roteamento

---

## 🧑‍💻 Autor

Feito por \[Seu Nome] — Desenvolvedor Backend Java com foco em aplicações reais, escaláveis e bem arquitetadas.

---
