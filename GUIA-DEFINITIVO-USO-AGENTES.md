# 🧭 The Ultimate AIOS Agent Guide: Scenarios & Usage

**Data**: 2026-02-15 | **Protocolo**: Ultrathinking Analysis
**Abrangência**: Todos os agentes (`.claude/agents` + `.claude/commands`)

---

## 🏆 Resumo Estratégico: "Quem Chamar Quando?"

| Se você precisa de... | Chame o Grupo... | Exemplo de Agente |
| :--- | :--- | :--- |
| **Construir Software (Rotina)** | **1. The Core Squad** | `@dev`, `@pm`, `@qa` |
| **Resolver Domínios Complexos** | **2. The Chiefs** | `cyber-chief`, `traffic-chief` |
| **Executar Tarefa Cirúrgica** | **3. The Specialists** | `db-sage`, `oalanicolas` |
| **Criar/Modificar o Sistema** | **4. The Meta-Builders** | `squad-creator`, `aios-master` |

---

## 1. The Core Squad (O Dia a Dia)
*Agentes que vivem no ciclo de vida de desenvolvimento de software.*

### 🧠 `@pm` (Product Manager)
*   **Melhor Cenário**: Você tem uma ideia vaga ("Quero um app de Uber para Pets") e precisa de um plano concreto (PRD).
*   **Como Usar (Interactive)**: `@pm *create-doc prd`
*   **Como Usar (Mission)**: `Generate a full PRD for a Pet Uber app including features and metrics.`
*   **Diferencial**: Transforma "Vontade" em "Documento de Requisitos". Não coda, planeja.

### 🤝 `@po` (Product Owner)
*   **Melhor Cenário**: Você tem um PRD e precisa quebrar em tarefas executáveis (Backlog) ou aceitar uma entrega.
*   **Como Usar (Interactive)**: `@po *shard-doc docs/prd.md` ou `@po *prioritize-backlog`
*   **Diferencial**: A ponte entre o PM (Sonho) e o Dev (Realidade). Cuida do "O Quê" e "Quando".

### 🏗️ `@architect` (System Architect)
*   **Melhor Cenário**: Precisa definir a stack tecnológica, banco de dados ou estrutura de pastas antes de codar.
*   **Como Usar (Interactive)**: `@architect *create-doc architecture`
*   **Diferencial**: Garante que o prédio não caia. Define padrões que o `@dev` obedece.

### 🎨 `@ux-expert` (UX Designer)
*   **Melhor Cenário**: Precisa de wireframes, fluxos de usuário ou design system antes do frontend.
*   **Como Usar (Interactive)**: `@ux-expert *create-doc ux-design`
*   **Diferencial**: Focado na jornada do usuário e interface, não em lógica de backend.

### 🧱 `@sm` (Scrum Master)
*   **Melhor Cenário**: Criar a próxima User Story para o desenvolvedor pegar. Gerencia o fluxo.
*   **Como Usar (Interactive)**: `@sm *create-next-story`
*   **Diferencial**: O "Gerente de Tráfego" das tarefas. Garante que o `@dev` tenha tudo para trabalhar.

### 💻 `@dev` (Developer)
*   **Melhor Cenário**: "Implemente a Story X". Escrever código, refatorar, corrigir bugs.
*   **Como Usar (Interactive)**: `@dev *develop docs/stories/story-1.md`
*   **Como Usar (Mission)**: `Develop the login feature following strict TDD.` (Ativa YOLO Mode)
*   **Diferencial**: O executor. Transforma Story em Código. Só deve trabalhar com Story aprovada.

### 🕵️ `@qa` (Quality Assurance)
*   **Melhor Cenário**: Validar o que o `@dev` entregou. Criar planos de teste.
*   **Como Usar (Interactive)**: `@qa *review-story docs/stories/story-1.md`
*   **Diferencial**: O "Advogado do Diabo". Seu trabalho é achar falhas no código do `@dev`.

### 🚀 `@devops` (DevOps Engineer)
*   **Melhor Cenário**: Fazer deploy, configurar CI/CD, ou dar push no código (único autorizado).
*   **Como Usar (Interactive)**: `@devops *pre-push`
*   **Diferencial**: O guardião da produção. Responsável pela integridade do repositório.

### 🔎 `@analyst` (Business Analyst)
*   **Melhor Cenário**: Pesquisa de mercado, análise de concorrentes, brainstorm inicial.
*   **Como Usar (Interactive)**: `@analyst *perform-market-research`
*   **Diferencial**: O "Olho Externo". Traz dados de fora para dentro do projeto.

---

## 2. The Chiefs (Os Estrategistas)
*Agentes exclusivos do Path 1 (Bootloaders). Não mexem no código diretamente, eles orquestram squads.*

### 🛡️ `cyber-chief`
*   **Melhor Cenário**: "Temos um vazamento de segurança" ou "Preciso de uma auditoria completa de segurança".
*   **Como Usar**: Prompt de Missão: `Audit our entire infrastructure for vulnerabilities.`
*   **Diferencial**: Não faz o pentest sozinho. Chama `@georgia-weidman` (Red Team) ou `@jim-manico` (AppSec) para executar. É um Router de Segurança.

### 🚦 `traffic-masters-chief`
*   **Melhor Cenário**: "Precisamos escalar nossos anúncios no Facebook e Google".
*   **Como Usar**: Prompt de Missão: `Create a scaling strategy for our e-commerce using Traffic Masters framework.`
*   **Diferencial**: Orquestra especialistas por plataforma (Tier 1) e estratégia (Tier 0). Se é Google, chama `@kasim-aslam`; se é Meta, `@depesh-mandalia`.

### 🛠️ `tools-orchestrator`
*   **Melhor Cenário**: "Crie um framework de vendas para nosso time".
*   **Como Usar**: Prompt de Missão: `Create a comprehensive Sales Playbook framework.`
*   **Diferencial**: Roteia entre Criar, Extrair ou Revisar frameworks. Chama especialistas de domínio (`sales`, `product`, `strategy`).

### ✍️ `copy-chief`
*   **Melhor Cenário**: "Revise toda a copy da nossa landing page".
*   **Como Usar**: Prompt de Missão: `Audit and rewrite the landing page copy for higher conversion.`
*   **Diferencial**: Orquestra especialistas em headlines, e-mail marketing, VSLs, etc.

---

## 3. The Specialists (Os Cirurgiões)
*Agentes de alta precisão para tarefas muito específicas.*

### 🧬 `@oalanicolas` (Mind Cloning Architect)
*   **Melhor Cenário**: "Quero criar um agente que pense e fale igual ao Steve Jobs".
*   **Como Usar**: `@oalanicolas *clone-mind "Steve Jobs"`
*   **Diferencial**: Extrai "Voice DNA" e "Thinking DNA". Cria a `persona` de novos agentes.

### ⚖️ `@pedro-valerio` (Process Absolutist)
*   **Melhor Cenário**: "Valide se esse workflow tem furos lógicos".
*   **Como Usar**: `@pedro-valerio *audit-workflow my-workflow.yaml`
*   **Diferencial**: Obsessivo por processos à prova de falhas. Garante que não existam "becos sem saída".

### 🗄️ `db-sage` (Database Expert)
*   **Melhor Cenário**: "O banco está lento" ou "Faça uma migração complexa de schema".
*   **Como Usar**: Prompt de Missão: `Optimize the slow queries in our order processing module.`
*   **Diferencial**: Especialista profundo em SQL, migrations e RLS. Aplica o princípio KISS rigorosamente.

### 📝 `@sop-extractor`
*   **Melhor Cenário**: "Transforme essa transcrição de reunião em um processo passo-a-passo".
*   **Como Usar**: `@sop-extractor *extract-sop meeting-transcript.txt`
*   **Diferencial**: Especialista em transformar texto não estruturado em Checklists e SOPs.

---

## 4. The Meta-Builders (Os Construtores de Sistema)
*Agentes que constroem e modificam o próprio AIOS.*

### 🏗️ `@squad-creator`
*   **Melhor Cenário**: "Quero criar um novo time de agentes para Marketing".
*   **Como Usar (Interactive)**: `@squad-creator *create-squad marketing`
*   **Diferencial**: Cria a estrutura de pastas, manifestos e configurações para novos squads inteiros.

### 👑 `aios-master` (Orchestrator)
*   **Melhor Cenário**: "Atualize o framework AIOS", "Valide todos os agentes" ou Orquestração Genérica.
*   **Como Usar (Interactive)**: `@aios-master *validate-agents` ou `@aios-master *create agent "novo-agente"`
*   **Diferencial**: O "root" do sistema. Tem permissão para alterar arquivos `.aios-core` e criar novos componentes do framework.

---

## 💡 Regra de Ouro para Uso

1.  **Dúvida?** Use `@aios-master` ou `@pm`. Eles sabem quem chamar.
2.  **Dev Cycle?** O fluxo é `@sm` (Cria Story) -> `@dev` (Coda) -> `@qa` (Valida).
3.  **Deploy?** Somente `@devops`.
4.  **Autonomia Total?** Use os arquivos de `.claude/agents` (ex: `cyber-chief`) com um prompt de missão detalhado.
5.  **Interação Fina?** Use os comandos de `.claude/commands` (ex: `@dev *develop`) para controle passo-a-passo.
