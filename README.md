# Conexão CS 

**Status do Projeto:**  Em Produção | Em Melhoria Contínua

**Um portal web completo para centralizar e otimizar as operações do setor de Customer Success, transformando processos manuais e descentralizados em fluxos de trabalho digitais, eficientes e rastreáveis.**

*Este é um projeto interno e de código-fonte fechado. Este repositório serve como uma vitrine pública ("case study") para demonstrar sua arquitetura, funcionalidades e o impacto de negócio que ele gerou.*

---

![Garantias e Trocas](./assets/Conexao_CS.gif)

---

## 1. Contexto e Problema

O setor de Customer Success da empresa lidava com um alto volume de processos críticos para a satisfação do cliente e para a saúde financeira da operação. Processos como gestão de garantias, trocas, devoluções, cancelamentos e controle de peças defeituosas eram gerenciados de forma descentralizada, utilizando planilhas, e-mails e comunicação informal.

Essa abordagem resultava em:
- **Falta de visibilidade:** Era difícil rastrear o status de uma solicitação em tempo real.
- **Ineficiência operacional:** Processos manuais e repetitivos consumiam um tempo valioso da equipe.
- **Perda de informação:** Dados importantes se perdiam entre diferentes plataformas, dificultando a tomada de decisão e a identificação de gargalos.
- **Riscos financeiros:** A falta de um controle rigoroso sobre vales-crédito, refugos e contas a pagar gerava riscos de perdas financeiras.

## 2. Solução Proposta

O **Conexão CS** foi desenvolvido do zero como uma solução web centralizada para atacar diretamente essas dores. O sistema unifica todos os fluxos de trabalho do setor em uma única plataforma, servindo como a fonte única de verdade para todas as operações de pós-venda.

A aplicação foi construída com uma stack de tecnologia moderna, conteinerizada com Docker e implantada em um servidor Linux (Ubuntu), garantindo escalabilidade, segurança e facilidade de manutenção.

## 3. Principais Funcionalidades

O sistema é modularizado para cobrir todas as facetas da operação de CS:

- **Módulo de Garantias e Trocas:** Orquestra todo o fluxo de solicitação, envio de peça pelo cliente, análise técnica e envio da nova peça.
- **Módulo de Triagem:** Gerencia o recebimento e a análise de produtos devolvidos, definindo seu destino (reparo, estoque, refugo).
- **Módulo de Contas a Pagar:** Controla os custos associados a cada processo, como fretes e taxas.
- **Módulo de Vale-Crédito:** Administra a geração, utilização e validade de créditos concedidos aos clientes.
- **Módulo de Recorrer:** Rastreia e gerencia as disputas abertas em plataformas de marketplace como o Mercado Livre.
- **Módulo de Refugo:** Controla o destino e o custo de peças e produtos defeituosos que não podem ser reaproveitados.
- **Autenticação e Permissões:** Sistema de login para garantir que cada usuário acesse apenas os módulos e informações pertinentes à sua função.
- **Dashboard e Relatórios:** (Se aplicável) Painéis que fornecem uma visão geral do status das operações e métricas de desempenho.

## 4. Stack de Tecnologias

| Categoria | Tecnologias Utilizadas |
| :--- | :--- |
| **Backend** | ![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white) ![Flask](https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white) |
| **Banco de Dados** | ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-336791?style=for-the-badge&logo=postgresql&logoColor=white) |
| **ORM & Migrations** | ![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=for-the-badge&logo=sqlalchemy&logoColor=white) ![Alembic](https://img.shields.io/badge/Alembic-4E85A9?style=for-the-badge) |
| **Frontend** | ![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white) ![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white) ![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black) ![Bootstrap](https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white) |
| **Deployment** | ![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white) ![Gunicorn](https://img.shields.io/badge/Gunicorn-499848?style=for-the-badge&logo=gunicorn&logoColor=white) ![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black) |

## 5. Resultados e Impacto

A implementação do Conexão CS representou a transição do setor de um modelo reativo e manual para um modelo proativo e orientado por dados.

- **Centralização da Informação:** Eliminou a dependência de múltiplas planilhas e fontes de dados.
- **Aumento da Eficiência:** Automatizou tarefas repetitivas e forneceu uma visão clara do status de cada solicitação, reduzindo o tempo de resolução.
- **Melhora na Tomada de Decisão:** A coleta de dados estruturados permitiu a geração de relatórios e a identificação de tendências e gargalos.
- **Redução de Riscos:** O controle financeiro integrado sobre os processos de pós-venda minimizou perdas e erros.
