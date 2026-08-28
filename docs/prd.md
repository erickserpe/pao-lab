# PRD - Documento de Requisitos do Produto: Pão Lab

## 1. Visão Geral do Produto

O **Pão Lab** é uma aplicação web responsiva para registro, acompanhamento e análise de experimentos de panificação artesanal. A ferramenta permite relacionar variáveis de produção (hidratação, tempos de fermentação, tipos de farinha) e condições climáticas do ambiente a resultados finais da massa.

## 2. Público-Alvo

Padeiros caseiros, entusiastas de panificação artesanal (_sourdough_) e estudantes que buscam um histórico organizado de testes para aprimorar suas técnicas.

## 3. User Stories (Histórias de Usuário)

- **US01:** Como usuário, quero cadastrar um novo experimento informando parâmetros da massa (farinha, hidratação %, levain, fermentação) para registrar minhas tentativas.
- **US02:** Como usuário, quero consultar a temperatura e umidade atuais da minha cidade automaticamente via API ao cadastrar/editar um teste para entender o impacto do clima no fermento.
- **US03:** Como usuário, quero visualizar meus experimentos cadastrados em formato de cards no painel com notas de aparência, miolo e crosta.
- **US04:** Como usuário, quero filtrar e buscar o histórico de testes por categoria de pão, ordenação e nota geral.
- **US05:** Como usuário, quero **editar os dados de um experimento já cadastrado** para corrigir informações ou atualizar observações após a degustação do pão.
- **US06:** Como usuário, quero **excluir um experimento do meu histórico** para remover testes descartados ou registros duplicados.
- **US07:** Como usuário, quero **marcar experimentos como favoritos** para ter acesso rápido às minhas melhores receitas na interface.
- **US08:** Como usuário, quero **cadastrar e gerenciar tipos de farinha** (marca, tipo, % de proteína) para reutilizá-los ao registrar novos experimentos, sem precisar redigitar essas informações.

## 4. Regras de Negócio

- **RN01:** O formulário deve exigir obrigatoriamente Nome do Pão, Categoria, Quantidade de Farinha (g) e Hidratação (%).
- **RN02:** As notas de avaliação (Geral, Aparência, Miolo e Crosta) devem ser numéricas de 1 a 5.
- **RN03:** O valor de hidratação (%) deve ser validado entre 50% e 100%.
- **RN04:** Os dados dos experimentos devem ser salvos, atualizados e deletados no backend simulado (JSON Server via requisições `POST`, `PUT` e `DELETE`), enquanto preferências de interface (favoritos, tema) persistem no `localStorage`.
- **RN05:** A exclusão de um experimento deve obrigatoriamente exibir um modal de confirmação para evitar perdas acidentais de dados.
- **RN06:** A edição de um experimento deve preencher automaticamente o formulário com os dados existentes mantendo a integridade do ID original do registro no JSON Server.
- **RN07:** O insucesso da consulta à Open-Meteo API (falha de rede ou timeout) não deve impedir o salvamento ou a edição do experimento.
- **RN08:** O formulário de experimento deve permitir selecionar a farinha a partir dos tipos previamente cadastrados na entidade `Farinha` (via `<select>`), evitando duplicidade de digitação.
