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
