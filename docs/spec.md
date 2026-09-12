# Spec - Especificação Técnica de Versões: Pão Lab

> Documento técnico de referência com as versões exatas das tecnologias
> escolhidas, os critérios usados na decisão e os riscos avaliados. Objetivo:
> garantir compatibilidade futura e servir de contexto preciso para
> ferramentas de IA (Cursor, Copilot, Claude Code) gerarem código nas versões
> corretas — evitar sintaxe de versões antigas (ex: Bootstrap 4) ou features
> futuras ainda não estáveis.

---

## 1. Framework CSS

### Bootstrap `5.3.8` (Active LTS)

- **Release:** 25 de agosto de 2025 — última patch da linha 5.3 antes da 5.4.
- **CDN (CSS):** `https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/css/bootstrap.min.css`
- **CDN (JS bundle, inclui Popper):** `https://cdn.jsdelivr.net/npm/bootstrap@5.3.8/dist/js/bootstrap.bundle.min.js`
- **Licença:** MIT.
- **Repositório:** ativo, Active LTS — a única versão da linha 5.x recebendo updates.

**Critérios avaliados (comparado a Materialize, BeerCSS e Bulma):**

| Critério            | Resultado                                                                                                                     |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Responsividade      | Grid de 12 colunas + breakpoints (`sm/md/lg/xl/xxl`) cobrem exatamente as versões mobile/desktop do protótipo                 |
| Componentes prontos | Navbar, Card, Modal e Offcanvas cobrem os 3 componentes marcados no protótipo (Navbar, Cards, Modal de exclusão)              |
| Ecossistema JS      | Não depende de jQuery desde a v5.0 (JS próprio + Popper via bundle)                                                           |
| Saúde do projeto    | Único Active LTS entre os avaliados; Bootstrap 6 ainda em alpha (`6.0.0-alpha1`), sem data de lançamento — **não usar ainda** |
| Licença             | MIT — compatível com projeto acadêmico open-source                                                                            |

**Risco monitorado:** Bootstrap 6 está em desenvolvimento ativo (branch `v6-dev`) e vai introduzir breaking changes relevantes (prefixo de classes responsivas no estilo `md:col-6` em vez de `col-md-6`, JS só em ESM). Não impacta este projeto agora, mas justifica não fixar em uma versão "genérica" — a 5.3.8 é a versão avaliada e testada.

---

## 2. Bibliotecas JavaScript

### jQuery `3.7.1` (não 4.0.0)

- **CDN:** `https://code.jquery.com/jquery-3.7.1.min.js`
- **Licença:** MIT.

**Por que não a versão mais nova (jQuery `4.0.0`, lançada em janeiro de 2026):**
o jQuery Mask Plugin (ver abaixo) nunca foi testado ou documentado como
compatível além do jQuery 1.7+ — o repositório oficial não menciona suporte à
4.0, que remove APIs internas antigas. Como o Mask Plugin está com o
desenvolvimento parado (sem commits de feature há anos), o risco de quebra
silenciosa é maior que o benefício de usar a versão mais nova. A 3.7.1 é a
release anterior à 4.0 e continua oficialmente suportada (jQuery só dá
suporte às duas últimas versões simultaneamente).

### jQuery Mask Plugin `1.14.16`

- **CDN:** `https://cdnjs.cloudflare.com/ajax/libs/jquery.mask/1.14.16/jquery.mask.min.js`
- **Compatibilidade declarada pelo autor:** jQuery 1.7+ (testado até essa faixa; sem garantia documentada acima disso).
- **Risco monitorado:** repositório com baixa atividade de manutenção. Caso apareçam bugs de máscara em campos numéricos (ex: hidratação %, gramas de farinha), a alternativa de fallback é reescrever a validação com `input` + Regex puro em JS Vanilla (sem dependência externa), já previsto como técnica alternativa no RA2/ID12 do checklist.

---

## 3. Backend Simulado

### JSON Server `0.17.4` (linha estável — NÃO a `1.0.0-beta`)

- **Instalação:** `npm install json-server@0.17.4`
- **Licença:** MIT.

**Por que a versão 0 e não a mais recente (`1.0.0-beta.15`, tag `latest` no
npm atualmente):** a v1 ainda está em beta com mudanças que quebram
compatibilidade com o modelo de dados já documentado em `architecture.md`:
IDs passam a ser sempre string (nosso modelo usa `"id": 1` numérico),
paginação muda de `_limit` para `_page`/`_per_page`, e relacionamentos mudam
de `_expand` para `_embed`. Para um projeto acadêmico com prazo fixo, a
estabilidade da v0.17.4 (mais madura, mesma sintaxe usada em toda a
documentação já escrita) é a escolha mais segura. O `package.json` do
projeto já fixa essa versão via `^0.17.4`.

---

## 4. API Pública

### Open-Meteo API — Forecast Endpoint `v1`

- **Base URL:** `https://api.open-meteo.com/v1/forecast`
- **Autenticação:** nenhuma (sem API key, sem cadastro).
- **Licença de uso:** gratuita para uso não-comercial, CC BY 4.0 nos dados.
- **Parâmetros usados:** `latitude`, `longitude`, `current=temperature_2m,relative_humidity_2m` (contrato completo documentado em `architecture.md`, seção 4.2).

**Critérios avaliados:** não exigir autenticação foi decisivo — elimina a
necessidade de gerenciar chave de API no front-end estático (GitHub Pages não
tem onde esconder secrets). Documentação oficial extensa e endpoint estável,
já em produção há anos.

---

## 5. Resumo de Versões (referência rápida)

| Tecnologia          | Versão        | Tipo de pin                                   |
| ------------------- | ------------- | --------------------------------------------- |
| Bootstrap           | 5.3.8         | Exata (CDN)                                   |
| Bootstrap Bundle JS | 5.3.8         | Exata (CDN)                                   |
| jQuery              | 3.7.1         | Exata (CDN)                                   |
| jQuery Mask Plugin  | 1.14.16       | Exata (CDN)                                   |
| JSON Server         | 0.17.4        | Caret `^0.17.4` (package.json)                |
| Open-Meteo API      | v1 (forecast) | Endpoint estável, sem versionamento semântico |
| Node.js             | 18+           | Mínima (ver README)                           |
