# Documentação do Projeto SALA

## 1. Introdução
O cenário SALA apresenta uma empresa de tecnologia em crescimento acelerado, mas com fragilidades operacionais ligadas à comunicação entre áreas, falta de automação, ausência de rastreabilidade, riscos de segurança e necessidade de escalabilidade. O projeto proposto resolve esses pontos por meio de um sistema integrado web.

## 2. Objetivo
Desenvolver um sistema web com front-end, back-end e banco de dados para integrar vendas, implementação, faturamento, suporte técnico e auditoria.

## 3. Escopo
- cadastro de clientes
- cadastro de contratos
- registro de vendas
- geração de ordens de serviço
- geração de faturas
- abertura de chamados
- controle de acesso por perfil
- logs de auditoria
- indicadores gerenciais

## 4. Requisitos Funcionais
- RF-01: permitir cadastro de usuários
- RF-02: permitir autenticação no sistema
- RF-03: permitir cadastro de clientes
- RF-04: permitir cadastro de contratos
- RF-05: registrar vendas
- RF-06: gerar ordem de serviço automaticamente após venda
- RF-07: gerar fatura automaticamente com base em contrato válido
- RF-08: permitir abertura de chamados técnicos
- RF-09: classificar chamados por severidade
- RF-10: classificar chamados por impacto
- RF-11: vincular chamados a módulos do ERP
- RF-12: registrar logs de auditoria
- RF-13: apresentar dashboard com indicadores
- RF-14: permitir gerenciamento de usuários e perfis

## 5. Requisitos Não Funcionais
- RNF-01: autenticação segura
- RNF-02: controle de acesso baseado em funções
- RNF-03: persistência confiável dos dados
- RNF-04: interface responsiva
- RNF-05: disponibilidade elevada
- RNF-06: suporte ao crescimento da base de clientes
- RNF-07: recuperação rápida em falhas
- RNF-08: rastreabilidade das ações críticas

## 6. Regras de Negócio
- RN-01: toda venda concluída deve gerar uma ordem de serviço
- RN-02: nenhuma fatura pode ser gerada sem contrato ativo
- RN-03: todo chamado deve possuir severidade e impacto
- RN-04: todo chamado deve estar vinculado a um módulo
- RN-05: alterações críticas devem ser registradas em log
- RN-06: dados sensíveis devem ser restritos por perfil
- RN-07: somente perfis autorizados podem gerenciar usuários

## 7. Atores
- Administrador
- Comercial
- Financeiro
- Suporte
- TI

## 8. Casos de Uso
- autenticar usuário
- cadastrar cliente
- cadastrar contrato
- registrar venda
- gerar ordem de serviço
- gerar fatura
- abrir chamado
- consultar dashboard
- gerenciar usuários
- consultar logs

## 9. MER
Entidades principais:
- Role
- User
- Client
- Contract
- Sale
- WorkOrder
- Invoice
- ERPModule
- Ticket
- AuditLog

## 10. DER textual
- Role 1:N User
- Client 1:N Contract
- Client 1:N Sale
- Contract 1:N Sale
- Sale 1:1 WorkOrder
- Contract 1:N Invoice
- Sale 1:N Invoice
- Client 1:N Ticket
- ERPModule 1:N Ticket
- User 1:N AuditLog

## 11. Dicionário resumido
### User
- id: identificador
- name: nome do usuário
- email: e-mail
- password: senha
- role_id: perfil

### Client
- id: identificador
- name: razão social / nome
- document: CNPJ ou documento
- email: contato
- phone: telefone
- address: endereço

### Contract
- id: identificador
- client_id: cliente
- title: título do contrato
- start_date: início
- end_date: fim
- total_value: valor
- status: situação

### Sale
- id: identificador
- client_id: cliente
- contract_id: contrato
- amount: valor
- status: status da venda
- sale_date: data

### Ticket
- id: identificador
- client_id: cliente
- module_id: módulo afetado
- title: resumo
- description: descrição
- severity: severidade
- impact: impacto
- status: situação

## 12. Arquitetura da solução
Arquitetura em 3 camadas:
1. Front-end em HTML, CSS e JavaScript
2. Back-end em Node.js com Express
3. Banco relacional SQLite

Fluxo principal:
Usuário -> Front-end -> API -> Banco de Dados

## 13. Justificativa tecnológica
A stack foi escolhida por ser simples para ambiente acadêmico, de fácil execução local e suficiente para demonstrar regras de negócio, integração entre camadas e persistência estruturada.

## 14. Backlog inicial
- Tela de login
- CRUD de clientes
- CRUD de contratos
- Registro de vendas
- Geração automática de ordem de serviço
- Geração automática de fatura
- Chamados técnicos
- Logs de auditoria
- Dashboard
- Perfis de acesso

## 15. Planejamento em sprints
### Sprint 1
- levantamento de requisitos
- modelagem de banco
- estrutura inicial do projeto

### Sprint 2
- autenticação
- cadastro de clientes
- cadastro de contratos

### Sprint 3
- vendas
- ordens de serviço
- faturas

### Sprint 4
- chamados
- auditoria
- dashboard

### Sprint 5
- testes
- ajustes finais
- documentação
- publicação no GitHub e LinkedIn

## 16. Testes realizados
- login com usuário válido e inválido
- cadastro de cliente
- cadastro de contrato
- registro de venda com geração automática de ordem e fatura
- abertura de chamado
- consulta de logs

## 17. Conclusão
O projeto atende às necessidades centrais do cenário SALA ao integrar áreas críticas da empresa, automatizar fluxos operacionais e fornecer mecanismos mínimos de segurança, rastreabilidade e controle.
