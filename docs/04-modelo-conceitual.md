# CampoDay

# Modelo Conceitual

## Objetivo

O Modelo Conceitual descreve os principais objetos do domínio do sistema CampoDay e os relacionamentos existentes entre eles.

Nesta etapa ainda não são definidos tipos de dados, chaves primárias ou tecnologia de banco de dados.

O objetivo é compreender o negócio.

---

# Visão Geral

O sistema é centrado na entidade **Evento**.

Todos os demais módulos possuem relacionamento direto ou indireto com um evento.

```
                Evento
                   │
 ┌─────────────────┼────────────────────┐
 │                 │                    │
 ▼                 ▼                    ▼
Usuários      Participantes       Empresas
 │                 │                    │
 ▼                 ▼                    ▼
Equipe         Check-in             RTV
 │
 ▼
Checklist
 │
 ▼
Tarefas
 │
 ▼
Infraestrutura
 │
 ▼
Fotos
```

---

# Entidades

## Usuário

Representa qualquer pessoa autenticada no sistema.

Responsabilidades:

- acessar o sistema
- criar eventos
- editar eventos
- executar tarefas
- gerar relatórios

---

## Evento

Representa um evento técnico realizado pela cooperativa.

Exemplos:

- Dia de Campo
- Vitrine Tecnológica
- Treinamento
- Demonstração de Máquinas
- Reunião Técnica

É a principal entidade do sistema.

---

## Local

Representa onde o evento será realizado.

Pode ser:

- Fazenda
- Unidade da Cooperativa
- Centro de Eventos
- Campo Experimental

---

## Empresa Parceira

Representa empresas patrocinadoras ou apoiadoras.

Exemplos:

- Syngenta
- Bayer
- BASF
- Corteva
- FMC

---

## RTV

Representa o representante técnico da empresa.

Cada RTV pertence a uma empresa.

---

## Participante

Representa produtores, cooperados ou visitantes.

---

## Grupo

Representa a divisão dos participantes durante o evento.

Exemplos:

- Grupo Azul
- Grupo Verde
- Grupo Vermelho
- Grupo Amarelo

---

## Estação Técnica

Representa um ponto de parada do evento.

Cada estação possui:

- tema
- responsável
- empresa parceira
- tempo de apresentação

---

## Checklist

Lista de atividades necessárias para organização do evento.

---

## Tarefa

Cada item pertencente ao checklist.

Exemplos:

- reservar tendas
- contratar buffet
- imprimir placas
- confirmar ônibus

---

## Material

Materiais utilizados durante o evento.

Exemplos:

- mesas
- cadeiras
- banner
- caixa de som
- projetor

---

## Infraestrutura

Itens estruturais necessários.

Exemplos:

- tendas
- banheiros
- estacionamento
- gerador
- palco

---

## Cronograma

Representa toda programação do evento.

---

## Check-in

Representa o registro de chegada dos participantes.

---

## Foto

Imagens registradas durante o evento.

---

## Relatório

Documento final contendo todas as informações do evento.

---

# Relacionamentos

## Usuário

Um usuário pode organizar vários eventos.

Relacionamento:

```
Usuário (1) -------- (N) Evento
```

---

## Evento

Um evento possui apenas um coordenador.

```
Evento (N) -------- (1) Usuário
```

---

## Evento x Participante

Um evento possui vários participantes.

Um participante poderá participar de vários eventos.

```
Evento (N) -------- (N) Participante
```

---

## Evento x Empresa

Um evento poderá possuir diversas empresas parceiras.

Uma empresa poderá participar de diversos eventos.

```
Evento (N) -------- (N) Empresa
```

---

## Empresa x RTV

Uma empresa possui vários RTVs.

```
Empresa (1) -------- (N) RTV
```

---

## Evento x Estação

Cada evento possui diversas estações.

```
Evento (1) -------- (N) Estação
```

---

## Estação x Empresa

Uma estação poderá ser patrocinada por uma empresa.

```
Empresa (1) -------- (N) Estação
```

---

## Evento x Grupo

Cada evento possui vários grupos.

```
Evento (1) -------- (N) Grupo
```

---

## Grupo x Participante

Um grupo possui vários participantes.

```
Grupo (1) -------- (N) Participante
```

---

## Evento x Checklist

Cada evento possui um checklist.

```
Evento (1) -------- (1) Checklist
```

---

## Checklist x Tarefa

Cada checklist possui várias tarefas.

```
Checklist (1) -------- (N) Tarefa
```

---

## Evento x Cronograma

Cada evento possui um cronograma.

```
Evento (1) -------- (1) Cronograma
```

---

## Evento x Foto

Cada evento possui várias fotos.

```
Evento (1) -------- (N) Foto
```

---

## Evento x Relatório

Cada evento poderá gerar um relatório final.

```
Evento (1) -------- (1) Relatório
```

---

# Ciclo de Vida do Evento

Todo evento passa pelas seguintes fases:

```
Planejamento

↓

Organização

↓

Preparação

↓

Execução

↓

Encerramento

↓

Pós-evento
```

Cada fase possui tarefas específicas.

---

# Objetivo Final

O Modelo Conceitual servirá como base para:

- Modelo Lógico
- Modelo Físico
- Banco de Dados
- API REST
- Backend Laravel
- Aplicativo Flutter