# Conexão CS

<div align="center">

![Status](https://img.shields.io/badge/Status-Em%20Produção-success?style=for-the-badge)
![Melhoria](https://img.shields.io/badge/Melhoria-Contínua-blue?style=for-the-badge)
![Versão](https://img.shields.io/badge/Versão-2.0-purple?style=for-the-badge)

**Portal web completo para centralizar e otimizar as operações do setor de Customer Success, transformando processos manuais e descentralizados em fluxos de trabalho digitais, eficientes e rastreáveis.**

*Este é um projeto interno e de código-fonte fechado. Este repositório serve como uma vitrine pública ("case study") para demonstrar sua arquitetura, funcionalidades e o impacto de negócio que ele gerou.*

[Funcionalidades](#principais-funcionalidades) •
[Arquitetura](#arquitetura-técnica) •
[Stack](#stack-de-tecnologias) •
[Resultados](#resultados-e-impacto)

</div>

---

## Preview do Sistema

<div align="center">

![Conexão CS - Demo](./assets/Conexao_CS.gif)

</div>

---

## Índice

- [Contexto e Problema](#contexto-e-problema)
- [Solução Proposta](#solução-proposta)
- [Principais Funcionalidades](#principais-funcionalidades)
- [Arquitetura Técnica](#arquitetura-técnica)
- [Stack de Tecnologias](#stack-de-tecnologias)
- [Integrações](#integrações)
- [Resultados e Impacto](#resultados-e-impacto)

---

## Contexto e Problema

O setor de Customer Success da empresa lidava com um alto volume de processos críticos para a satisfação do cliente e para a saúde financeira da operação. Processos como gestão de garantias, trocas, devoluções, cancelamentos e controle de peças defeituosas eram gerenciados de forma descentralizada, utilizando planilhas e comunicação informal.

### Principais Dores Identificadas

| Problema | Impacto |
|----------|---------|
| **Falta de visibilidade** | Impossível rastrear o status de uma solicitação em tempo real |
| **Ineficiência operacional** | Processos manuais e repetitivos consumiam tempo valioso da equipe |
| **Perda de informação** | Dados importantes se perdiam entre diferentes plataformas |
| **Riscos financeiros** | Falta de controle rigoroso sobre vales-crédito, refugos e contas a pagar |
| **Retrabalho constante** | Ausência de automações gerava duplicidade de esforços |

---

## Solução Proposta

O **Conexão CS** foi desenvolvido do zero como uma solução web centralizada para atacar diretamente essas dores. O sistema unifica todos os fluxos de trabalho do setor em uma única plataforma, servindo como a **fonte única de verdade** para todas as operações de pós-venda.

### Diferenciais da Solução

- **Centralização Total** - Todos os processos em um único lugar
- **Automação Inteligente** - Redução de tarefas manuais repetitivas
- **Rastreabilidade Completa** - Histórico de todas as ações
- **Integração com ERP** - Comunicação direta com Tiny ERP
- **Sistema de Notificações** - Alertas em tempo real para a equipe
- **Controle de Permissões** - Acesso baseado em cargos e funções

---

## Principais Funcionalidades

### Módulo de Garantias e Trocas
Orquestra todo o fluxo de solicitação de garantia e troca de produtos.

**Recursos:**
- Cadastro completo com dados do cliente (integração BigQuery)
- Busca automática de clientes por CPF/CNPJ
- Gestão de múltiplos itens por solicitação
- Sistema de marcadores automáticos (GR1, GR2, TR1, etc.)
- Controle de logística reversa
- Geração automática de pedidos no Tiny ERP
- Fluxo de conferência com notificações
- Suporte a endereço de entrega diferente
- Exportação para Excel com filtros

**Status do Fluxo:**
```
Pendente → Aguardando Logística Reversa → Gerado → Conferido → Cancelado
```

---

### Módulo de Triagem
Gerencia o recebimento e análise de produtos devolvidos.

**Recursos:**
- Registro de triagem com destino da peça
- Vinculação automática com garantias existentes
- Criação automática de processos de recurso
- Controle de prazos com alertas visuais
- Rastreamento por canal de venda
- Motivos de devolução categorizados

**Destinos Possíveis:**
- Estoque
- Refugo
- Em Transporte
- Técnico

---

### Módulo de Contas a Pagar
Controla os custos associados a cada processo de pós-venda.

**Recursos:**
- Cadastro de contas com múltiplas formas de pagamento (PIX, Boleto)
- Integração direta com Tiny ERP para geração de contas
- Fluxo de aprovação: Pendente → Gerado → Conferido → Pago
- Sistema de conferência com notificações para o financeiro
- Controle de refugo vinculado
- Histórico completo de pagamentos
- Exportação para Excel

**Workflow de Aprovação:**
```
Responsável CS → Conferente → Financeiro → Pago
```

---

### Módulo de Vale-Crédito
Administra a geração, utilização e validade de créditos concedidos aos clientes.

**Recursos:**
- Cadastro de vales com valor original e saldo atual
- Sistema de solicitação de uso por vendedores
- Aprovação/Recusa pelo time financeiro
- Consulta de saldo do cliente via API
- Histórico de utilizações
- Notificações automáticas para todas as partes
- Controle de status: Em Aberto, Utilizado Parcial, Utilizado, Aprovação Pendente

**Fluxo de Utilização:**
```
Vendedor Solicita → Financeiro Aprova/Recusa → Saldo Atualizado
```

---

### Módulo de Recorrer
Rastreia e gerencia as disputas abertas em plataformas de marketplace.

**Recursos:**
- Criação manual ou automática via triagem
- Controle de prazos com alertas visuais (cores por urgência)
- Registro de respostas e resultados
- Campos específicos para reembolso (dentro/fora da venda)
- Vinculação com número de transação
- Exportação para Excel com filtros avançados

**Status do Recurso:**
```
Aguardando Recorrer → Em Análise → Finalizado
```

---

### Módulo de Transportadora
Gerencia solicitações de coleta e entregas especiais.

**Recursos:**
- Cadastro de solicitações com valor do pedido e coleta
- Controle de prazos com indicadores visuais
- Upload de anexos (comprovantes, notas)
- Status: Solicitada, Concluído, Cancelada
- Exportação para Excel

---

### Módulo de Cancelamentos
Registra e controla cancelamentos de pedidos.

**Recursos:**
- Registro por responsabilidade (CS ou Cliente)
- Controle de custos e taxas
- Vinculação com refugo quando aplicável
- Histórico completo de cancelamentos

---

### Módulo de Refugo (Visão Consolidada)
Controla o destino e o custo de peças e produtos defeituosos.

**Recursos:**
- Visão unificada de refugos de todos os módulos
- Agregação de dados de: Garantias, Trocas, Triagens, Contas a Pagar, Vale-Crédito, Cancelamentos
- Filtros avançados por tipo, responsável e período
- Exportação consolidada para Excel

---

### Módulo de Estoque de Versões
Controle granular de estoque por versão de produto.

**Recursos:**
- Cadastro de produtos com múltiplas versões
- Controle de estoque mínimo com alertas
- Movimentações: Entrada, Saída, Ajuste
- Histórico completo de movimentações
- Dashboard com estatísticas
- Atendimentos vinculados a produtos
- Permissões específicas por cargo

**Tipos de Movimentação:**
- **Entrada**: Recebimento de peças
- **Saída**: Envio para cliente/técnico
- **Ajuste**: Correção de inventário

---

### Sistema de Notificações
Sistema de alertas em tempo real para toda a equipe.

**Recursos:**
- Notificações por categoria (Conferência, Vale-Crédito, Recorrer, etc.)
- Marcação como lida individual ou em massa
- Exclusão em massa
- API REST para integração
- Contador de não lidas no header

---

### Autenticação e Permissões
Sistema robusto de controle de acesso.

**Cargos Disponíveis:**
| Cargo | Permissões |
|-------|------------|
| `super_admin` | Acesso total ao sistema |
| `admin_CS` | Gestão completa do CS |
| `Conferente` | Conferência de registros |
| `Financeiro` | Aprovação de pagamentos e vales |
| `Vendedor` | Solicitação de uso de vales |
| `Mercado Livre` | Gestão de estoque de versões |
| `Tecnico Eletronico` | Movimentações de estoque |

---

## Arquitetura Técnica

### Estrutura de Módulos (Blueprints Flask)

```
app/
├── auth/                 # Autenticação e login
├── main/                 # Páginas principais e dashboard
├── garantias_trocas/     # Módulo de garantias e trocas
│   ├── routes.py
│   ├── forms.py
│   ├── tiny_api.py       # Integração Tiny ERP
│   └── bgq_api.py        # Integração BigQuery
├── triagens/             # Módulo de triagem
├── contas_pagar/         # Módulo financeiro
│   ├── routes.py
│   ├── forms.py
│   └── tiny_api.py       # Integração Tiny ERP
├── vale_credito/         # Módulo de vale-crédito
│   ├── routes.py
│   ├── forms.py
│   └── bgq_api.py        # Integração BigQuery
├── recorrer/             # Módulo de recursos/disputas
├── cancelamentos/        # Módulo de cancelamentos
├── transportadora/       # Módulo de transportadora
├── refugo/               # Visão consolidada de refugos
├── estoque_versoes/      # Controle de estoque por versão
│   ├── routes.py
│   ├── forms.py
│   ├── models.py         # Models específicos do módulo
│   └── importacao.py     # Importação em massa
├── notifications/        # Sistema de notificações
├── manuais/              # Documentação interna
├── models.py             # Models principais
├── utils.py              # Funções utilitárias
└── templates/            # Templates Jinja2
```

### Modelo de Dados Simplificado

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│      User       │────<│  GarantiaTroca  │────<│      Item       │
└─────────────────┘     └─────────────────┘     └─────────────────┘
        │                       │
        │               ┌───────┴───────┐
        │               │               │
        ▼               ▼               ▼
┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│   ContaPagar    │ │    Triagem      │ │   Marcador      │
└─────────────────┘ └─────────────────┘ └─────────────────┘
        │                   │
        │                   ▼
        │           ┌─────────────────┐
        │           │    Recorrer     │
        │           └─────────────────┘
        │
        ▼
┌─────────────────┐     ┌─────────────────┐
│   ValeCredito   │────<│ValeCreditoUtil. │
└─────────────────┘     └─────────────────┘

┌─────────────────┐     ┌─────────────────┐
│    Produto      │────<│  VersaoProduto  │
└─────────────────┘     └─────────────────┘
        │                       │
        ▼                       ▼
┌─────────────────┐     ┌─────────────────┐
│  Atendimento    │     │ MovimentacaoEst │
└─────────────────┘     └─────────────────┘
```

---

## Stack de Tecnologias

### Backend
| Tecnologia | Uso |
|------------|-----|
| ![Python](https://img.shields.io/badge/Python_3.11-3776AB?style=for-the-badge&logo=python&logoColor=white) | Linguagem principal |
| ![Flask](https://img.shields.io/badge/Flask_3.0-000000?style=for-the-badge&logo=flask&logoColor=white) | Framework web |
| ![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=for-the-badge&logo=sqlalchemy&logoColor=white) | ORM |
| ![Alembic](https://img.shields.io/badge/Alembic-4E85A9?style=for-the-badge) | Migrations |

### Banco de Dados
| Tecnologia | Uso |
|------------|-----|
| ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white) | Banco principal |
| ![SQLite](https://img.shields.io/badge/SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white) | Banco de desenvolvimento |

### Frontend
| Tecnologia | Uso |
|------------|-----|
| ![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white) | Estrutura |
| ![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white) | Estilização |
| ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black) | Interatividade |
| ![Bootstrap](https://img.shields.io/badge/Bootstrap_5-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white) | Framework CSS |
| ![Jinja2](https://img.shields.io/badge/Jinja2-B41717?style=for-the-badge&logo=jinja&logoColor=white) | Template Engine |

### Infraestrutura
| Tecnologia | Uso |
|------------|-----|
| ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) | Containerização |
| ![Gunicorn](https://img.shields.io/badge/Gunicorn-499848?style=for-the-badge&logo=gunicorn&logoColor=white) | WSGI Server |
| ![Linux](https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white) | Sistema Operacional |

---

## Integrações

### Tiny ERP
- **Geração de Pedidos**: Criação automática de pedidos de garantia/troca
- **Contas a Pagar**: Inclusão de contas diretamente no financeiro do ERP
- **Consulta de Produtos**: Busca de SKUs e saldos de estoque

### Google BigQuery
- **Consulta de Clientes**: Busca de dados cadastrais por CPF/CNPJ
- **Histórico de Pedidos**: Consulta de pedidos anteriores do cliente
- **Autocomplete**: Sugestões em tempo real durante digitação

### Exportações
- **Excel (XLSX)**: Todos os módulos possuem exportação com filtros
- **Relatórios**: Dados formatados para análise gerencial

---

## Resultados e Impacto

A implementação do Conexão CS representou a transição do setor de um modelo reativo e manual para um modelo proativo e orientado por dados.

### Benefícios Alcançados

- **Centralização da Informação** - Eliminou a dependência de múltiplas planilhas
- **Aumento da Eficiência** - Automatizou tarefas repetitivas
- **Melhora na Tomada de Decisão** - Dados estruturados para relatórios
- **Redução de Riscos** - Controle financeiro integrado
- **Rastreabilidade Total** - Histórico completo de todas as operações
- **Comunicação Eficiente** - Sistema de notificações em tempo real

---

## Licença

Este projeto é proprietário e de código-fonte fechado. Este repositório serve apenas como demonstração pública das capacidades e arquitetura do sistema.

---

<div align="center">

**Desenvolvido para otimizar operações de Customer Success**

</div>
