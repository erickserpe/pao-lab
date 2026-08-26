# 🥖 Pão Lab — Laboratório de Panificação Artesanal

> Aplicação web responsiva para registro, acompanhamento e análise de experimentos de panificação artesanal integrada a dados meteorológicos em tempo real.

---

## 👤 Autor

- **Nome Completo:** Erick Serpe
- **Curso:** Tecnologia em Sistemas para Internet / Ciência da Computação
- **Instituição:** Universidade Tecnológica Federal do Paraná (UTFPR)

---

## 📝 Descrição do Projeto

O **Pão Lab** é uma aplicação voltada para padeiros artesanais e entusiastas de _sourdough_ (fermentação natural) registrarem e compararem seus experimentos de massa. Em vez de receitas estáticas, o sistema registra ensaios técnicos variando a hidratação (%), os tipos de farinha, a porcentagem de levain e os tempos de fermentação.

A aplicação integra a **Open-Meteo API** para consultar automaticamente a temperatura e a umidade da cidade no momento do teste, correlacionando o clima com a qualidade final do miolo, crosta e fermentação. Os dados dos experimentos são persistidos via **JSON Server** (REST API fake), enquanto as preferências da interface (como favoritos e tema) são gerenciadas no `localStorage`.

---

## 🎨 Prototipação & Design System

- **🎨 Protótipo no Figma:** [Acessar Projeto no Figma](https://www.figma.com/)
- **📐 Design System:** [Documentação de tokens e guia de estilo](docs/architecture.md#3-design-tokens-identidade-visual)

---

## 🛠️ Framework CSS & Dependências

- **Framework CSS:** [Bootstrap 5](https://getbootstrap.com/)
- **Bibliotecas & Dependências JavaScript:**
  - [Bootstrap 5 Bundle JS](https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js) (Navbar, Cards, Modais, Tooltips)
  - [jQuery](https://jquery.com/) (Manipulação do DOM e animações)
  - [jQuery Mask Plugin](https://cdnjs.cloudflare.com/ajax/libs/jquery.mask/1.14.16/jquery.mask.min.js) (Máscaras de inputs no formulário)
  - [Open-Meteo API](https://open-meteo.com/) (Fetch API meteorológica pública)
  - [JSON Server](https://github.com/typicode/json-server) (Backend RESTful fake local)

---

## 🌐 Link para o Site em Produção

- **URL do Deploy (GitHub Pages):** [https://erickserpe.github.io/pao-lab/](https://erickserpe.github.io/pao-lab/)

---

## ✅ Checklist de Funcionalidades (IDs dos RAs)

### RA1 - Frameworks CSS e Layouts Responsivos

- [x] **ID 01:** Prototipação de telas mobile e desktop no Figma.
- [ ] **ID 02:** Layout responsivo construído com Grid e Flexbox do Bootstrap 5.
- [ ] **ID 03:** Seções customizadas com layout fluido em CSS puro (Flexbox/Grid).
- [ ] **ID 04:** Utilização de componentes Bootstrap (Cards, Navbar, Modais e Badges).
- [ ] **ID 05:** Estilização fluida com unidades relativas (`rem`, `em`, `%`, `vh`, `vw`).
- [x] **ID 06:** Design System consistente aplicado (paleta de trigo/crosta, tipografia).
- [ ] **ID 07:** Uso de Sass (SCSS) com variáveis, mixins e funções para modularização.
- [ ] **ID 08:** Tipografia fluida e responsiva com `clamp()` e media queries _mobile-first_.
- [ ] **ID 09:** Responsividade de imagens usando `object-fit: cover` e containers flexíveis.
- [ ] **ID 10:** Otimização de imagens do projeto no formato WebP.

### RA2 - Formulários e Validações no Cliente

- [ ] **ID 11:** Validação nativa HTML5 nos formulários (`required`, `min`, `max`).
- [ ] **ID 12:** Validação customizada via Expressões Regulares (REGEX).
- [ ] **ID 13:** Uso de elementos de seleção (`<select>`, `<input type="radio">`, `<input type="checkbox">`).
- [ ] **ID 14:** Leitura e escrita no `localStorage` para salvar favoritos e estado do tema.

### RA3 - Ferramentas de Otimização e Workflow

- [x] **ID 15:** Ambiente configurado com Node.js e NPM para gerenciamento de dependências.
- [x] **ID 16:** Versionamento Git/GitHub correto na branch `main` e arquivo `.gitignore`.
- [x] **ID 17:** Arquivo `README.md` padronizado conforme o template e matriz da UTFPR.
- [x] **ID 18:** Organização de arquivos de forma modular (`/docs`, `/css`, `/js`, `/assets`).
- [x] **ID 19:** Configuração de linters e formatadores (ESLint, Prettier).

### RA4 - JavaScript e Bibliotecas Externas

- [ ] **ID 20:** Manipulação de eventos e elementos do DOM utilizando jQuery.
- [ ] **ID 21:** Integração do jQuery Mask Plugin para aplicação de máscaras nos formulários.

### RA5 - Requisições Assíncronas (APIs)

- [ ] **ID 22:** Requisições assíncronas (`POST`/`PUT`/`DELETE`) para o JSON Server.
- [ ] **ID 23:** Requisições assíncronas (`GET`) para renderizar lista e métricas no dashboard.
- [ ] **ID 24:** Requisições assíncronas para a **Open-Meteo API** com tratamento de erros (`try/catch`).

---

## ⚙️ Instruções de Execução

### Pré-requisitos

- Node.js (v18 ou superior)
- Git
- Navegador Web (Chrome, Firefox, Edge, Safari)

### Passo a Passo

1. **Clonar o repositório:**
   ```bash
   git clone [https://github.com/erickserpe/pao-lab.git](https://github.com/erickserpe/pao-lab.git)
   cd pao-lab
   ```
