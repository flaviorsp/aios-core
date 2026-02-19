# 🚀 Referência Definitiva: Todas as Sequências de Instrução AIOS

**Data**: 2026-02-13 | **Fonte**: user-guide.md (1414L), working-in-the-brownfield.md (362L), constitution.md (172L)

---

## 📑 Índice de Cenários

| # | Cenário | Agents | Complexidade |
|---|---------|--------|-------------|
| 1 | [Instalação](#1-instalação) | - | Baixa |
| 2 | [Greenfield Completo](#2-greenfield-completo-do-conceito-à-produção) | 7 agents | Alta |
| 3 | [Brownfield PRD-First](#3-brownfield-prd-first-recomendado) | 5 agents | Alta |
| 4 | [Brownfield Document-First](#4-brownfield-document-first) | 6 agents | Alta |
| 5 | [Brownfield Quick Fix](#5-brownfield-quick-enhancement) | 2 agents | Baixa |
| 6 | [Ciclo de Story](#6-ciclo-de-desenvolvimento-de-story) | 3 agents | Média |
| 7 | [Modo YOLO](#7-modo-yolo-desenvolvimento-autônomo) | 1 agent | Baixa |
| 8 | [Modo Interactive](#8-modo-interactive-desenvolvimento-colaborativo) | 1 agent | Média |
| 9 | [Modo Pre-Flight](#9-modo-pre-flight-planejamento-total) | 1 agent | Alta |
| 10 | [Quality Gates + Push](#10-quality-gates--push-para-github) | 1 agent | Média |
| 11 | [Squad Customization](#11-squad-customization) | 1 agent | Alta |
| 12 | [Mudança de Requisitos](#12-mudança-de-requisitos-mid-project) | 4 agents | Média |
| 13 | [Criação de Agente Custom](#13-criar-agente-customizado) | 1 meta-agent | Média |
| 14 | [Configuração de CI/CD](#14-configuração-cicd-github-actions) | 1 agent | Média |

---

## 1. Instalação

> **Evidência**: user-guide.md L27-42, L130-162

### 1.1 Projeto Novo ou Existente

```bash
# Navegue para o diretório do projeto
cd /path/to/your/project

# Execute o instalador (versão RC atual)
npx @synkra/aios-core@rc install
```

### 1.2 Wizard Interativo (o que aparece)

```
🚀 AIOS-FullStack Installation Wizard

📦 Select Expansion Packs to Install:
  ◉ hybrid-ops
  ◯ expansion-creator
  ◯ aios-infrastructure-devops
  ◯ meeting-notes

💻 Select IDEs to Configure:
  ◉ Claude Code (.claude/commands/)
  ◉ Cursor (.cursor/rules/)
  ◯ Windsurf (.windsurf/rules.md)
  ◯ Gemini CLI (.gemini/)

📝 Sharding Preferences:
  ◯ Single file
  ◉ Multi-file
```

### 1.3 Upgrade de Versão Existente

```bash
# Upgrade automático (RC.9+)
npx @synkra/aios-core@rc install --force-upgrade

# OU interativo
npx @synkra/aios-core@rc install
# → Escolha "Upgrade AIOS core"
```

### 1.4 Verificar Versão

```bash
npm view @synkra/aios-core@rc version
```

### 1.5 Listar Recursos

```bash
# Ver agentes disponíveis
npx @synkra/aios-core@rc list:agents

# Ver expansion packs
npx @synkra/aios-core@rc list:expansions
```

---

## 2. Greenfield Completo (Do Conceito à Produção)

> **Evidência**: user-guide.md L642-748, core-architecture.md L154-193

### FASE 1: Planejamento (Web UI — Claude.ai / Gemini / ChatGPT)

```
═══════════════════════════════════════════════════════
  PASSO 1: Criar Briefing (analyst)
═══════════════════════════════════════════════════════

@analyst
*create-brief

  → Entender requisitos de negócio
  → Identificar stakeholders
  → Definir objetivos e métricas de sucesso

  Output: docs/brief/project-brief.md

═══════════════════════════════════════════════════════
  PASSO 2: Criar PRD (pm)
═══════════════════════════════════════════════════════

@pm
*create-doc prd

  → Recebe briefing do analyst
  → Faz perguntas de esclarecimento
  → Cria PRD fragmentado
  → Refina com feedback do usuário

  Output:
    docs/prd/01-overview.md
    docs/prd/02-features.md
    docs/prd/03-requirements.md
    docs/prd/04-success-metrics.md

═══════════════════════════════════════════════════════
  PASSO 3: Criar Arquitetura (architect)
═══════════════════════════════════════════════════════

@architect
*create-doc architecture

  → Desenhar arquitetura técnica
  → Escolher stack tecnológico
  → Criar diagramas de sistema
  → Definir padrões de código

  Output:
    docs/architecture/01-system-design.md
    docs/architecture/02-tech-stack.md
    docs/architecture/03-data-models.md
    docs/architecture/04-patterns.md

═══════════════════════════════════════════════════════
  PASSO 4 (Opcional): Design UX (ux-expert)
═══════════════════════════════════════════════════════

@ux-expert
*create-doc ux-design

  → Design de interface
  → Fluxos de usuário
  → Wireframes conceituais

  Output:
    docs/ux/01-user-flows.md
    docs/ux/02-wireframes.md
```

### FASE 2: Transição Web UI → IDE

```
═══════════════════════════════════════════════════════
  PASSO 5: Validar Planejamento (po)
═══════════════════════════════════════════════════════

@po
*execute-checklist po-master-checklist

  → Validar consistência PRD ↔ Arquitetura
  → Confirmar que tudo está pronto para dev

═══════════════════════════════════════════════════════
  PASSO 6: Fragmentar Docs (po) — Agora no IDE
═══════════════════════════════════════════════════════

@po
*shard-doc docs/prd.md
*shard-doc docs/architecture.md

  → Fragmenta documentos grandes em seções
  → Prepara contexto para stories
```

### FASE 3: Desenvolvimento (IDE — Cursor / Claude Code / Windsurf)

```
═══════════════════════════════════════════════════════
  PASSO 7: Criar Stories (sm)
═══════════════════════════════════════════════════════

@sm
*create-next-story

  → Cria story com contexto completo
  → Define tarefas com checkboxes
  → Estabelece acceptance criteria
  → Organiza dependências

  Output: docs/stories/story-1.1-setup-inicial.md

═══════════════════════════════════════════════════════
  PASSO 8: Implementar Story (dev) — LOOP
═══════════════════════════════════════════════════════

@dev
*develop docs/stories/story-1.1.md

  → Lê story completamente
  → Implementa código
  → Atualiza checkboxes [ ] → [x]
  → Mantém lista de Arquivos Criados/Modificados
  → Documenta decisões nas Notas

═══════════════════════════════════════════════════════
  PASSO 9: QA Review (qa) — LOOP
═══════════════════════════════════════════════════════

@qa
*review-story docs/stories/story-1.1.md

  → Revisa código
  → Executa testes
  → Valida acceptance criteria
  → PASS → Story Done
  → FAIL → Volta para @dev com feedback

═══════════════════════════════════════════════════════
  PASSO 10: Repetir para próxima story
═══════════════════════════════════════════════════════

@sm
*create-next-story     # Cria próxima story

# Repetir passos 8-9 ATÉ todas stories Done
```

### FASE 4: Release

```
═══════════════════════════════════════════════════════
  PASSO 11: Quality Gate + Push (devops)
═══════════════════════════════════════════════════════

@devops
*pre-push

  → npm run lint ✓
  → npm run typecheck ✓
  → npm run test ✓
  → npm run build ✓
  → Story status = Done ✓
  → Push para GitHub

═══════════════════════════════════════════════════════
  PASSO 12: Criar PR (devops)
═══════════════════════════════════════════════════════

@devops
*create-pr

  → Cria branch do story ID
  → Gera descrição do PR
  → Atribui reviewers
```

---

## 3. Brownfield PRD-First (Recomendado)

> **Evidência**: working-in-the-brownfield.md L31-97

**Melhor para**: Grandes codebases, monorepos, features complexas

```
═══════════════════════════════════════════════════════
  PASSO 1: Instalar AIOS (se não instalado)
═══════════════════════════════════════════════════════

cd /projeto-existente
npx @synkra/aios-core@rc install

═══════════════════════════════════════════════════════
  PASSO 2: Criar PRD Brownfield (pm) — Gemini Web
═══════════════════════════════════════════════════════

# Upload codebase para Gemini Web (1M+ tokens context)
# OU use Gemini CLI no diretório do projeto

@pm
*create-doc brownfield-prd

  → PM analisa codebase + pede requirements
  → Explora código existente
  → Identifica áreas afetadas
  → Cria PRD focado

═══════════════════════════════════════════════════════
  PASSO 3: Documentar Áreas Relevantes (analyst)
═══════════════════════════════════════════════════════

@analyst
*document-project

  → Documenta APENAS módulos afetados pelo PRD
  → Foca em código relevante
  → Gera docs/project-architecture.md

═══════════════════════════════════════════════════════
  PASSO 4: Criar Arquitetura Brownfield (architect)
═══════════════════════════════════════════════════════

@architect
*create-doc brownfield-architecture

  → Review do brownfield PRD
  → Design de integração
  → Plano de migração (se necessário)
  → Riscos técnicos

═══════════════════════════════════════════════════════
  PASSO 5: Validar (po)
═══════════════════════════════════════════════════════

@po
*execute-checklist po-master-checklist

  → Compatibilidade com sistema existente
  → Sem breaking changes
  → Scope definido

═══════════════════════════════════════════════════════
  PASSO 6: Transição para IDE → Loop de Dev
═══════════════════════════════════════════════════════

# No IDE:
@sm
*create-next-story

@dev
*develop docs/stories/story-X.md

@qa
*review-story docs/stories/story-X.md

# Repetir até todas stories Done

═══════════════════════════════════════════════════════
  PASSO 7: Push (devops)
═══════════════════════════════════════════════════════

@devops
*pre-push
```

---

## 4. Brownfield Document-First

> **Evidência**: working-in-the-brownfield.md L98-158

**Melhor para**: Projetos menores, sistemas desconhecidos

```
═══════════════════════════════════════════════════════
  PASSO 1: Documentar Sistema Inteiro (analyst)
═══════════════════════════════════════════════════════

# Gemini Web: Upload projeto (GitHub URL ou ZIP)
# Carregar agent: Upload dist/agents/analyst.txt

@analyst
*document-project

  → Documenta TUDO (sistema inteiro)
  → Output: docs/project-architecture.md

═══════════════════════════════════════════════════════
  PASSO 2: Criar PRD com Contexto Completo (pm)
═══════════════════════════════════════════════════════

@pm
*create-doc brownfield-prd

  → PM já tem contexto total do sistema
  → Cria PRD baseado na documentação

═══════════════════════════════════════════════════════
  PASSO 3: Arquitetura (architect)
═══════════════════════════════════════════════════════

@architect
*create-doc brownfield-architecture

═══════════════════════════════════════════════════════
  PASSO 4: Validar + Dev (mesmo fluxo do Cenário 3)
═══════════════════════════════════════════════════════

# Mesmos passos 5-7 do cenário anterior
```

---

## 5. Brownfield Quick Enhancement

> **Evidência**: working-in-the-brownfield.md L160-188

### 5A. Epic Isolado (Feature Média)

```
@pm
*brownfield-create-epic

  → Enhancement bem definido e isolado
  → Documentação existente é suficiente
  → Não impacta múltiplos sistemas

# Depois: dev→qa loop normal
```

### 5B. Story Única (Bug Fix / Feature Tiny)

```
@pm
*brownfield-create-story

  → Bug fix ou feature minúscula
  → Mudança muito isolada
  → Sem impacto arquitetural
  → Path de implementação claro

# Depois: dev→qa loop normal
```

---

## 6. Ciclo de Desenvolvimento de Story

> **Evidência**: user-guide.md L689-711, core-architecture.md L200-221

```
═══════════════════════════════════════════════════════
  Loop Principal (repetir para CADA story)
═══════════════════════════════════════════════════════

# 1. SM cria story
@sm
*create-next-story

# 2. Dev implementa
@dev
*develop docs/stories/story-X.md

  → Lê story completamente
  → Implementa código
  → Atualiza [ ] → [x] ao completar
  → Adiciona arquivos à lista
  → Documenta decisões nas Notas

# 3. QA valida
@qa
*review-story docs/stories/story-X.md

  → Code review
  → Executa testes
  → Valida acceptance criteria
  → PASS: Story Done → próxima story
  → FAIL: Dev recebe feedback → fix → re-review

# 4. Se FAIL:
@dev
*apply-qa-fixes

  → Lê feedback do QA
  → Corrige issues
  → Volta para QA review
```

---

## 7. Modo YOLO (Desenvolvimento Autônomo)

> **Evidência**: user-guide.md L891-926

**Melhor para**: Devs experientes, stories simples, pressa

```
@dev
*develop-yolo "Story 2.5"

  → Lê story automaticamente
  → Toma TODAS decisões técnicas sozinho
  → Zero prompts ao usuário (0-1 max)
  → Loga todas decisões
  → Implementa story inteira
  → Gera relatório de decisões

# Output: Relatório de Decisões YOLO
# Ex: "Escolheu Axios (melhor error handling)"
#     "Escolheu React Context (não justifica Redux)"
```

### Quando usar YOLO

| Cenário | Recomendado? |
|---------|-------------|
| CRUD simples | ✅ Sim |
| Bug fix | ✅ Sim |
| Spike/prototype | ✅ Sim |
| Sistema crítico de auth | ❌ Não |
| Algoritmo complexo | ❌ Não |

---

## 8. Modo Interactive (Desenvolvimento Colaborativo)

> **Evidência**: user-guide.md L928-968

**Melhor para**: Aprendizado, stories complexas, decisões importantes

```
@dev
*develop-story "Story 2.5"
# ou
*develop-interactive "Story 2.5"

  → Checkpoints explícitos de decisão
  → 5-10 prompts ao usuário
  → Explicações educacionais
  → Usuário confirma decisões chave

# Exemplo de interação:
# Agente: "Preciso escolher state management"
# Opções: 1. Context  2. Redux  3. Zustand
# Recomendação: Context (requisitos simples)
# Sua escolha [1/2/3]: _
```

---

## 9. Modo Pre-Flight (Planejamento Total)

> **Evidência**: user-guide.md L970-1065

**Melhor para**: Features críticas, stories ambíguas, zero scope drift

```
@dev
*develop-preflight "Story 2.5"

═══════════════════════════════════════════════════════
  Fase 1: Análise + Questionário
═══════════════════════════════════════════════════════

  → Agente lê story
  → Identifica TODAS ambiguidades
  → Gera questionário completo:

  Questionário Pre-Flight:
  1. Padrão de API? (RESTful, GraphQL, RPC)
  2. Lógica de negócio? (Service, Controller, Model)
  3. HTTP client? (Axios, Fetch, node-fetch)
  4. Validação? (Yup, Zod, Joi, custom)
  5. Cobertura alvo? (80%, 90%, 100%)
  6. Dados de teste? (Fixtures, Factories, Mocks)
  7. Error handling? (Try-catch, Boundaries, ambos)
  8. Loading UI? (Spinner, Skeleton, Progress)

  Suas respostas [separar com |]:
  RESTful | Service | Axios | Yup | 80% | Fixtures | Ambos | Spinner

═══════════════════════════════════════════════════════
  Fase 2: Execução com Zero Ambiguidade
═══════════════════════════════════════════════════════

  → Agente tem TODAS respostas
  → Sem perguntas durante dev
  → Sem scope drift
  → Registra decisões no final
```

---

## 10. Quality Gates + Push para GitHub

> **Evidência**: user-guide.md L750-886, git-workflow-guide.md L23-96

### 10.1 Push Completo com Quality Gate

```
@devops
*pre-push

  → ✓ npm run lint
  → ✓ npm run typecheck
  → ✓ npm run test
  → ✓ npm run build
  → ✓ Story status = "Done"
  → ✓ Sem mudanças uncommitted
  → Apresenta resumo para aprovação
  → Push para GitHub
```

### 10.2 Criar Pull Request

```
@devops
*create-pr

  → Cria feature branch do story ID
  → Gera descrição do PR
  → Linka PR à story
  → Atribui reviewers
```

### 10.3 Configurar CI/CD

```
@devops
*configure-ci

  → Instala .github/workflows/ci.yml
  → Instala .github/workflows/cd.yml
  → Instala .github/workflows/quality-gate.yml
```

### 10.4 Detectar Repositório

```
@devops
*detect-repo

  → Mostra repo e modo detectados
```

### 10.5 Cleanup

```
@devops
*cleanup

  → Remove branches obsoletas
  → Remove arquivos temporários
```

### 10.6 Version Check

```
@devops
*version-check

  → Analisa requisitos de bump de versão
```

> **⚠️ Regra Constitucional**: Push direto (`git push`) é BLOQUEADO. Apenas `@devops *pre-push` funciona.
> **Evidência**: constitution.md L35, user-guide.md L842-856

---

## 11. Squad Customization

> **Evidência**: faq.md L458-488, user-guide.md L1281-1313

### 11.1 Criar Squad do Zero

```
═══════════════════════════════════════════════════════
  PASSO 1: Design
═══════════════════════════════════════════════════════

@squad-creator
*design

  → Analisa PRD/docs
  → Identifica patterns de domínio
  → Propõe estrutura

═══════════════════════════════════════════════════════
  PASSO 2: Criar
═══════════════════════════════════════════════════════

@squad-creator
*create meu-squad --from-design

  → Cria:
    Squads/meu-squad/
    ├── squad.yaml
    ├── README.md
    ├── agents/
    ├── tasks/
    ├── templates/
    └── workflows/

═══════════════════════════════════════════════════════
  PASSO 3: Validar
═══════════════════════════════════════════════════════

@squad-creator
*validate meu-squad

  → Verifica squad.yaml
  → Confirma agents existem
  → Valida tasks e templates
  → Checa dependências

═══════════════════════════════════════════════════════
  PASSO 4: Publicar (Opcional)
═══════════════════════════════════════════════════════

@squad-creator
*publish meu-squad

═══════════════════════════════════════════════════════
  Extra: Download de Squad Existente
═══════════════════════════════════════════════════════

@squad-creator
*download nome-do-squad

═══════════════════════════════════════════════════════
  Extra: Listar Squads Disponíveis
═══════════════════════════════════════════════════════

npx @synkra/aios-core@rc list:expansions
```

---

## 12. Mudança de Requisitos Mid-Project

> **Evidência**: user-guide.md L1216-1233

```
═══════════════════════════════════════════════════════
  PASSO 1: Atualizar PRD (po)
═══════════════════════════════════════════════════════

@po
*update-prd "Nova feature X necessária"

═══════════════════════════════════════════════════════
  PASSO 2: Avaliar Impacto (architect)
═══════════════════════════════════════════════════════

@architect
*assess-impact "Nova feature X"

  → Identifica áreas afetadas
  → Avalia complexidade
  → Riscos técnicos

═══════════════════════════════════════════════════════
  PASSO 3: Criar Stories de Mudança (sm)
═══════════════════════════════════════════════════════

@sm
*create-change-stories

═══════════════════════════════════════════════════════
  PASSO 4: Repriorizar Backlog (po)
═══════════════════════════════════════════════════════

@po
*reprioritize-backlog

# → Volta ao loop dev→qa normal
```

---

## 13. Criar Agente Customizado

> **Evidência**: user-guide.md L1264-1328

```
@aios-developer
*create-agent

  → Siga a elicitação interativa:
  Nome do agente: data-scientist
  Expertise: Análise de dados e machine learning
  Comandos principais: *analyze, *visualize, *predict
  Workflows: data-analysis.yml, ml-model.yml
```

---

## 14. Configuração CI/CD GitHub Actions

> **Evidência**: user-guide.md L871-883

```
@devops
*configure-ci

  → Instala em .github/workflows/:
    ci.yml            # Testes em PRs
    cd.yml            # Deploy em merge para main
    quality-gate.yml  # Lint + Test + Build

  → Workflows se adaptam aos npm scripts do repositório
```

---

## 📋 Referência Rápida: Todos os Comandos por Agent

### @analyst
```
*create-brief              # Criar briefing
*analyze-requirements      # Analisar requisitos
*document-project          # Documentar projeto existente
*analyze-existing-project  # Análise de brownfield
```

### @pm
```
*create-doc prd                # Criar PRD (greenfield)
*create-doc brownfield-prd     # Criar PRD (brownfield)
*brownfield-create-epic        # Epic rápido brownfield
*brownfield-create-story       # Story rápida brownfield
*create-migration-plan         # Plano de migração
*update-prd                    # Atualizar PRD
```

### @architect
```
*create-doc architecture            # Criar arquitetura
*create-doc brownfield-architecture # Arquitetura brownfield
*document-existing-architecture     # Documentar arch existente
*assess-impact                      # Avaliar impacto de mudança
```

### @ux-expert
```
*create-doc ux-design      # Criar design UX
```

### @po
```
*execute-checklist po-master-checklist  # Validar planejamento
*shard-doc [arquivo]                    # Fragmentar documento
*manage-story-backlog                   # Gerenciar backlog
*close-story                            # Fechar story
*prioritize-backlog                     # Priorizar backlog
*reprioritize-backlog                   # Repriorizar
*update-prd                             # Atualizar PRD
*sync-story-to-clickup                  # Sync ClickUp
*stories-index                          # Gerar índice stories
```

### @sm
```
*create-next-story         # Criar próxima story
*draft                     # Mesmo que create-next-story
*fragment-prd              # Fragmentar PRD em stories
*split-story [id]          # Dividir story grande
*create-change-stories     # Stories de mudança
```

### @dev
```
*develop [story]           # Modo Interactive (padrão)
*develop-yolo [story]      # Modo YOLO (autônomo)
*develop-interactive [story] # Modo Interactive (explícito)
*develop-preflight [story]  # Modo Pre-Flight
*apply-qa-fixes            # Aplicar correções QA
*suggest-refactoring       # Sugerir refatorações
*improve-code-quality      # Melhorar qualidade
*optimize-performance      # Otimizar performance
*backlog-debt              # Gerenciar débito técnico
```

### @qa
```
*review-story [story]      # Revisar story
*generate-tests            # Gerar testes
*security-checklist        # Checklist OWASP
*review-build              # Revisar build
*fix-issues                # Corrigir issues
*final-validation          # Validação final release
```

### @devops
```
*pre-push                  # Quality gate + push
*create-pr                 # Criar Pull Request
*configure-ci              # Configurar GitHub Actions
*detect-repo               # Detectar repositório
*cleanup                   # Limpar branches/temp
*version-check             # Verificar versioning
```

### @squad-creator
```
*design                    # Design squad
*create [nome]             # Criar squad
*validate [nome]           # Validar squad
*publish [nome]            # Publicar squad
*download [nome]           # Download squad
*list                      # Listar squads
*extend [nome]             # Estender squad
*migrate [nome]            # Migrar squad
*analyze [nome]            # Analisar squad
```

### @aios-developer (Meta-Agent)
```
*create-agent [nome]       # Criar agente custom
```

### @aios-master (Orchestrador)
```
*help                      # Ver comandos
*workflow                  # Executar workflow
*orchestrate               # Orquestração multi-agente
```

---

## ⚡ Atalho: Comando Universal

Qualquer agent reconhece:
```
*help      # Ver comandos disponíveis do agent
*exit      # Sair do agent
```

---

## 🔑 Regras Invioláveis (Constituição)

| Regra | Severidade | O que Significa |
|-------|-----------|----------------|
| CLI First | BLOCK | CLI antes de UI, sempre |
| Agent Authority | BLOCK | @devops = push, @qa = verdicts |
| Story-Driven | BLOCK | Sem código sem story |
| No Invention | BLOCK | Specs derivam de requisitos |
| Quality First | BLOCK | lint+test+build devem passar |
| Absolute Imports | INFO | Usar @/ em vez de ../../ |

> **Evidência**: constitution.md L11-157
