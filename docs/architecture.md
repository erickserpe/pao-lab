# Architecture - Documento de Arquitetura de Software: Pão Lab

## 1. Tecnologias Utilizadas

- **Estilização:** Bootstrap 5 (Framework CSS)
- **Lógica e Interatividade:** JavaScript Vanilla (ES6+)
- **Armazenamento de Estado/Preferências:** Web Storage (`localStorage`)
- **Servidor de Dados Simulado:** JSON Server (API Fake RESTful)
- **API Pública Externa:** Open-Meteo API (dados meteorológicos em tempo real por geolocalização)

## 2. Entidades de Dados

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
  "observacoes": "Massa muito hidratada, exigiu dobras a cada 30 min."
}
```
