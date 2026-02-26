# VendasBoost PRO

> Plataforma SaaS de automação para marketing em redes sociais
>
> *SaaS automation platform for social media marketing*

![Status](https://img.shields.io/badge/Status-Produção-brightgreen)
![Version](https://img.shields.io/badge/Versão-10.0-blue)

---

## Visão Geral | Overview

O VendasBoost PRO é uma plataforma SaaS completa que automatiza fluxos de marketing em redes sociais. Permite que empresas gerenciem postagens em múltiplos grupos, agendem conteúdo, criem anúncios em marketplaces e acompanhem performance — tudo a partir de um único painel.

O sistema suporta múltiplas empresas com gestão de funcionários, planos de assinatura com limites de uso e um painel administrativo completo para gerenciamento da plataforma.

*VendasBoost PRO is a complete SaaS platform that automates social media marketing workflows. It allows businesses to manage posting across multiple groups, schedule content, create marketplace listings, and track performance — all from a single dashboard. The system supports multiple companies with employee management, subscription plans with usage limits, and a full admin panel for platform management.*

---

## Funcionalidades Principais | Key Features

**Motor de Automação**
- Postagem em múltiplos grupos simultaneamente
- Criação de anúncios em marketplaces
- Agendamento único (data/hora) e recorrente semanal
- Descoberta e entrada automática em grupos relevantes
- Suporte a múltiplas contas

**Plataforma SaaS**
- Arquitetura multi-tenant (empresas e funcionários)
- Planos de assinatura com limites de uso por nível
- Processamento de pagamentos via MercadoPago (webhooks)
- Rastreamento de uso e medição por tokens

**Painel Administrativo**
- Métricas e KPIs de toda a plataforma
- Gestão de empresas e funcionários
- Log de auditoria
- Gerenciamento de versões e distribuição da extensão

**Segurança**
- Autenticação JWT com middleware
- Rate limiting por rota
- Validação e sanitização de entrada
- Ofuscação de código para distribuição
- Proteção contra XSS e autenticação via cookies

---

## Arquitetura | Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Extensão Chrome                        │
│              (Content Scripts + Popup UI)                 │
└──────────────────────┬──────────────────────────────────┘
                       │ REST API
┌──────────────────────▼──────────────────────────────────┐
│                   Backend (Node.js)                       │
│  ┌─────────┐  ┌──────────┐  ┌────────────┐              │
│  │  Auth    │  │  Rotas   │  │  Serviços  │              │
│  │Middleware│  │  (REST)  │  │  (Email,   │              │
│  └─────────┘  └──────────┘  │   Logger)  │              │
│                              └────────────┘              │
│  ┌──────────────────────────────────────────┐            │
│  │         Models (Sequelize ORM)            │            │
│  │  User | Company | Usage | Webhook | ...   │            │
│  └──────────────────────────────────────────┘            │
└──────────────────────┬──────────────────────────────────┘
                       │
          ┌────────────▼────────────┐
          │    Banco de Dados (SQL)  │
          └─────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│                    Painel Admin                           │
│            (HTML Estático + Vanilla JS)                   │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│               CI/CD (GitHub Actions)                     │
│         Testes automatizados e deploy contínuo           │
└─────────────────────────────────────────────────────────┘
```

---

## Stack Tecnológica | Tech Stack

| Camada | Tecnologia |
|--------|-----------|
| **Runtime** | Node.js, Express |
| **Banco de Dados** | SQL (Sequelize ORM) |
| **Autenticação** | JWT, sessões via cookies |
| **Pagamentos** | MercadoPago SDK (assinaturas + webhooks) |
| **Cliente** | Extensão Chrome (Manifest V3) |
| **Admin** | HTML Estático + Vanilla JavaScript |
| **Testes** | Jest (unitários + integração, 14+ suítes) |
| **CI/CD** | GitHub Actions (pipeline CI + deploy CD) |
| **Processo** | PM2 (gerenciador de processos em produção) |
| **Segurança** | Rate limiter, validadores, ofuscação de código |

---

## Testes | Testing

O projeto inclui testes abrangentes cobrindo:

- **Testes unitários** — Middleware de autenticação, limites de plano, validadores de entrada
- **Testes de integração** — Todas as rotas REST (auth, admin, empresas, planos, assinaturas, uso, webhooks, extensão, health)
- **Testes de segurança** — Verificação de assinatura de webhooks, proteção de rotas

---

## Números do Projeto | Project Stats

| Métrica | Valor |
|---------|-------|
| Total de arquivos | 169 |
| Suítes de teste | 14+ |
| Versão | 10.0 |
| Período de desenvolvimento | Dez 2025 — Fev 2026 |

---

*Este é um repositório vitrine. O código-fonte está em um repositório privado.*

*This is a showcase repository. The source code is in a private repository.*
