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

- **🧪 Protótipo no Stitch:** _[link a ser adicionado após a exploração inicial]_
- **🎨 Refinamento no Figma:** _[link a ser adicionado após o refinamento do UI Kit]_
- **📐 Design System:** [Documentação do Design System](docs/design-system.md)
- **📐 Arquitetura de Software:** [Documentação de Arquitetura](docs/architecture.md)

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

> _Screenshots das telas principais (Dashboard, Cadastro de Experimento, Laboratório/Histórico) serão adicionadas aqui conforme o desenvolvimento avançar._
