# Architecture - Documento de Arquitetura de Software: Pão Lab

## 1. Tecnologias Utilizadas

- **Estilização:** Bootstrap 5 (Framework CSS)
- **Lógica e Interatividade:** JavaScript Vanilla (ES6+)
- **Armazenamento de Estado/Preferências:** Web Storage (`localStorage`)
- **Servidor de Dados Simulado:** JSON Server (API Fake RESTful)
- **API Pública Externa:** Open-Meteo API (dados meteorológicos em tempo real por geolocalização)

## 2. Design Tokens

Os Design Tokens (paleta de cores, tipografia, espaçamento, radius, sombras, transições) estão documentados oficialmente em [`design-system.md`](./design-system.md), que é a fonte única de verdade para esses valores. Resumo dos tokens principais:

- **Cores:** `--pl-brown-900/700/500`, `--pl-wheat-100/200`, `--pl-cream`, `--pl-green-800/600`, `--pl-teal-800`, `--pl-amber-700`, `--pl-red-700`, `--pl-gray-700`, `--pl-border` (ver seção 2.2–2.3 do Design System).
- **Tipografia:** Fraunces (headings) + Inter (corpo/UI), escala fluida com `clamp()` (seção 3).
- **Espaçamento:** escala de 4/8/16/24/32/48/64px, seguindo o sistema de spacing do Bootstrap 5.
- **Radius:** `--pl-radius-sm/md/lg/pill`.
- **Sombras:** `--pl-shadow-sm/md/lg`.
- **Transições:** `--pl-transition-fast/base/slow` (120ms/180ms/300ms).

## 3. Entidades de Dados

### Entidade: `Experimento`

```json
{
  "id": 1,
  "nome": "Ciabatta Alta Hidratação",
  "categoria": "Ciabatta",
  "data": "2026-08-25",
  "farinha_g": 500,
  "hidratacao_pct": 78,
  "fermentacao_horas": 18,
  "clima": {
    "temperatura": 18.5,
    "umidade": 82
  },
  "avaliacao": {
    "geral": 5,
    "miolo": 5,
    "crosta": 4
  },
  "observacoes": "Massa muito hidratada, exigiu dobras a cada 30 min.",
  "favorito": false
}
```

### Entidade: `Farinha`

Cadastro auxiliar de tipos de farinha, reutilizável entre experimentos (segunda entidade da API, conforme recomendação do escopo mínimo da disciplina).

```json
{
  "id": 1,
  "nome": "Farinha de Trigo Tipo 1",
  "marca": "Anaconda",
  "proteina_pct": 12.5,
  "observacoes": "Boa força de glúten, indicada para pães de alta hidratação."
}
```

## 4. Contratos da API

### 4.1 JSON Server (API fake local — `db.json`)

Base URL local: `http://localhost:3000`

| Recurso     | Método   | Endpoint            | Descrição                                           |
| ----------- | -------- | ------------------- | --------------------------------------------------- |
| Experimento | `GET`    | `/experimentos`     | Lista todos os experimentos                         |
| Experimento | `GET`    | `/experimentos/:id` | Consulta um experimento específico                  |
| Experimento | `POST`   | `/experimentos`     | Cria um novo experimento                            |
| Experimento | `PUT`    | `/experimentos/:id` | Atualiza um experimento existente (edição completa) |
| Experimento | `DELETE` | `/experimentos/:id` | Remove um experimento                               |
| Farinha     | `GET`    | `/farinhas`         | Lista todos os tipos de farinha cadastrados         |
| Farinha     | `POST`   | `/farinhas`         | Cria um novo tipo de farinha                        |
| Farinha     | `PUT`    | `/farinhas/:id`     | Atualiza um tipo de farinha                         |
| Farinha     | `DELETE` | `/farinhas/:id`     | Remove um tipo de farinha                           |

Todas as requisições e respostas usam `Content-Type: application/json`. Erros de rede/servidor devem ser tratados com `try/catch` em torno das chamadas `fetch`, exibindo um alerta/toast de erro sem quebrar a interface (ver RN07 no PRD).

### 4.2 Open-Meteo API (dado climático externo)

Base URL: `https://api.open-meteo.com/v1/forecast`

Parâmetros principais utilizados:

| Parâmetro   | Exemplo                               | Descrição                               |
| ----------- | ------------------------------------- | --------------------------------------- |
| `latitude`  | `-25.41`                              | Latitude da cidade do usuário           |
| `longitude` | `-49.27`                              | Longitude da cidade do usuário          |
| `current`   | `temperature_2m,relative_humidity_2m` | Variáveis climáticas atuais solicitadas |

Exemplo de chamada:

```
GET https://api.open-meteo.com/v1/forecast?latitude=-25.41&longitude=-49.27&current=temperature_2m,relative_humidity_2m
```

Exemplo de resposta (simplificado):

```json
{
  "current": {
    "time": "2026-08-25T14:00",
    "temperature_2m": 18.5,
    "relative_humidity_2m": 82
  }
}
```

A latitude/longitude podem ser obtidas via `navigator.geolocation` (com fallback manual, caso o usuário negue a permissão). Falha na consulta (rede, timeout ou permissão negada) não deve impedir o salvamento do experimento — os campos `clima.temperatura` e `clima.umidade` ficam nulos e a interface exibe o estado de aviso descrito na seção 6.4 do Design System.
