# CampoDay

# Regras de Negócio

Este documento define as regras que governam o funcionamento da plataforma CampoDay.

---

# RN001 - Usuários

Todo usuário deve possuir um perfil de acesso.

Perfis disponíveis:

- Administrador
- Coordenador
- Agrônomo
- Equipe de Apoio

Cada perfil visualizará apenas as funcionalidades permitidas.

---

# RN002 - Login

Somente usuários ativos poderão acessar o sistema.

---

# RN003 - Eventos

Todo evento deverá possuir obrigatoriamente:

- Nome
- Tipo
- Data
- Horário
- Local
- Responsável

Não será permitido publicar um evento incompleto.

---

# RN004 - Situação do Evento

Todo evento possuirá um status.

Status possíveis:

- Planejamento
- Organização
- Preparação
- Em execução
- Encerrado
- Cancelado

---

# RN005 - Estações Técnicas

Todo evento deverá possuir pelo menos uma estação técnica antes de ser iniciado.

---

# RN006 - Responsável pela Estação

Cada estação deverá possuir um responsável técnico.

---

# RN007 - Tempo da Estação

O tempo mínimo recomendado será de 10 minutos.

O tempo máximo recomendado será de 40 minutos.

---

# RN008 - Participantes

O participante poderá estar inscrito apenas uma vez no mesmo evento.

---

# RN009 - Check-in

Cada participante poderá realizar apenas um check-in por evento.

---

# RN010 - Check-out

O check-out somente poderá ser realizado após o check-in.

---

# RN011 - Grupos

Todo participante deverá pertencer a apenas um grupo.

---

# RN012 - Rotação

Todos os grupos deverão visitar todas as estações.

Nenhuma estação poderá ficar sem receber um grupo.

---

# RN013 - Empresas Parceiras

Uma empresa poderá participar de diversos eventos.

Um evento poderá possuir diversas empresas parceiras.

Relacionamento:

N : N

---

# RN014 - RTV

Cada RTV deverá estar vinculado a uma empresa.

---

# RN015 - Produtos

Um produto poderá estar presente em diversas estações.

---

# RN016 - Infraestrutura

Toda infraestrutura deverá possuir um responsável pela montagem.

---

# RN017 - Checklist

O sistema deverá gerar automaticamente um checklist padrão ao criar um novo evento.

O usuário poderá personalizar esse checklist.

---

# RN018 - Tarefas

Uma tarefa poderá possuir os seguintes estados:

- Pendente
- Em andamento
- Concluída
- Cancelada

---

# RN019 - Fotos

Toda foto deverá estar vinculada a um evento.

Opcionalmente poderá ser vinculada a:

- estação
- participante
- empresa

---

# RN020 - Relatórios

O relatório somente poderá ser gerado após o encerramento do evento.

---

# RN021 - Pós-evento

O evento somente poderá ser finalizado após:

- desmontagem concluída
- limpeza concluída
- checklist final concluído

---

# RN022 - Exclusão

Eventos encerrados não poderão ser excluídos.

Apenas cancelados.

---

# RN023 - Auditoria

Toda alteração deverá registrar:

- usuário
- data
- hora
- operação realizada

---

# RN024 - Offline

O aplicativo deverá permitir registrar informações mesmo sem conexão.

Os dados serão sincronizados quando houver internet.

---

# RN025 - Permissões

Cada perfil visualizará apenas os módulos autorizados.

Administrador:

- acesso total

Coordenador:

- gerenciamento dos eventos

Agrônomo:

- gerenciamento operacional

Equipe de Apoio:

- apenas tarefas atribuídas

---

# RN026 - Capacidade do Evento

O número de participantes inscritos não poderá ultrapassar a capacidade máxima definida para o evento.

---

# RN027 - Histórico

Nenhuma informação operacional deverá ser apagada definitivamente.

Sempre que possível, utilizar exclusão lógica (Soft Delete).

---

# RN028 - Notificações

O sistema deverá alertar quando houver tarefas atrasadas.

---

# RN029 - Segurança

Todas as operações críticas deverão exigir usuário autenticado.

---

# RN030 - Integridade

O sistema deverá impedir registros órfãos no banco de dados.