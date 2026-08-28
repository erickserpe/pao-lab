# Pão Lab — Design System

> **Pão Lab — Laboratório de Panificação Artesanal**
> Design System oficial da aplicação acadêmica desenvolvida para a disciplina de Desenvolvimento Web — UTFPR.

---

## 1. Fluxo de Trabalho — Stitch ➔ Figma ➔ Bootstrap 5

O desenvolvimento visual do Pão Lab seguirá um fluxo de **prototipação → sistematização → implementação**, evitando que o design e o código evoluam de forma independente.

### 1.1 Visão geral

```text
┌─────────────────────┐
│       STITCH        │
│ Exploração visual   │
│ e prototipação IA   │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│       FIGMA         │
│ UI Kit + Tokens     │
│ + Componentes       │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│    BOOTSTRAP 5      │
│ Implementação HTML  │
│ + CSS + JS/jQuery   │
└─────────────────────┘
```

### 1.2 Stitch — exploração e prototipação

O Stitch será utilizado como ferramenta de exploração inicial da interface.

Objetivos:

- testar diferentes direções visuais;
- explorar composição das telas;
- definir hierarquia de informação;
- experimentar layouts responsivos;
- validar a disposição dos principais componentes;
- gerar referências visuais antes da implementação.

As três telas principais serão prototipadas:

- `index.html` — Dashboard;
- `experimento.html` — Cadastro de experimento;
- `laboratorio.html` — Histórico e filtros.

O Stitch serve como **referência de design**, e não como fonte definitiva do código.

### 1.3 Figma — transformação em UI Kit

Após a exploração, os elementos aprovados serão reconstruídos no Figma como um **UI Kit estruturado**.

O arquivo deverá conter:

```text
Pão Lab Design System
│
├── Foundations
│   ├── Colors
│   ├── Typography
│   ├── Spacing
│   ├── Radius
│   └── Shadows
│
├── Components
│   ├── Buttons
│   ├── Cards
│   ├── Badges
│   ├── Forms
│   ├── Modals
│   ├── Toasts
│   └── Rating
│
└── Pages
    ├── Dashboard
    ├── Experimento
    └── Laboratório
```

### 1.4 Bootstrap 5 — implementação

O Bootstrap 5 será utilizado como base estrutural.

O princípio será:

> **Bootstrap fornece estrutura e comportamento; o Design System fornece identidade visual.**

Serão utilizados prioritariamente:

- Grid;
- Flex utilities;
- Spacing utilities;
- Forms;
- Cards;
- Buttons;
- Badges;
- Modal;
- Toast;
- Navbar;
- Accordion;
- Alerts.

Não será utilizado Tailwind CSS.

Os componentes Bootstrap serão customizados por meio de CSS próprio e variáveis CSS do Pão Lab, mantendo a estrutura semântica e responsiva do framework.

---

# 2. Paleta de Cores & Psicologia Visual

## 2.1 Conceito cromático

A identidade visual combina três ideias:

**Terra + trigo + laboratório.**

A paleta utiliza tons quentes associados à farinha, madeira e pão assado, equilibrados por um verde escuro que representa fermentação natural, natureza e o aspecto artesanal do processo.

Um tom azul-esverdeado é reservado para informações técnicas, especialmente dados meteorológicos.

### Princípios

- tons claros para superfícies;
- marrom escuro para identidade e elementos de destaque;
- verde para estados positivos e fermentação natural;
- âmbar para atenção e avaliação;
- azul-petróleo para dados climáticos;
- vermelho apenas para erros e validações.

---

## 2.2 Tokens de cores

| Token            | Hexadecimal | RGB             | Função                  | Justificativa                                |
| ---------------- | ----------- | --------------- | ----------------------- | -------------------------------------------- |
| `--pl-brown-900` | `#3B2416`   | `59, 36, 22`    | Texto principal / marca | Marrom profundo associado à crosta e madeira |
| `--pl-brown-700` | `#633B22`   | `99, 59, 34`    | Primário                | Remete ao pão artesanal e forno              |
| `--pl-brown-500` | `#8B5E34`   | `139, 94, 52`   | Destaques               | Tom natural de pão assado                    |
| `--pl-wheat-100` | `#FFF8E8`   | `255, 248, 232` | Fundo principal         | Evoca farinha e papel artesanal              |
| `--pl-wheat-200` | `#F5EBD4`   | `245, 235, 212` | Superfícies secundárias | Sensação de farinha e material natural       |
| `--pl-cream`     | `#FFFDF8`   | `255, 253, 248` | Cards / superfícies     | Alto conforto visual                         |
| `--pl-green-800` | `#164A3A`   | `22, 74, 58`    | Sucesso / natureza      | Fermentação natural e sustentabilidade       |
| `--pl-green-600` | `#28735A`   | `40, 115, 90`   | Estado positivo         | Representa resultado satisfatório            |
| `--pl-teal-800`  | `#155E63`   | `21, 94, 99`    | Clima / dados           | Diferencia informação técnica                |
| `--pl-amber-700` | `#8A5A00`   | `138, 90, 0`    | Avaliação / atenção     | Associado ao dourado da crosta               |
| `--pl-red-700`   | `#A12A2A`   | `161, 42, 42`   | Erro / perigo           | Feedback negativo                            |
| `--pl-gray-700`  | `#4B5563`   | `75, 85, 99`    | Texto secundário        | Hierarquia sem competir com títulos          |
| `--pl-border`    | `#D8CDBB`   | `216, 205, 187` | Bordas                  | Neutro quente em vez de cinza frio           |

---

## 2.3 Tokens CSS

```css
:root {
  --pl-brown-900: #3b2416;
  --pl-brown-700: #633b22;
  --pl-brown-500: #8b5e34;

  --pl-wheat-100: #fff8e8;
  --pl-wheat-200: #f5ebd4;
  --pl-cream: #fffdf8;

  --pl-green-800: #164a3a;
  --pl-green-600: #28735a;

  --pl-teal-800: #155e63;

  --pl-amber-700: #8a5a00;
  --pl-red-700: #a12a2a;

  --pl-gray-700: #4b5563;
  --pl-border: #d8cdbb;
}
```

---

## 2.4 Contraste WCAG

O contraste deverá ser verificado considerando **WCAG 2.2**.

Critérios utilizados:

- **AA — texto normal:** mínimo 4.5:1;
- **AA — texto grande:** mínimo 3:1;
- **AAA — texto normal:** mínimo 7:1;
- **AAA — texto grande:** mínimo 4.5:1.

### Combinações principais

| Texto     | Fundo     | Uso                      | Contraste alvo |
| --------- | --------- | ------------------------ | -------------- |
| `#3B2416` | `#FFF8E8` | Texto principal          | AAA            |
| `#3B2416` | `#FFFDF8` | Texto principal em cards | AAA            |
| `#FFFFFF` | `#633B22` | Botão primário           | AA/AAA         |
| `#FFFFFF` | `#164A3A` | Botão positivo           | AA/AAA         |
| `#FFFFFF` | `#155E63` | Informações climáticas   | AA             |
| `#3B2416` | `#F5EBD4` | Texto em superfície      | AAA            |
| `#4B5563` | `#FFFDF8` | Texto secundário         | AA             |

### Regra de acessibilidade

Cor nunca será utilizada como único indicador de estado.

Exemplo:

```text
❌ Campo obrigatório
```

e não apenas uma borda vermelha.

Da mesma forma:

```text
✓ Experimento salvo
```

em vez de depender somente da cor verde.

---

# 3. Tipografia & Escala Fluida

## 3.1 Fontes

### Headings — Fraunces

**Fraunces** será utilizada nos títulos.

Características:

- serif contemporânea;
- personalidade editorial;
- aparência artesanal;
- boa associação com gastronomia;
- cria contraste com a interface técnica.

Uso:

```text
H1
H2
H3
H4
Títulos de cards especiais
Nome do projeto
```

### Body/UI — Inter

**Inter** será utilizada para corpo e interface.

Características:

- excelente legibilidade;
- números claros;
- adequada para dashboards;
- boa leitura em telas pequenas;
- aparência moderna e tecnológica.

Uso:

```text
parágrafos
labels
inputs
botões
badges
tabelas
métricas
navegação
```

### Par tipográfico

```text
Fraunces
+
Inter
```

A combinação representa:

> **artesanal no conteúdo + técnico na interface.**

---

## 3.2 Importação

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />

<link
  href="https://fonts.googleapis.com/css2?family=Fraunces:wght@600;700&family=Inter:wght@400;500;600;700&display=swap"
  rel="stylesheet"
/>
```

---

## 3.3 Escala tipográfica fluida

| Elemento |         Tamanho | Fórmula                            |
| -------- | --------------: | ---------------------------------- |
| H1       |      2.5–3.5rem | `clamp(2.5rem, 5vw, 3.5rem)`       |
| H2       |       2–2.75rem | `clamp(2rem, 4vw, 2.75rem)`        |
| H3       |        1.5–2rem | `clamp(1.5rem, 3vw, 2rem)`         |
| H4       |     1.25–1.5rem | `clamp(1.25rem, 2vw, 1.5rem)`      |
| Body     |      1–1.125rem | `clamp(1rem, 1.2vw, 1.125rem)`     |
| Small    | 0.8125–0.875rem | `clamp(0.8125rem, 1vw, 0.875rem)`  |
| Caption  |  0.75–0.8125rem | `clamp(0.75rem, 0.9vw, 0.8125rem)` |

### CSS

```css
:root {
  --pl-font-heading: 'Fraunces', serif;
  --pl-font-body: 'Inter', sans-serif;

  --pl-text-h1: clamp(2.5rem, 5vw, 3.5rem);
  --pl-text-h2: clamp(2rem, 4vw, 2.75rem);
  --pl-text-h3: clamp(1.5rem, 3vw, 2rem);
  --pl-text-h4: clamp(1.25rem, 2vw, 1.5rem);

  --pl-text-body: clamp(1rem, 1.2vw, 1.125rem);
  --pl-text-small: clamp(0.8125rem, 1vw, 0.875rem);
  --pl-text-caption: clamp(0.75rem, 0.9vw, 0.8125rem);
}
```

### Pesos

| Uso     | Fonte    | Peso |
| ------- | -------- | ---: |
| H1/H2   | Fraunces |  700 |
| H3/H4   | Fraunces |  600 |
| Corpo   | Inter    |  400 |
| Label   | Inter    |  600 |
| Botão   | Inter    |  600 |
| Métrica | Inter    |  700 |
| Caption | Inter    |  500 |

---

# 4. Framework CSS & Componentes Customizados

## 4.1 Bootstrap 5

O Bootstrap 5 será a base do sistema de layout e dos componentes.

### Grid

Será utilizado o grid responsivo:

```text
xs → sm → md → lg → xl → xxl
```

O conteúdo principal deverá utilizar:

```html
<div class="container"></div>
```

com `container-fluid` reservado para áreas que realmente precisem ocupar toda a largura.

---

## 4.2 Cards de experimento

Os cards são o principal componente visual do Pão Lab.

### Estrutura

```text
┌─────────────────────────────────┐
│ 🥖 CIABATTA          ⭐ 4.8     │
│ Experimento #024                │
│                                 │
│ Hidratação       Fermentação    │
│ 78%              18h             │
│                                 │
│ 🌡 19°C   💧 78%                │
│                                 │
│ [Ver experimento →]             │
└─────────────────────────────────┘
```

### Tokens

```css
.pl-card {
  background: var(--pl-cream);
  border: 1px solid var(--pl-border);
  border-radius: 1rem;
  box-shadow: 0 4px 16px rgba(59, 36, 22, 0.08);
}
```

### Características

- borda discreta;
- raio de 16px;
- sombra suave;
- bastante espaço interno;
- hierarquia clara;
- nenhuma informação essencial depende apenas de cor.

### Hover

```css
.pl-card {
  transition:
    transform 180ms ease,
    box-shadow 180ms ease;
}

.pl-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 8px 24px rgba(59, 36, 22, 0.12);
}
```

O movimento deverá ser discreto.

---

# 4.3 Botões

## Primário

Uso:

- salvar experimento;
- cadastrar;
- confirmar ações principais.

Visual:

```css
.btn-pl-primary {
  background-color: var(--pl-brown-700);
  border-color: var(--pl-brown-700);
  color: #ffffff;
}
```

Hover:

```css
.btn-pl-primary:hover {
  background-color: var(--pl-brown-900);
  border-color: var(--pl-brown-900);
}
```

---

## Secundário

Uso:

- cancelar;
- voltar;
- ações alternativas.

```css
.btn-pl-secondary {
  background-color: transparent;
  border: 1px solid var(--pl-brown-700);
  color: var(--pl-brown-700);
}
```

Hover:

```css
.btn-pl-secondary:hover {
  background-color: var(--pl-wheat-200);
}
```

---

## Estados

Todo botão deverá possuir estados:

```text
Default
Hover
Focus
Active
Disabled
Loading
```

O estado `focus` deverá permanecer claramente visível para navegação por teclado.

---

# 4.4 Badges

Badges representam categorias e estados.

### Categorias

```text
Sourdough
Ciabatta
Baguete
Croissant
Pão rústico
Outro
```

Exemplo:

```html
<span class="badge pl-badge-category"> Sourdough </span>
```

### Clima

```text
🌡 Temperatura
💧 Umidade
```

### Resultado

```text
✓ Excelente
Bom
Atenção
```

Badges não devem substituir textos explicativos.

---

# 4.5 Formulários

O formulário de `experimento.html` será dividido em seções.

```text
1. Identificação
2. Ingredientes
3. Fermentação
4. Condições ambientais
5. Avaliação
6. Observações
```

### Input

Características:

- fundo `#FFFDF8`;
- borda `#D8CDBB`;
- raio de 8px;
- altura mínima de 44px;
- label sempre visível;
- foco claramente identificado.

```css
.form-control,
.form-select {
  min-height: 44px;
  border-color: var(--pl-border);
  background-color: var(--pl-cream);
  color: var(--pl-brown-900);
  border-radius: 0.5rem;
}
```

### Focus

```css
.form-control:focus,
.form-select:focus {
  border-color: var(--pl-brown-500);
  box-shadow: 0 0 0 0.2rem rgba(139, 94, 52, 0.2);
}
```

### Validação

Sucesso:

```text
✓ Dados válidos
```

Erro:

```text
⚠ Informe a quantidade de farinha.
```

A mensagem deve explicar **como corrigir o problema**.

---

# 4.6 Modal

O Modal Bootstrap será utilizado para:

- confirmação de exclusão;
- detalhes rápidos;
- confirmação de ações irreversíveis.

### Estilo

```text
┌──────────────────────────────┐
│ Excluir experimento?      ×  │
│                              │
│ Esta ação não poderá ser     │
│ desfeita.                    │
│                              │
│ [Cancelar] [Excluir]         │
└──────────────────────────────┘
```

O botão destrutivo deverá utilizar `--pl-red-700`.

Não utilizar vermelho em ações normais.

---

# 4.7 Toasts

Toasts serão utilizados para feedback rápido.

Exemplos:

```text
✓ Experimento cadastrado com sucesso.
```

```text
✓ Favorito atualizado.
```

```text
⚠ Não foi possível consultar o clima.
```

O Toast não deverá ser utilizado para mensagens críticas que precisam permanecer na tela.

---

# 5. Ícones & Imagens

## 5.1 Biblioteca

A biblioteca oficial será:

**Bootstrap Icons**

A escolha mantém consistência com Bootstrap 5 e evita misturar diferentes estilos de ícones.

---

## 5.2 Ícones do projeto

### Navegação

| Ícone              | Uso              |
| ------------------ | ---------------- |
| `bi-house`         | Dashboard        |
| `bi-flask`         | Laboratório      |
| `bi-plus-circle`   | Novo experimento |
| `bi-clock-history` | Histórico        |
| `bi-search`        | Busca            |

### Panificação

| Ícone                | Uso          |
| -------------------- | ------------ |
| `bi-basket`          | Ingredientes |
| `bi-box`             | Farinha      |
| `bi-fire`            | Forno        |
| `bi-hourglass-split` | Fermentação  |
| `bi-arrow-repeat`    | Dobras       |

### Clima

| Ícone                 | Uso                |
| --------------------- | ------------------ |
| `bi-thermometer-half` | Temperatura        |
| `bi-droplet`          | Umidade            |
| `bi-cloud-sun`        | Condição climática |
| `bi-cloud-rain`       | Chuva              |
| `bi-sun`              | Sol                |

### Avaliação

| Ícone           | Uso                |
| --------------- | ------------------ |
| `bi-star-fill`  | Estrela preenchida |
| `bi-star`       | Estrela vazia      |
| `bi-heart`      | Favorito           |
| `bi-heart-fill` | Favorito ativo     |

### Ações

| Ícone                     | Uso        |
| ------------------------- | ---------- |
| `bi-pencil`               | Editar     |
| `bi-trash`                | Excluir    |
| `bi-eye`                  | Visualizar |
| `bi-check-circle`         | Sucesso    |
| `bi-exclamation-triangle` | Atenção    |

---

# 5.3 Regras de ícones

Ícones deverão:

- ter significado claro;
- possuir `aria-label` quando forem ações sem texto;
- não substituir labels importantes;
- manter tamanho consistente.

Tamanhos:

```text
16px — informações secundárias
20px — interface
24px — ações principais
32px+ — ilustrações/métricas
```

---

# 5.4 Imagens

As fotografias dos pães serão utilizadas principalmente nos cards de experimento.

Formato preferencial:

```text
WebP
```

Benefícios:

- menor tamanho de arquivo;
- carregamento mais rápido;
- boa qualidade;
- melhor desempenho em dispositivos móveis.

### Proporção

As imagens dos cards deverão utilizar proporção aproximada:

```text
16:9
```

ou

```text
4:3
```

conforme a composição.

### CSS

```css
.experiment-card__image {
  width: 100%;
  aspect-ratio: 16 / 9;
  object-fit: cover;
  border-radius: 0.75rem;
}
```

`object-fit: cover` deverá ser utilizado para evitar distorção.

---

# 5.5 Responsividade das imagens

### Desktop

Imagens maiores podem ocupar toda a largura superior do card.

### Tablet

Redução proporcional sem alterar a composição.

### Mobile

A imagem deverá manter a proporção e nunca ultrapassar a largura do card.

```css
img {
  max-width: 100%;
  height: auto;
}
```

Imagens decorativas deverão possuir `alt=""`.

Imagens de experimentos deverão possuir descrição significativa:

```html
<img src="ciabatta-024.webp" alt="Ciabatta do experimento 024 com miolo aberto" />
```

---

# 6. Microinterações & Prototipagem

As microinterações deverão reforçar a percepção de qualidade sem transformar o projeto em uma interface excessivamente animada.

---

## 6.1 Hover nos cards

Ao passar o mouse:

```text
Card
 ↓
elevação de 3px
 ↓
sombra levemente maior
```

Duração:

```css
180ms
```

Não utilizar animações longas.

---

## 6.2 Estrelas de avaliação

O sistema de avaliação terá cinco estrelas.

Estado inicial:

```text
☆ ☆ ☆ ☆ ☆
```

Ao passar o mouse:

```text
★ ★ ★ ☆ ☆
```

Ao selecionar:

```text
★ ★ ★ ★ ★
```

A seleção deverá apresentar uma pequena transição.

```css
.rating-star {
  transition:
    transform 120ms ease,
    opacity 120ms ease;
}

.rating-star:hover {
  transform: scale(1.12);
}
```

O componente deverá possuir uma alternativa acessível via teclado.

---

## 6.3 Favoritos

O botão de favorito alternará entre:

```text
♡
```

e

```text
♥
```

A preferência será persistida utilizando `localStorage`.

Exemplo conceitual:

```javascript
localStorage.setItem('paoLabFavorites', JSON.stringify(favorites));
```

---

# 6.4 Consulta à Open-Meteo

Ao cadastrar ou visualizar um experimento, a aplicação poderá solicitar os dados climáticos correspondentes à localização e momento do teste.

Estados da interface:

### Antes da consulta

```text
Consultar condições climáticas
```

### Carregando

```text
⟳ Consultando condições climáticas...
```

### Sucesso

```text
🌡 19°C
💧 78%
```

### Falha

```text
⚠ Não foi possível consultar o clima.
Os demais dados do experimento continuam disponíveis.
```

A falha da API não deverá impedir o cadastro do experimento.

---

# 6.5 Loading states

Enquanto uma requisição ao JSON Server estiver acontecendo:

```text
[ spinner ] Salvando experimento...
```

ou utilizar skeletons nos cards:

```text
┌─────────────────────┐
│ ███████████████     │
│ ███████             │
│                     │
│ █████ █████         │
└─────────────────────┘
```

O usuário deverá receber feedback de que o sistema está processando a ação.

---

# 6.6 Feedback de cadastro

Fluxo:

```text
Usuário preenche formulário
          ↓
      Validação
          ↓
       POST API
          ↓
    ┌─────┴─────┐
    ↓           ↓
 Sucesso       Erro
    ↓           ↓
  Toast       Alert
    ↓
 Dashboard
```

Mensagem de sucesso:

```text
✓ Experimento cadastrado com sucesso.
```

---

# 6.7 Transições globais

As transições deverão ser curtas:

```css
--pl-transition-fast: 120ms;
--pl-transition-base: 180ms;
--pl-transition-slow: 300ms;
```

Priorizar:

```css
transform
opacity
box-shadow
```

Evitar animações que alterem excessivamente o layout.

---

# 6.8 Reduced Motion

Usuários que preferirem reduzir animações deverão ser respeitados.

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```

---

# 6.9 Responsividade

O Pão Lab seguirá uma abordagem **mobile-first**, utilizando os breakpoints do Bootstrap 5.

### Mobile

```text
< 576px
```

- uma coluna;
- cards empilhados;
- formulário vertical;
- botões prioritários ocupando largura adequada;
- navegação compacta.

### Tablet

```text
≥ 768px
```

- duas colunas quando apropriado;
- cards em grid;
- formulário parcialmente dividido.

### Desktop

```text
≥ 992px
```

- dashboard em múltiplas colunas;
- cards lado a lado;
- maior aproveitamento horizontal.

---

# Tokens Complementares

## Espaçamento

A escala de espaçamento seguirá prioritariamente o sistema do Bootstrap:

```text
4px
8px
16px
24px
32px
48px
64px
```

Uso:

```text
4px  — microespaçamento
8px  — elementos relacionados
16px — componentes
24px — seções internas
32px — seções
48px — grandes separações
64px — áreas de destaque
```

---

## Border Radius

```css
--pl-radius-sm: 0.375rem;
--pl-radius-md: 0.5rem;
--pl-radius-lg: 1rem;
--pl-radius-pill: 999px;
```

Aplicação:

| Token  | Uso             |
| ------ | --------------- |
| `sm`   | Inputs pequenos |
| `md`   | Inputs / botões |
| `lg`   | Cards / modais  |
| `pill` | Badges          |

---

## Sombras

A interface utilizará sombras suaves.

```css
--pl-shadow-sm: 0 2px 8px rgba(59, 36, 22, 0.06);

--pl-shadow-md: 0 4px 16px rgba(59, 36, 22, 0.08);

--pl-shadow-lg: 0 8px 24px rgba(59, 36, 22, 0.12);
```

O objetivo é criar profundidade sem aparência excessivamente “glassmorphism”.

---

# Princípios de UX do Pão Lab

O Design System deverá seguir cinco princípios:

### 1. Artesanal

A interface deve transmitir a personalidade da panificação artesanal.

### 2. Técnico

Os dados dos experimentos precisam ter apresentação organizada e precisa.

### 3. Simples

O sistema é acadêmico e deve manter um escopo controlado.

### 4. Acessível

Contraste, foco, textos alternativos e navegação por teclado são requisitos do sistema.

### 5. Orientado a experimentação

O usuário deve conseguir responder facilmente:

> **O que eu fiz?**

> **Em quais condições?**

> **Qual foi o resultado?**

> **O que posso mudar no próximo teste?**

---

# Identidade resumida

```text
PÃO LAB
Laboratório de Panificação Artesanal

ARTESANAL
    +
CIÊNCIA
    +
TECNOLOGIA

Fraunces + Inter
Marrom + Trigo + Verde
Bootstrap 5
JavaScript Vanilla + jQuery
JSON Server
localStorage
Open-Meteo API
```

O resultado esperado é uma interface que pareça **um caderno técnico de panificação transformado em aplicação web**, combinando a estética artesanal do pão com a precisão de um laboratório.
