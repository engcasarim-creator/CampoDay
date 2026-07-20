# CampoDay

# Documento de Arquitetura de Software

Versão: 1.0

---

# 1. Objetivo

Este documento descreve a arquitetura técnica da plataforma CampoDay.

Seu objetivo é definir os padrões de desenvolvimento que deverão ser seguidos durante todo o projeto.

---

# 2. Arquitetura Geral

A plataforma será composta por quatro aplicações independentes.

```
                   CampoDay

        ┌───────────────────────────┐
        │                           │
        │      Flutter Mobile       │
        │                           │
        └─────────────┬─────────────┘
                      │
                HTTPS / JSON
                      │
                      ▼
        ┌───────────────────────────┐
        │                           │
        │      Laravel API          │
        │                           │
        └─────────────┬─────────────┘
                      │
                Eloquent ORM
                      │
                      ▼
        ┌───────────────────────────┐
        │       PostgreSQL          │
        └───────────────────────────┘

                      ▲

        ┌───────────────────────────┐
        │                           │
        │     Painel Web Laravel    │
        │                           │
        └───────────────────────────┘
```

---

# 3. Tecnologias

## Backend

Laravel 12

PHP 8.4

Composer

---

## Banco de Dados

PostgreSQL 17

---

## Mobile

Flutter

Dart

---

## Painel Web

Laravel Blade

Livewire

AlpineJS

---

## Infraestrutura

Docker

Docker Compose

GitHub

GitHub Actions

Nginx

Redis

---

# 4. Arquitetura em Camadas

A API será organizada em camadas.

```
Controller

↓

Service

↓

Repository

↓

Model

↓

Database
```

Cada camada possui responsabilidade única.

---

# 5. Organização do Projeto

```
backend/

app/

    Domain/

    Application/

    Infrastructure/

    Http/

    Models/

    Services/

    Repositories/

routes/

database/

tests/
```

---

# 6. Estrutura dos Módulos

Cada módulo possuirá sua própria estrutura.

Exemplo:

```
Evento

Controller

Service

Repository

Model

Request

Policy

Resource
```

---

# 7. Organização dos Módulos

```
Identidade

Eventos

Participantes

Empresas

Infraestrutura

Materiais

Checklist

Cronograma

Fotos

Relatórios
```

Cada módulo será independente.

---

# 8. API

A API será RESTful.

Padrões:

GET

POST

PUT

PATCH

DELETE

Todas as respostas utilizarão JSON.

---

# 9. Versionamento

Toda API será versionada.

```
/api/v1
```

No futuro:

```
/api/v2
```

---

# 10. Autenticação

Laravel Sanctum.

Autenticação baseada em Token.

---

# 11. Autorização

Policies

Gates

Roles

Permissões

---

# 12. Banco

ORM

Laravel Eloquent

Migrations

Seeders

Factories

Soft Deletes

---

# 13. Auditoria

Todas as alterações importantes deverão ser registradas.

Exemplo:

Usuário

Data

Hora

Operação

IP

Dispositivo

---

# 14. Upload de Arquivos

Fotos

PDF

Documentos

Serão armazenados utilizando Storage do Laravel.

---

# 15. Logs

Logs separados por ambiente.

development

staging

production

---

# 16. Testes

Testes Unitários

Testes de Integração

Testes de API

---

# 17. Segurança

Hash de senha

HTTPS obrigatório

Proteção CSRF

Rate Limit

Validação de Requests

Sanitização

---

# 18. Convenções

Tabela

snake_case

Campo

snake_case

Classe

PascalCase

Métodos

camelCase

---

# 19. Fluxo de Requisição

Flutter

↓

API

↓

Controller

↓

Request

↓

Service

↓

Repository

↓

Model

↓

PostgreSQL

↓

Repository

↓

Service

↓

Resource

↓

JSON

↓

Flutter

---

# 20. Padrões Utilizados

SOLID

Clean Code

Repository Pattern

Service Layer

REST

MVC

DDD (parcial)

PSR-12

Conventional Commits

---

# 21. Escalabilidade

A arquitetura deverá permitir:

- Multiempresa (Multi-tenant)
- Múltiplos tipos de eventos
- Integração com ERPs
- Aplicativo Offline
- Dashboard Web
- API Pública
- Integração com IA
- Integração com WhatsApp
- Integração com QR Code

---

# 22. Roadmap Técnico

Sprint 1

Arquitetura

Banco

API

---

Sprint 2

Usuários

Autenticação

Eventos

---

Sprint 3

Checklist

Cronograma

Estações

---

Sprint 4

Participantes

Grupos

Check-in

---

Sprint 5

Infraestrutura

Materiais

Empresas

---

Sprint 6

Fotos

Relatórios

Dashboard

---

Sprint 7

Modo Offline

Sincronização

Notificações

IA

---

# 23. Princípios do Projeto

O CampoDay deverá seguir os seguintes princípios:

- Simplicidade
- Escalabilidade
- Alta coesão
- Baixo acoplamento
- Código limpo
- Documentação completa
- Testabilidade
- Manutenibilidade