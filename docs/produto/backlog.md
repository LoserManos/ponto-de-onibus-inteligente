# Backlog de Funcionalidades: Totem de Ponto de Ônibus Inteligente

Este documento consolida o Backlog Inicial do produto, estruturado com base nas necessidades identificadas nas personas do projeto.

As funcionalidades estão priorizadas seguindo a metodologia **MoSCoW**:

* **Must Have:** Essenciais para a versão inicial do produto (MVP).
* **Should Have:** Importantes e de alto valor, planejadas para a sequência imediata.
* **Could Have:** Diferenciais desejáveis que agregam conveniência ou inovação tecnológica.

Nesta primeira entrega, o backlog apresenta apenas a estrutura inicial do produto. As funcionalidades serão detalhadas como histórias de usuário, com critérios de aceitação e estimativas, na Entrega 2.

---

## 📌 Visão Geral dos Épicos

| ID | Épico | Descrição | Prioridade Geral |
| :--- | :--- | :--- | :--- |
| **EP01** | **Interface & Experiência do Totem (UI/UX)** | Design visual, ergonomia para telas touchscreen e operação em modo quiosque. | **Must Have** |
| **EP02** | **Previsão e Monitoramento em Tempo Real** | Integração com a API Olho Vivo (SPTrans) para chegadas, linhas e posições. | **Must Have** |
| **EP03** | **Acessibilidade Universal & Interação por Voz** | Recursos auditivos e de alto contraste voltados a pessoas com deficiência visual e idosos. | **Should Have** |
| **EP04** | **Planejamento e Auxílio de Rotas** | Orientações de como chegar a pontos de referência e destinos populares. | **Could Have** |

---

## 🗂️ Detalhamento inicial das funcionalidades

### Épico 01: Interface & Experiência do Totem (UI/UX)
> *Garante que o software funcione de maneira ergonômica, intuitiva e segura em uma tela pública de uso coletivo.*

| ID | Funcionalidade | Prioridade |
| :--- | :--- | :--- |
| **F01** | Exibir as linhas disponíveis no ponto e o sentido de cada uma. | **Must Have** |
| **F02** | Permitir que o passageiro selecione ou pesquise uma linha. | **Must Have** |
| **F03** | Exibir destino e pontos principais da linha selecionada. | **Must Have** |
| **F04** | Retornar à tela inicial após um período sem interação. | **Should Have** |

---

### Épico 02: Previsão e Monitoramento em Tempo Real
> *Consumo e apresentação dos dados operacionais da SPTrans.*

| ID | Funcionalidade | Prioridade |
| :--- | :--- | :--- |
| **F05** | Consultar linhas e paradas pela API Olho Vivo da SPTrans. | **Must Have** |
| **F06** | Exibir a previsão de chegada dos próximos ônibus. | **Must Have** |
| **F07** | Informar o horário da última atualização da previsão. | **Must Have** |
| **F08** | Informar falhas ou indisponibilidade dos dados e permitir nova tentativa. | **Must Have** |

---

### Épico 03: Acessibilidade Universal & Interação por Voz
> *Projetado primariamente para a persona Kleber (deficiente visual) e usuários da terceira idade.*

| ID | Funcionalidade | Prioridade |
| :--- | :--- | :--- |
| **F09** | Oferecer modo de alto contraste e textos legíveis. | **Should Have** |
| **F10** | Permitir a navegação sem depender exclusivamente de cores. | **Should Have** |
| **F11** | Disponibilizar leitura em áudio das opções e previsões. | **Should Have** |
| **F12** | Permitir interação por comandos de voz. | **Could Have** |

---

### Épico 04: Planejamento e Auxílio de Rotas
> *Ajuda usuários sem celular a se localizarem na malha urbana.*

| ID | Funcionalidade | Prioridade |
| :--- | :--- | :--- |
| **F13** | Apresentar pontos de referência atendidos por uma linha. | **Could Have** |
| **F14** | Sugerir linhas para chegar a um ponto de referência. | **Could Have** |
| **F15** | Calcular rotas multimodais combinando ônibus, metrô e caminhada. | **Could Have** |

---

## Limites do primeiro incremento

O MVP será concentrado em um ponto previamente configurado, permitindo consultar as linhas disponíveis, seus sentidos e as previsões de chegada. Recursos adicionais de acessibilidade serão desenvolvidos se houver tempo após o funcionamento do fluxo principal. Reconhecimento de fala e planejamento de rotas são features adicionais que poderemos trabalhar, caso o tempo permita.
