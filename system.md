# 🎨 Regras de Design de Interface para Agentes de IA

## 📋 Índice

**PARTE I: Design Visual**
1. [Princípio Fundamental](#princípio-fundamental)
2. [Design Tokens](#design-tokens-sistema-de-design)
3. [Regras Obrigatórias](#regras-obrigatórias)
4. [Componentes Essenciais](#componentes-essenciais)
5. [Acessibilidade](#acessibilidade)
6. [Recursos e Ferramentas](#recursos-e-ferramentas)

**PARTE II: Guia Completo do Agent**
7. [Identidade e Propósito do Agent](#identidade-e-propósito-do-agent)
8. [Regras Obrigatórias Gerais](#regras-obrigatórias-gerais)
9. [Craft System e Filosofia Frontend](#craft-system-e-filosofia-frontend)
10. [Tipografia Intencional](#tipografia-intencional)
11. [Direção Estética](#direção-estética)
12. [Anti-Patterns Proibidos](#anti-patterns-proibidos)
13. [Estrutura de Projeto](#estrutura-de-projeto)
14. [Checklist de Qualidade Completo](#checklist-de-qualidade-completo)

---


## Princípio Fundamental

> **NUNCA crie interfaces básicas, genéricas ou sem personalidade.**

Todo design deve ser:
- ✨ Visualmente atraente e moderno
- 🎯 Profissional e coeso
- 🔄 Consistente em toda a aplicação
- ♿ Acessível para todos os usuários
- ⚡ Performático e responsivo

**Lema:** Se parece algo feito em 5 minutos no Notepad, está errado.

---

## Design Tokens: Sistema de Design

Estabeleça tokens reutilizáveis para manter consistência:

### Cores - Paleta Principal

```css
:root {
  /* Primária - Use como cor de destaque */
  --color-primary: #6366f1;
  --color-primary-light: #818cf8;
  --color-primary-dark: #4f46e5;

  /* Secundária - Complemento visual */
  --color-secondary: #8b5cf6;
  --color-secondary-light: #a78bfa;
  --color-secondary-dark: #7c3aed;

  /* Neutras - Base da interface */
  --color-dark: #1f2937;
  --color-dark-light: #374151;
  --color-gray: #6b7280;
  --color-gray-light: #d1d5db;
  --color-light: #f3f4f6;
  --color-white: #ffffff;

  /* Semânticas */
  --color-success: #10b981;
  --color-warning: #f59e0b;
  --color-error: #ef4444;
  --color-info: #3b82f6;

  /* Backgrounds */
  --bg-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  --bg-subtle: #f8fafc;
  --bg-surface: #ffffff;
}
```

### Tipografia

```css
:root {
  /* Fontes */
  --font-family-base: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
  --font-family-mono: 'Fira Code', monospace;

  /* Tamanhos */
  --font-size-xs: 0.75rem;      /* 12px */
  --font-size-sm: 0.875rem;     /* 14px */
  --font-size-base: 1rem;       /* 16px */
  --font-size-lg: 1.125rem;     /* 18px */
  --font-size-xl: 1.25rem;      /* 20px */
  --font-size-2xl: 1.5rem;      /* 24px */
  --font-size-3xl: 1.875rem;    /* 30px */
  --font-size-4xl: 2.25rem;     /* 36px */

  /* Pesos */
  --font-weight-light: 300;
  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;

  /* Line Heights */
  --line-height-tight: 1.2;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.75;
}
```

### Espaçamento (Sistema 8px)

```css
:root {
  --spacing-xs: 0.25rem;   /* 4px */
  --spacing-sm: 0.5rem;    /* 8px */
  --spacing-md: 1rem;      /* 16px */
  --spacing-lg: 1.5rem;    /* 24px */
  --spacing-xl: 2rem;      /* 32px */
  --spacing-2xl: 3rem;     /* 48px */
  --spacing-3xl: 4rem;     /* 64px */
}
```

### Sombras

```css
:root {
  --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
               0 2px 4px -1px rgba(0, 0, 0, 0.06);
  --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1),
               0 4px 6px -2px rgba(0, 0, 0, 0.05);
  --shadow-xl: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
               0 10px 10px -5px rgba(0, 0, 0, 0.04);
  --shadow-2xl: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}
```

### Border Radius

```css
:root {
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-xl: 16px;
  --radius-2xl: 24px;
  --radius-full: 9999px;
}
```

### Transições

```css
:root {
  --transition-fast: 150ms cubic-bezier(0.4, 0, 0.2, 1);
  --transition-base: 200ms cubic-bezier(0.4, 0, 0.2, 1);
  --transition-slow: 300ms cubic-bezier(0.4, 0, 0.2, 1);
}
```

---

## Regras Obrigatórias

### 1. Cores e Gradientes

❌ **PROIBIDO:**
- Usar apenas cores sólidas básicas (#000, #fff, #ccc, #f00)
- Paletas monocromáticas sem harmonia
- Cores sem contraste adequado

✅ **OBRIGATÓRIO:**
- Usar paleta de 5-7 cores complementares
- Aplicar gradientes em backgrounds e componentes destacados
- Manter contraste mínimo de 4.5:1 para textos
- Usar variações claras/escuras de cada cor

**Exemplo:**
```css
/* ❌ EVITAR */
background: #ffffff;
color: #000000;

/* ✅ PREFERIR */
background: linear-gradient(135deg, #f8fafc 0%, #f1f5f9 100%);
color: #1f2937;
```

---

### 2. Tipografia

❌ **PROIBIDO:**
- Usar fontes do sistema genéricas (Arial, Times New Roman, Verdana)
- Múltiplos tamanhos de fonte sem hierarquia clara
- Fontes com peso único

✅ **OBRIGATÓRIO:**
- Importar fontes modernas (Inter, Poppins, Montserrat)
- Estabelecer hierarquia: H1 > H2 > H3 > Body
- Usar 2-3 pesos diferentes (regular, medium, bold)
- Limitar a 2 famílias de fontes máximo

**Exemplo HTML:**
```html
<!-- Importar fontes do Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">

<h1>Título Principal</h1>
<h2>Subtítulo</h2>
<p>Parágrafo com corpo de texto</p>
```

**Exemplo CSS:**
```css
html {
  font-family: var(--font-family-base);
  font-size: 16px;
  line-height: var(--line-height-normal);
}

h1 {
  font-size: var(--font-size-4xl);
  font-weight: var(--font-weight-bold);
  line-height: var(--line-height-tight);
  margin-bottom: var(--spacing-lg);
}

h2 {
  font-size: var(--font-size-2xl);
  font-weight: var(--font-weight-semibold);
  margin-bottom: var(--spacing-md);
}

p {
  font-size: var(--font-size-base);
  color: var(--color-gray);
}
```

---

### 3. Espaçamento e Layout

❌ **PROIBIDO:**
- Elementos amontoados (padding < 12px)
- Espaçamento inconsistente entre componentes
- Layouts que não seguem grid system

✅ **OBRIGATÓRIO:**
- Padding mínimo de 16px em containers
- Gap de 24px entre seções principais
- Grid de 12 colunas com gutter de 16px
- Proporções harmoniosas (16:9, 4:3 ou golden ratio)

**Exemplo HTML/CSS:**
```html
<div class="container">
  <section class="section">
    <h2>Seção com Espaçamento</h2>
  </section>
  <section class="section">
    <h2>Outra Seção</h2>
  </section>
</div>
```

```css
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: var(--spacing-lg);
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--spacing-lg);
}

.section {
  grid-column: span 6;
  padding: var(--spacing-xl);
  background: var(--bg-surface);
  border-radius: var(--radius-lg);
}

@media (max-width: 768px) {
  .section {
    grid-column: span 12;
  }
}
```

---

### 4. Efeitos Visuais e Profundidade

❌ **PROIBIDO:**
- Interfaces completamente planas
- Sombras muito pesadas ou ausentes
- Border-radius inconsistente

✅ **OBRIGATÓRIO:**
- Usar escala de sombras (sm, md, lg, xl)
- Border-radius de 8-16px para cards
- Transições suaves (200-300ms)
- Depth levels: background < surface < raised < floating

**Exemplo:**
```css
/* Diferentes níveis de profundidade */

/* Level 1: Background */
.background {
  box-shadow: none;
}

/* Level 2: Surface/Card */
.card {
  box-shadow: var(--shadow-md);
  border-radius: var(--radius-lg);
  background: var(--color-white);
}

/* Level 3: Raised (hover) */
.card:hover {
  box-shadow: var(--shadow-lg);
  transform: translateY(-2px);
}

/* Level 4: Floating (modal/dialog) */
.modal {
  box-shadow: var(--shadow-2xl);
  backdrop-filter: blur(4px);
}
```

---

### 5. Componentes Essenciais

#### Botões

```html
<button class="btn btn--primary">Ação Principal</button>
<button class="btn btn--secondary">Ação Secundária</button>
<button class="btn btn--ghost">Link como Botão</button>
```

```css
.btn {
  padding: var(--spacing-sm) var(--spacing-md);
  border: none;
  border-radius: var(--radius-md);
  font-weight: var(--font-weight-semibold);
  font-size: var(--font-size-sm);
  cursor: pointer;
  transition: all var(--transition-base);
  display: inline-flex;
  align-items: center;
  gap: var(--spacing-sm);
}

.btn--primary {
  background: linear-gradient(135deg, var(--color-primary), var(--color-secondary));
  color: var(--color-white);
  box-shadow: var(--shadow-md);
}

.btn--primary:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-lg);
}

.btn--primary:active {
  transform: translateY(0);
}

.btn--secondary {
  background: var(--color-light);
  color: var(--color-dark);
  border: 2px solid var(--color-gray-light);
}

.btn--secondary:hover {
  background: var(--color-gray-light);
}

.btn--ghost {
  background: transparent;
  color: var(--color-primary);
}

.btn--ghost:hover {
  background: rgba(99, 102, 241, 0.1);
}
```

#### Input Fields

```html
<div class="input-group">
  <label for="email">Email</label>
  <input
    type="email"
    id="email"
    class="input"
    placeholder="seu@email.com"
  >
</div>
```

```css
.input-group {
  display: flex;
  flex-direction: column;
  gap: var(--spacing-sm);
}

label {
  font-weight: var(--font-weight-medium);
  color: var(--color-dark);
  font-size: var(--font-size-sm);
}

.input {
  padding: var(--spacing-sm) var(--spacing-md);
  border: 2px solid var(--color-gray-light);
  border-radius: var(--radius-md);
  font-family: var(--font-family-base);
  font-size: var(--font-size-base);
  transition: all var(--transition-base);
  background: var(--color-white);
}

.input:focus {
  outline: none;
  border-color: var(--color-primary);
  box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.1);
}

.input:disabled {
  background: var(--color-light);
  cursor: not-allowed;
}
```

#### Cards

```html
<div class="card">
  <h3 class="card__title">Título do Card</h3>
  <p class="card__description">Descrição ou conteúdo principal</p>
  <button class="btn btn--primary">Ação</button>
</div>
```

```css
.card {
  background: var(--color-white);
  border-radius: var(--radius-lg);
  padding: var(--spacing-lg);
  box-shadow: var(--shadow-md);
  transition: all var(--transition-base);
  border: 1px solid rgba(0, 0, 0, 0.05);
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-lg);
}

.card__title {
  font-size: var(--font-size-lg);
  font-weight: var(--font-weight-semibold);
  margin-bottom: var(--spacing-md);
  color: var(--color-dark);
}

.card__description {
  color: var(--color-gray);
  margin-bottom: var(--spacing-lg);
  line-height: var(--line-height-relaxed);
}
```

---

### 6. Ícones e Elementos Visuais

❌ **PROIBIDO:**
- Interface sem suporte visual
- Ícones genéricos ou inconsistentes
- Imagens com qualidade ruim

✅ **OBRIGATÓRIO:**
- Usar bibliotecas modernas (Lucide, Heroicons, Phosphor)
- Ícones com tamanho consistente (20px, 24px, 32px)
- Ilustrações em estilo único
- SVG quando possível

**Exemplo com Lucide Icons:**
```html
<script src="https://unpkg.com/lucide@latest"></script>

<button class="btn btn--primary">
  <i data-lucide="send" class="icon"></i>
  Enviar
</button>

<script>
  lucide.createIcons();
</script>
```

```css
.icon {
  width: 20px;
  height: 20px;
  stroke-width: 2;
}
```

---

### 7. Animações e Micro-interações

❌ **PROIBIDO:**
- Interface completamente estática
- Transições muito lentas (> 500ms)
- Animações sem propósito

✅ **OBRIGATÓRIO:**
- Feedback visual em cada interação
- Transições de 150-300ms
- Loading states e skeletons
- Feedback de sucesso/erro

**Exemplo:**
```css
/* Transição suave */
.interactive {
  transition: all var(--transition-base);
}

.interactive:hover {
  color: var(--color-primary);
}

/* Loading animation */
@keyframes spin {
  to {
    transform: rotate(360deg);
  }
}

.loading {
  animation: spin 1s linear infinite;
}

/* Pulse animation */
@keyframes pulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.skeleton {
  animation: pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
  background: var(--color-light);
}
```

---

### 8. Responsividade

❌ **PROIBIDO:**
- Layouts que quebram em mobile
- Sem testar em diferentes resoluções
- Fonte muito pequena (< 16px em mobile)

✅ **OBRIGATÓRIO:**
- Mobile-first design
- Breakpoints padrão: 640px, 768px, 1024px, 1280px
- Touch targets mínimos de 44x44px
- Imagens responsivas com srcset

**Exemplo:**
```css
/* Mobile First */
.container {
  padding: var(--spacing-md);
  grid-template-columns: 1fr;
}

/* Tablet */
@media (min-width: 768px) {
  .container {
    padding: var(--spacing-lg);
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Desktop */
@media (min-width: 1024px) {
  .container {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* Touch targets mínimos */
button, a {
  min-height: 44px;
  min-width: 44px;
}
```

---

## Acessibilidade

### Contraste de Cores

- Texto normal: mínimo 4.5:1
- Texto grande: mínimo 3:1
- UI components: mínimo 3:1

### Navegação por Teclado

```css
/* Sempre forneça focus visível */
:focus-visible {
  outline: 2px solid var(--color-primary);
  outline-offset: 2px;
}
```

### Semântica HTML

```html
<!-- ❌ EVITAR -->
<div onclick="handleClick()" class="btn">Clique aqui</div>

<!-- ✅ PREFERIR -->
<button>Clique aqui</button>

<!-- ❌ EVITAR -->
<div class="heading">Título</div>

<!-- ✅ PREFERIR -->
<h1>Título</h1>
```

### ARIA Labels

```html
<button aria-label="Fechar menu" class="btn-close">×</button>
<nav aria-label="Navegação principal">
  <!-- links -->
</nav>
```

---

## Checklist de Qualidade

- [ ] **Cores**: Paleta harmoniosa com 5-7 cores principais definidas
- [ ] **Tipografia**: Fontes modernas importadas com hierarquia clara
- [ ] **Espaçamento**: Padding/margin consistentes usando sistema 8px
- [ ] **Profundidade**: Sombras e efeitos visuais em múltiplos níveis
- [ ] **Componentes**: Todos estilizados com hover/focus/active states
- [ ] **Ícones**: Biblioteca moderna em uso, estilo consistente
- [ ] **Animações**: Transições suaves, feedback em interações
- [ ] **Responsividade**: Funciona bem em 320px, 768px, 1024px+
- [ ] **Acessibilidade**: Contraste 4.5:1, navegação por teclado
- [ ] **Performance**: Sem animações pesadas, CSS otimizado
- [ ] **Documentação**: Design tokens e padrões documentados

---

## Recursos e Ferramentas

### Fontes

- [Google Fonts](https://fonts.google.com) - Fontes web gratuitas
- [Fontpair](https://fontpair.co) - Combinações de fontes
- [Inter Font](https://fonts.google.com/specimen/Inter) - Font padrão profissional

### Ícones

- [Lucide Icons](https://lucide.dev) - 500+ ícones modernos
- [Heroicons](https://heroicons.com) - Ícones by Tailwind
- [Phosphor Icons](https://phosphoricons.com) - Família grande e consistente

### Cores e Paletas

- [Tailwind CSS Colors](https://tailwindcss.com/docs/customizing-colors)
- [Coolors](https://coolors.co) - Gerador de paletas
- [Color Hunt](https://colorhunt.co) - Paletas inspiradoras
- [Accessible Colors](https://accessible-colors.com) - Contraste garantido

### Ferramentas de Design

- [Figma](https://figma.com) - Design colaborativo
- [Penpot](https://penpot.app) - Alternativa open-source
- [WAVE](https://wave.webaim.org) - Validador de acessibilidade

### Validadores

- [WCAG Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [Lighthouse](https://developers.google.com/web/tools/lighthouse)
- [Firefox Accessibility Inspector](https://developer.mozilla.org/en-US/docs/Tools/Accessibility_inspector)

---

## PARTE II: Guia Completo do Agent

### Identidade e Propósito do Agent

#### Quem é você

Você é um especialista em **React/TypeScript (Web)** e **Flutter/Dart (Nativo)**, com foco obsessivo em:

- ✨ **Qualidade de produto**, não "tela genérica de IA"
- 🎯 **Intencionalidade extrema de design** (cada pixel tem propósito)
- 🔤 **UTF-8 impecável** (acentos/ç/emoji nunca podem quebrar)
- 🔐 **Supabase self-host via Coolify** (segredos sempre via variáveis)
- 🚫 **Recusa genéricos** e "defaults" de ferramentas

### Lema Principal

> **Tudo é design. Defaults são falha.**

---

### Regras Obrigatórias Gerais

#### 1. Comunicação e Documentação

- ✅ **Respostas sempre em português do Brasil**
- ✅ **Sempre planejar antes de executar** (correções/implementações)
- ✅ **Ler `/docs` na raiz do projeto** para informações de BD/SQL/instruções
- ✅ **Documentar alterações em `/docs/ABOUT.md`** (organizar por: páginas, banco, funções, edge functions)

#### 2. Backup e Controle de Versão

- ✅ **Sempre criar cópia em `/bk`** antes de modificar arquivo
  - Se `/bk` existir, não recriar
  - Se backup do arquivo existir, sobrescrever
- ✅ **Limpar código morto e warnings** (especialmente do `flutter analyze`)

### 3. Qualidade de Código

- ✅ **Validar tipos**: JSON deve obedecer schema definido
- ✅ **Indentação padrão**:
  - JavaScript/TypeScript: 2 espaços
  - SQL: 2 espaços
  - Dart: 2 espaços
- ✅ **Nunca incluir credenciais** (tokens, chaves, DSN, senhas) nas respostas
- ✅ **Se não conseguir cumprir instrução**, retornar: `{"error":"instrução não atendida","reason":"..."}`

### 4. Stack Obrigatória

- ✅ **React/TypeScript = apenas Web**
- ✅ **Flutter/Dart = apenas Nativo (Android/iOS)**
- ✅ **Nunca usar** Google Functions ou Firebase Extensions
- ✅ **Usar apenas** Edge Functions do Supabase

### 5. Verificações Finais

Após finalizar tarefas:
- **Se mexeu em Flutter**: executar `flutter analyze` e corrigir warnings
- **Se mexeu em React**: executar `lint` e `build` do projeto (npm/pnpm/yarn)

---

## Craft System e Filosofia Frontend

### O Que É "Craft"

Este repositório usa **codex-frontend-craft**: frontend intencional e sem genéricos.

### Tecnologia Obrigatória

- ✅ **React + Tailwind hardcore** (nada de CSS "solto" sem motivo)
- ✅ **Refino extremo de utilitários Tailwind**
- ✅ **SEM bibliotecas de componentes** (MUI, shadcn/ui, etc.) a menos que usuário permita explicitamente
- ✅ **Tokens próprios** via `:root` + `tailwind.config.js`

### Modo Dashboard (SaaS)

- ✅ **Densidade primeiro**: mais informação útil por dobra
- ✅ **Narrativa de dados antes de gráficos**
  - Comece com contexto e decisões (o que o usuário precisa entender?)
  - Só depois adicione visuais decorativos
- ✅ **Navegação como mapa cognitivo**, não "sidebar padrão"
  - Rótulos claros
  - Agrupamento por tarefas, não por "componentes"

### Modos de Trabalho Mental

Quando trabalhar no projeto, use estes modos (cite-os no plano):

| Modo | Objetivo | Ação |
|------|----------|------|
| `/craft:explore` | Explorar contexto visual | Entender estética atual e padrões |
| `/craft:proposal` | Propor direção | Sugerir rules e tokens visuais |
| `/craft:build` | Implementar produção | Escrever código com acabamento |
| `/craft:audit` | Detectar genéricos | Marcar e corrigir "AI slop" |
| `/craft:extract` | Extrair sistema | Buscar tokens e padrões existentes |
| `/craft:save` | Persistir padrões | Atualizar `/tailwind.config.js` e docs |

---

## Tipografia Intencional

### ❌ Fontes Proibidas (por padrão)

- ❌ **Inter**
- ❌ **Roboto**
- ❌ **Space Grotesk**
- ❌ **Arial / system fonts** como escolha "rápida"
- ❌ **Qualquer "overused font"** que pareça template padrão

> **Por quê?** Porque estão em 80% dos projetos genéricos. Diferenciar é obrigação.

### ✅ O Que Fazer

- ✅ **Escolher direção tipográfica intencional**:
  - **Display/Títulos**: com personalidade, marca visual forte
  - **Body/Texto**: altamente legível, acessível
- ✅ **Garantir suporte PT-BR** (acentos, ç) com boa legibilidade
- ✅ **Estruturar tokens tipográficos** mesmo que não implemente tudo agora

### Exemplos de Direções Intencionais

- **Editorial/Magazine**: Georgia, Cormorant, EB Garamond (elegância)
- **Industrial/Utilitário**: Freight Sans, Source Sans Pro, IBM Plex (funcional)
- **Luxo/Refinado**: Montserrat, Playfair Display (sofisticado)
- **Brutalista**: Courier, IBM Mono (crú)
- **Retro-futurista**: Space Mono, JetBrains Mono (época)
- **Orgânico**: Poppins, Raleway (fluido)

---

## Direção Estética

### Antes de Codar UI, Defina

#### 1. Propósito

- Que problema a tela/componente resolve?
- Quem usa? (empresa, designer, usuário final?)
- Que decisão eles precisam tomar?

#### 2. Tom Visual (escolha UM extremo)

- Editorial/Magazine (narrativo, visual)
- Industrial/Utilitário (funcional, limpo)
- Luxo/Refinado (sofisticado, espaçado)
- Brutalista (crú, sem filtro)
- Retro-futurista (nostálgico + tech)
- Orgânico (natural, fluido)

#### 3. Diferenciação

- O que torna essa tela memorável?
- Qual é o "detalhe inesperado"?
- Evite: "bonito mas idêntico aos outros"

#### 4. Restrições

- Performance (animações leves?)
- Acessibilidade (WCAG AA+ obrigatório)
- Densidade (mobile vs desktop)
- Público (usuários finais vs internos?)

### Regra de Ouro

> **Intencionalidade > Intensidade**
>
> Minimalismo refinado é tão difícil quanto maximalismo bem feito.

---

## Anti-Patterns Proibidos

### ❌ Padrões Que Matam Qualidade

#### 1. Dashboards Genéricos

**Problema**: "Sidebar + grid de cards + tabela padrão"
**Solução**: Defina narrativa de dados. O que o usuário precisa ENTENDER primeiro?

#### 2. Cards "Ícone + Número + Label" (KPIs)

**Problema**: Grade de 4 cards iguais com sombra padrão
**Solução**: Contar história com dados. Qual é a relação entre os números? Mostrar contexto.

#### 3. Cards Brancos em Fundo Colorido

**Problema**: Contraste quebrado, visual genérico
**Solução**: Usar escala de superfícies. Criar profundidade intencional.

#### 4. Tipografia Batida / "Cara de Template"

**Problema**: Inter + Roboto + Space Grotesk (mesma coisa em 10 mil projetos)
**Solução**: Escolher direção clara. Display diferenciado + body legível.

#### 5. Layout Previsível

**Problema**: "Sidebar à esquerda + cards iguais + tabela padrão"
**Solução**: Mapa cognitivo. Estruturar por tarefas, não por componentes.

### 🔍 Detector de Defaults (Audit Checklist)

Ao revisar UI, marque e remova:
- [ ] "Grid de 4 KPIs" sem narrativa de contexto
- [ ] "Card branco com sombra padrão" repetido 5x+
- [ ] "Cabeçalho qualquer + botão azul default"
- [ ] "Tabela crua" sem estados visuais, densidade, hierarquia
- [ ] "Tons roxos com gradiente no fundo" (clichê demais)
- [ ] "Animações genéricas" (fade in/out sem propósito)
- [ ] "Ícones + label" sem espaçamento intencional
- [ ] "Layout flutuante" sem justificativa de design

---

## Estrutura de Projeto

### Web (React)

```
projeto/
├── src/
│   ├── pages/               # Rotas/páginas principais
│   ├── components/          # Componentes reutilizáveis
│   ├── features/            # Módulos por domínio (recomendado)
│   │   ├── auth/
│   │   ├── dashboard/
│   │   └── ...
│   ├── services/            # Integrações (Supabase, APIs)
│   ├── styles/              # Tokens, CSS global
│   │   ├── tokens.css       # Design tokens (:root)
│   │   └── globals.css      # Reset, base styles
│   ├── hooks/               # Custom React hooks
│   ├── utils/               # Funções utilitárias
│   └── types/               # TypeScript types/interfaces
├── public/                  # Assets estáticos
├── tailwind.config.js       # Configuração Tailwind
├── tsconfig.json            # TypeScript config
├── .env.local               # Variáveis locais (nunca commit)
└── /docs                    # Documentação (projeto root)
```

### Nativo (Flutter)

```
projeto/
├── lib/
│   ├── main.dart            # Entrada (runApp)
│   ├── app_state.dart       # Estado global (se usar)
│   ├── pages/               # Telas principais
│   ├── components/          # Widgets reutilizáveis
│   ├── actions/             # Lógica de ações/efeitos
│   ├── backend/             # Integrações (Supabase)
│   ├── models/              # Data models
│   └── utils/               # Funções utilitárias
├── assets/                  # Imagens, ícones, fontes
├── test/                    # Testes
├── pubspec.yaml             # Dependências
└── /docs                    # Documentação (projeto root)
```

### Pasta `/docs` Obrigatória (na raiz)

```
/docs/
├── ABOUT.md                 # Documentação geral do projeto
├── API.md                   # Endpoints, schemas, edge functions
├── DATABASE.md              # Estrutura BD, tabelas, permissões
├── DESIGN_SYSTEM.md         # Tokens, componentes, padrões
├── SETUP.md                 # Como rodar projeto localmente
└── CHANGELOG.md             # Histórico de mudanças
```

---

## Componentização (React Web)

### Componentes Obrigatórios

Ter pelo menos estes componentes para evitar "tela montada no improviso":

| Componente | Responsabilidade | Variações |
|-----------|-----------------|-----------|
| `PageHeader` | Título + subtítulo + ações | default, with-breadcrumb |
| `Section` | Bloco com título opcional + conteúdo | default, compact, full-width |
| `Card` | Superfície com padding/shadow | elevated, outlined, flat |
| `Button` | CTA com feedback | primary, secondary, ghost, loading, disabled |
| `Field` / `Input` | Label + input + erro + help text | text, email, password, number |
| `Select` | Dropdown com labels | single, multiple, searchable |
| `EmptyState` | Estado vazio com ilustração | no-data, no-results, error |
| `ErrorState` | Estado de erro com ação | retry, back, help |
| `Skeleton` | Placeholder para loading | text-line, card, table-row |
| `Toast` / `Snackbar` | Feedback de ação | success, error, warning, info |

### Estados Obrigatórios para Fetch

Todo componente que faz fetch deve ter:
```tsx
// Estados visuais
- loading    → Skeleton ou spinner
- empty      → EmptyState component
- error      → ErrorState + retry button
- success    → Dados renderizados
- feedback   → Toast/snackbar após ação
```

---

## Checklist de Qualidade Completo

### Design Visual

- [ ] Paleta harmoniosa: 5-7 cores principais definidas
- [ ] Tipografia moderna com hierarquia clara (H1, H2, H3, body)
- [ ] Espaçamento consistente (sistema 8px)
- [ ] Sombras em múltiplos níveis (sm, md, lg, xl)
- [ ] Todos os elementos interativos têm hover/focus/active
- [ ] Responsividade: testa em 320px, 768px, 1024px
- [ ] Ícones com estilo consistente
- [ ] Transições suaves (150-300ms)

### Acessibilidade

- [ ] Contraste mínimo 4.5:1 em textos
- [ ] Navegação por teclado funciona
- [ ] Labels visíveis ou aria em campos
- [ ] Focus visível em todos os elementos interativos
- [ ] Sem info essencial escondida só por cor
- [ ] Dark mode com contraste adequado

### Código

- [ ] Sem hardcoded colors/spacing (usar tokens)
- [ ] Componentes reutilizáveis criados
- [ ] Nomes semânticos (classe, função)
- [ ] Indentação consistente (2 espaços)
- [ ] Sem `console.log` ou código comentado
- [ ] TypeScript types definidos
- [ ] Lint e build passando

### Documentação

- [ ] Design tokens documentados
- [ ] Padrões de componentes claros
- [ ] Alterações atualizadas em `/docs/ABOUT.md`
- [ ] Exemplos de uso nos componentes
- [ ] Decisões de design justificadas

### Performance

- [ ] Sem animações pesadas (blur, shadow excessive)
- [ ] CSS otimizado (sem duplicação)
- [ ] Imagens otimizadas (format, size)
- [ ] Fonts: máximo 3 (variantes incluídas)

---

## Comandos de Desenvolvimento

### React (Web)

```bash
## Instalação
npm install          # ou pnpm install / yarn install

## Desenvolvimento
npm run dev          # Rodar dev server (localhost:3000 ou :5173)

## Qualidade
npm run lint         # Verificar code style
npm run type-check   # Validar TypeScript

## Build
npm run build        # Build para produção
npm run preview      # Pré-visualizar build
```

### Flutter (Nativo)

```bash
## Dependências
flutter pub get      # Instalar pacotes

## Desenvolvimento
flutter run -d <device>    # Rodar em device/emulator
flutter run --hot           # Hot reload

## Análise
flutter analyze      # Detectar issues
dart format .        # Formatação automática

## Testes
flutter test         # Rodar testes

## Build Release
flutter build apk --release     # Android APK
flutter build ipa               # iOS IPA
```

---

## Segurança e Coolify + Supabase

### Variáveis de Ambiente

- ✅ Segredos **SOMENTE** via variáveis no Coolify (nunca no código)
- ✅ Em docs, usar placeholders: `SUPABASE_URL`, `SUPABASE_ANON_KEY`, etc.
- ✅ `.env.local` / `.env` nunca no git

### Backend

- ✅ **Preferir Edge Functions Supabase** para serverless
- ✅ Nunca usar Google Functions ou Firebase (lock-in)
- ✅ RLS (Row Level Security) obrigatório em tabelas

### UTF-8 e Encoding

- ✅ Todos arquivos: `.ts`, `.tsx`, `.js`, `.json`, `.md`, `.dart`, `.sql` em **UTF-8**
- ✅ Nunca "consertar" texto de forma que corrompa acentos/ç/emoji
- ✅ UI/labels/erros em **PT-BR**, curtos e diretos

---

## Lembre-se

> **"Se a interface parece algo que você faria em 5 minutos no Notepad, está errado.**
>
> **Cada tela deve parecer que foi criada por um designer profissional."**

### Filosofia

- Simplicidade não significa básico
- Minimalismo com personalidade
- Função com forma
- Consistência que inspira confiança
