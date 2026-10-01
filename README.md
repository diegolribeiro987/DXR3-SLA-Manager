# 🚀 D-XR3 - Helpdesk & SLA Manager

> **Sistema de Gestão de Chamados, Triagem Operacional e Prevenção de Estouro de SLA com PostgreSQL e Python.**

---

## 📌 Sobre o Projeto

O **D-XR3** é uma solução para controle de ordens de serviço (OS) e gestão de chamados operacionais multidepartamentais. O objetivo central da plataforma é monitorar o tempo de atendimento (SLA) em tempo real, priorizando contas estratégicas e prevenindo multas contratuais e perda de clientes (*churn*).

O sistema atende os fluxos operacionais dos seguintes departamentos:
* **Vendas:** Cotações, Pedidos de Venda, NF de Saída, Saída de Estoque, Cancelamentos e Expedição.
* **Compras:** Contratos, Requisições, Estratégias de Liberação, Pedidos de Compras e Divergências de NF.
* **Estoque:** Armazenamento, Saída de Mercadorias e Inventário.
* **Faturamento, TI e Logística Reversa.**

---

## 🎯 Principais Funcionalidades

* **Quadro Kanban Interativo:** Organização por colunas (*A Fazer / Triagem, Em Andamento, Em Espera, Concluído*) com suporte a Drag & Drop.
* **Monitoramento e Gestão de SLA:** Cálculo em tempo real indicando chamados próximos de estourar (`⚠️ QUASE ESTOURANDO`) e chamados excedidos (`🚨 SLA ESTOURADO`).
* **Dashboard de Clientes Críticos:** Acompanhamento métrico de atendimentos para grandes contas (*Itaú, McDonald's, Pão de Açúcar, Samsung, Santander, Sanofi, Drogasil, Telhanorte e Havaianas*).
* **Controle de Acesso e Gestão:** Aba restrita a gestores autorizados para cadastro dinâmico de novos colaboradores e clientes.
* **Persistência Relacional (PostgreSQL):** Estrutura de banco de dados para auditoria, histórico de acompanhamento e análise de performance técnica.

---

## 🛠️ Tecnologias Utilizadas

* **Backend:** Python 3.x
* **Banco de Dados:** PostgreSQL (`psycopg2-binary`)
* **Frontend:** HTML5, CSS3, JavaScript (Vanilla ES6), Tailwind CSS
* **IDE de Desenvolvimento:** PyCharm
* **Versionamento de Código:** Git & GitHub

---

## 🗄️ Estrutura do Banco de Dados (`PostgreSQL`)

A tabela principal de chamados no banco `dxr3_db` segue a estrutura relacional abaixo:

```sql
CREATE TABLE IF NOT EXISTS chamados (
    id SERIAL PRIMARY KEY,
    cliente VARCHAR(100) NOT NULL,
    departamento VARCHAR(50) NOT NULL,
    processo VARCHAR(100),
    prioridade VARCHAR(20) NOT NULL,
    solicitante VARCHAR(100),
    tecnico VARCHAR(100),
    descricao TEXT,
    data_criacao TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    status_sla VARCHAR(30) DEFAULT 'DENTRO DO PRAZO'
);
