# BridgePoint Africa Europa — Project Portal

![BridgePoint](https://img.shields.io/badge/BridgePoint-Africa%20Europa-C9A227?style=flat-square&labelColor=0A1520)
![Version](https://img.shields.io/badge/Portal-v1.0-green?style=flat-square&labelColor=0A1520)
![Host](https://img.shields.io/badge/Host-GitHub%20Pages-blue?style=flat-square&labelColor=0A1520)
![Domain](https://img.shields.io/badge/Domain-projects.bridgepointafreuropa.com-C9A227?style=flat-square&labelColor=0A1520)

---

## 🇵🇹 Português

### Estrutura do Portal

Este repositório aloja o **BridgePoint Project Portal** — a infraestrutura central para todos os dashboards PMO de projetos BridgePoint Africa Europa.

```
projects.bridgepointafreuropa.com
/
├── index.html                    ← Página de entrada (sem listagem de projetos)
│
├── jardins-de-leiria/
│     └── index.html             ← PMO Dashboard — Jardins de Leiria Residence
│
├── centro-de-setubal/
│     └── index.html             ← Em preparação
│
├── mining/
│     └── index.html             ← Em preparação
│
├── agriculture/
│     └── index.html             ← Em preparação
│
├── infrastructure/
│     └── index.html             ← Em preparação
│
├── assets/
│     ├── images/
│     │     └── bpae-logo.jpg    ← Logo partilhado
│     ├── css/                   ← CSS partilhado (uso futuro)
│     └── js/                    ← JS partilhado (uso futuro)
│
├── CNAME                        ← Domínio personalizado
└── .github/workflows/pages.yml  ← Deploy automático
```

### Isolamento de Projetos

Cada projeto tem a sua própria pasta isolada. Os visitantes com um link de projeto apenas veem esse projeto específico. A página de entrada **nunca expõe** outros projetos ou links ativos.

### Adicionar um Novo Projeto

1. Criar uma nova pasta: `/nome-do-projeto/`
2. Adicionar `index.html` com o dashboard PMO do projeto
3. Fazer commit e push para `main`
4. O deploy é automático via GitHub Actions

### Configuração de DNS

Para apontar `projects.bridgepointafricaeuropa.com` para este repositório:

| Tipo | Nome | Valor |
|------|------|-------|
| `CNAME` | `projects` | `bennyxman.github.io` |

Após configuração DNS, ativar **GitHub Pages** nas Settings do repositório com source: `main / (root)`.

---

## 🇬🇧 English

### Portal Structure

This repository hosts the **BridgePoint Project Portal** — the central infrastructure for all BridgePoint Africa Europa project PMO dashboards.

### Project Isolation

Each project has its own isolated folder. Visitors with a project link only see that specific project. The landing page **never exposes** other projects or active links.

### Adding a New Project

1. Create a new folder: `/project-name/`
2. Add `index.html` with the project PMO dashboard
3. Commit and push to `main`
4. Deployment is automatic via GitHub Actions

### DNS Configuration

To point `projects.bridgepointafricaeuropa.com` to this repository:

| Type | Name | Value |
|------|------|-------|
| `CNAME` | `projects` | `bennyxman.github.io` |

After DNS is configured, enable **GitHub Pages** in repository Settings with source: `main / (root)`.

---

## Active Projects

| Project | URL | Status |
|---------|-----|--------|
| Jardins de Leiria Residence | `/jardins-de-leiria/` | ✅ Active |
| Centro de Setúbal | `/centro-de-setubal/` | 🔜 Coming soon |
| Mining | `/mining/` | 🔜 Coming soon |
| Agriculture | `/agriculture/` | 🔜 Coming soon |
| Infrastructure | `/infrastructure/` | 🔜 Coming soon |

---

*BridgePoint Africa Europa · Connecting Capital. Empowering Growth.*
*Angola · Portugal · Germany · www.bridgepointafricaeuropa.com*
