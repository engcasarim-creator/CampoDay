# CampoDay

# Modelo Lógico do Banco de Dados

## Objetivo

Este documento define a estrutura lógica do banco de dados da plataforma CampoDay.

São apresentados:

- Entidades
- Campos
- Chaves Primárias
- Chaves Estrangeiras
- Relacionamentos
- Restrições

---

# Convenções

Todos os nomes serão escritos em inglês.

Exemplo:

users
events
companies
participants

Isso facilita futuras integrações e segue o padrão utilizado pelo Laravel.

---

# 1. users

Representa os usuários do sistema.

| Campo | Tipo | Obrigatório |
|--------|------|-------------|
| id | BIGINT | Sim |
| name | VARCHAR(150) | Sim |
| email | VARCHAR(150) | Sim |
| password | VARCHAR(255) | Sim |
| phone | VARCHAR(20) | Não |
| role | ENUM | Sim |
| active | BOOLEAN | Sim |
| created_at | TIMESTAMP | Sim |
| updated_at | TIMESTAMP | Sim |
| deleted_at | TIMESTAMP | Não |

Relacionamentos

- 1 usuário pode coordenar vários eventos.

---

# 2. event_types

Tipos de evento.

Campos

- id
- name
- description

Exemplos

- Dia de Campo
- Treinamento
- Demonstração
- Vitrine Tecnológica

---

# 3. events

Campos

- id
- title
- description
- event_type_id
- coordinator_id
- location_id
- start_date
- end_date
- expected_participants
- status
- observations
- created_at
- updated_at
- deleted_at

Relacionamentos

- pertence a event_types
- pertence a users
- pertence a locations

---

# 4. locations

Campos

- id
- name
- farm_name
- address
- city
- state
- latitude
- longitude

---

# 5. companies

Campos

- id
- corporate_name
- trade_name
- cnpj
- phone
- email
- website

---

# 6. representatives

RTVs

Campos

- id
- company_id
- name
- phone
- email

---

# 7. event_companies

Tabela Pivot

Relaciona empresas aos eventos.

Campos

- event_id
- company_id

Relacionamento

N : N

---

# 8. stations

Campos

- id
- event_id
- company_id
- responsible_user_id
- title
- theme
- duration_minutes
- order

---

# 9. groups

Campos

- id
- event_id
- name
- color
- order

---

# 10. participants

Campos

- id
- name
- cpf
- phone
- email
- city
- state

---

# 11. registrations

Tabela de inscrição.

Campos

- id
- participant_id
- event_id
- group_id
- status

Status

- Confirmado
- Lista de Espera
- Cancelado

---

# 12. checkins

Campos

- id
- registration_id
- checkin_at
- checkout_at

---

# 13. templates

Modelo padrão de evento.

Campos

- id
- name
- culture
- description

---

# 14. checklists

Campos

- id
- event_id
- template_id
- title

---

# 15. checklist_tasks

Campos

- id
- checklist_id
- title
- description
- responsible_user_id
- due_date
- status

---

# 16. infrastructures

Campos

- id
- event_id
- type
- description
- quantity
- supplier
- responsible_user_id
- status

---

# 17. materials

Campos

- id
- event_id
- description
- quantity
- unit

---

# 18. schedule_items

Cronograma

Campos

- id
- event_id
- start_time
- end_time
- title
- station_id

---

# 19. photos

Campos

- id
- event_id
- station_id
- file_name
- caption
- uploaded_by

---

# 20. reports

Campos

- id
- event_id
- generated_by
- pdf_path
- created_at

---

# 21. audit_logs

Histórico das alterações.

Campos

- id
- user_id
- table_name
- record_id
- action
- created_at

---

# Relacionamentos

users

↓

events

↓

stations

↓

schedule

↓

photos

--------------------------------

events

↓

registrations

↓

participants

↓

checkins

--------------------------------

events

↓

checklists

↓

tasks

--------------------------------

events

↓

companies

↓

representatives