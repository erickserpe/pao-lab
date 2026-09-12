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

- **🧪 Protótipo navegável no Stitch (8 telas, mobile + desktop):** _[link do Instant Prototype a ser adicionado aqui após a geração]_
- **🎨 Refinamento no Figma:** _[link a ser adicionado após o refinamento do UI Kit]_
- **📐 Design System:** [Documentação do Design System](docs/design-system.md)
- **📐 Arquitetura de Software:** [Documentação de Arquitetura](docs/architecture.md)

---

## 🛠️ Framework CSS & Dependências

- **Framework CSS:** [Bootstrap 5.3.8](https://getbootstrap.com/)
- **Bibliotecas & Dependências JavaScript:**
  - [Bootstrap 5 Bundle JS](https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js) (Navbar, Cards, Modais, Tooltips)
  - [jQuery 3.7.1](https://jquery.com/) (Manipulação do DOM e animações)
  - [jQuery Mask Plugin 1.14.16](https://cdnjs.cloudflare.com/ajax/libs/jquery.mask/1.14.16/jquery.mask.min.js) (Máscaras de inputs no formulário)
  - [Open-Meteo API](https://open-meteo.com/) (Fetch API meteorológica pública)
  - [JSON Server 0.17.4](https://github.com/typicode/json-server) (Backend RESTful fake local)

📄 Versões exatas, critérios de avaliação e justificativa técnica completa em **[`docs/spec.md`](docs/spec.md)**.

### Por que Bootstrap 5?

Entre os frameworks avaliados (Bootstrap, Materialize, BeerCSS, Bulma), o Bootstrap 5.3.8 venceu em 3 dos critérios analisados: (1) **responsividade** — grid de 12 colunas com breakpoints que já cobrem exatamente as duas versões do protótipo (mobile/desktop); (2) **componentes prontos** — Cards, Navbar, Modal e Offcanvas cobrem literalmente as 3 substituições planejadas no protótipo (Navbar, Cards de experimento, Modal de exclusão); (3) **saúde do projeto** — é o único framework Active LTS entre os avaliados, com release estável em agosto de 2025 e ecossistema/documentação muito acima dos concorrentes. Desde a v5.0 não depende mais de jQuery para os componentes interativos (Popper.js via bundle), o que simplifica o carregamento de scripts.

### Por que Open-Meteo?

Não exige API key (sem cadastro/autenticação, o que elimina um ponto de fricção pro escopo do projeto), tem endpoint simples via `fetch` puro, documentação clara, e os dados de temperatura/umidade atual se conectam diretamente ao valor central do app: relacionar clima real à fermentação (US02 do PRD).

---

## 🌐 Link para o Site em Produção

- **URL do Deploy (GitHub Pages):** [https://erickserpe.github.io/pao-lab/](https://erickserpe.github.io/pao-lab/)

---

## ✅ Checklist de Funcionalidades

O acompanhamento detalhado do status dos Indicadores de Desempenho (IDs) e Resultados de Aprendizagem (RAs) da matriz da UTFPR está documentado no arquivo exclusivo:

📄 **[Acessar Checklist de Funcionalidades e IDs (RAs)](docs/checklist.md)**

---

## ⚙️ Instruções de Execução

### Pré-requisitos

- Node.js (v18 ou superior)
- Git
- Navegador Web (Chrome, Firefox, Edge, Safari)

### Passo a Passo

1. **Clonar o repositório:**

   ```bash
   git clone https://github.com/erickserpe/pao-lab.git
   cd pao-lab
   ```

2. **Instalar as dependências:**

   ```bash
   npm install
   ```

3. **Subir a API fake (JSON Server):**

   ```bash
   npm run server
   ```

   O servidor ficará disponível em `http://localhost:3000`.

4. **Abrir a aplicação:**
   Abra o arquivo `index.html` com a extensão **Live Server** (VS Code) ou qualquer servidor estático local, mantendo o JSON Server rodando em paralelo.

---

## 🖼️ Telas da Aplicação

O protótipo cobre 8 telas (fluxo completo + estados de negócio). Screenshots
serão adicionados aqui conforme o desenvolvimento em HTML/CSS avançar:

1. **Painel** — visão geral com clima atual, métricas e experimentos recentes
2. **Novo Experimento** — formulário de cadastro/edição
3. **Laboratório** — histórico completo com busca, filtro e ordenação
4. **Detalhes do Experimento** — ficha de leitura do registro
5. **Confirmar Exclusão** — modal de confirmação
6. **Aviso: Clima Indisponível** — estado de erro não-bloqueante da API pública
7. **Sucesso ao Salvar** — feedback de confirmação
8. **Laboratório Vazio** — estado vazio
