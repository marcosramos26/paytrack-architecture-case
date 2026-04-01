# 🗂️ Case: Arquitetura de Governança para Gestão de Despesas de Viagem (Paytrack)

> **Autor:** Marcos Ramos  
> **Empresa:** Atakarejo  
> **Período:** Ago/2025 – Abr/2026 (8 meses)  
> **Stack:** Paytrack | Excel + Power Query | Power BI | RMS | Governança de Processos

---

## 🎯 Problema de Negócio

Rede de varejo em expansão (BA/SE) com processo manual de gestão de despesas de viagem:
- Solicitações via planilha + e-mail
- Aprovações descentralizadas e sem alçada definida
- Falta de padronização nos lançamentos
- Dificuldade em auditar, reportar e negociar com fornecedores
- Tempo médio de processamento: ~1 dia por solicitação

**Impacto:** Risco de compliance, desperdício de horas administrativas e perda de visibilidade estratégica.

---
# 🧩 Arquitetura da Solução – Gestão de Viagens

## 📐 Componentes da Arquitetura

| Camada        | Tecnologia              | Função                                                                 |
|--------------|------------------------|------------------------------------------------------------------------|
| Entrada       | Paytrack (UI)          | Self-service para colaboradores                                        |
| Governança    | Paytrack (Rules Engine)| Validação de política, alçadas e fluxos de aprovação                   |
| Dados         | Excel + Power Query    | Tratamento e padronização da base de 10k associados do RMS            |
| Integração    | Extração Manual Agendada | Ponte entre Paytrack e ecossistema interno (RMS/TOTVS)               |
| Inteligência  | Power BI               | Dashboard Orçado vs Realizado para diretoria                          |

---

## ⚙️ Regras de Negócio Implementadas

- 🔁 **Alçadas de aprovação**  
  Gestor Imediato → Time de Viagens → Contas a Pagar (Coord/Ger)

- ⏱️ **Políticas de antecedência**  
  Bloqueio de solicitações fora do prazo mínimo

- 💰 **Limites por cargo/região**  
  Configuração de tetos de gasto por perfil

- 🛏️ **Compartilhamento de quarto**  
  Regra obrigatória para otimização de custos

- 🔄 **Ciclo completo**  
  Viagem → Adiantamento → Prestação de Contas → Reembolso

---

## 📊 Resultados Quantificados

| Métrica                     | Antes           | Depois         | Variação     |
|----------------------------|----------------|---------------|--------------|
| Tempo por solicitação      | ~1 dia (24h)   | 5 minutos     | ↓ 99,6%      |
| Adoção da plataforma       | 0%             | 95%           | +95 pp       |
| Usuários ativos            | -              | 300           | -            |
| Despesas de viagem         | Base 100%      | 67%           | ↓ 33%        |
| Visibilidade para auditoria| Manual/Reativa | Automática/Tempo Real | Qualitativo |

> 💡 **Impacto financeiro indireto:**  
> Contribuição para a redução de **R$ 5,5M** em despesas operacionais (2025 vs 2024).

---

## 🔑 Lições Aprendidas

- 🧠 **Governança > Tecnologia**  
  A ferramenta é habilitadora, mas o valor vem do desenho do processo e das regras de negócio.

- 🧹 **Qualidade na migração**  
  Tratar dados ANTES de subir para a plataforma evita retrabalho e rejeição dos usuários.

- 📢 **Comunicação é parte da arquitetura**  
  Documentar fluxos e criar POPs foi essencial para adesão e escalabilidade.

- 📊 **Dados geram poder de negociação**  
  Visibilidade detalhada permitiu renegociar contratos com fornecedores.

## 🏗️ Solução Técnica: Arquitetura em Camadas

```mermaid
graph LR
    A[Colaborador] -->|Solicita Viagem | B(Paytrack)
    B -->|Valida Política | C{Regras de Negócio}
    C -->|Aprovado | D[Gestor Imediato]
    D -->|Aprova Mobile | E[Time de Viagens]
    E -->|Aprovação Final | F[Emissão Hotel/Condução]
    F -->|Voucher | A
    G[Dashboard Power BI] <-->|Extração Automática | B
    H[RM - 10k Associados] -->|Tratamento Python/Excel | B



