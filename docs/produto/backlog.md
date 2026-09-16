# Backlog de Funcionalidades: Totem de Ponto de Ônibus Inteligente

Este documento consolida o Backlog Inicial do produto, estruturado com base nas necessidades identificadas nas personas do projeto.

As funcionalidades estão priorizadas seguindo a metodologia **MoSCoW**:

* **Must Have:** Essenciais para a versão inicial do produto (MVP).
* **Should Have:** Importantes e de alto valor, planejadas para a sequência imediata.
* **Could Have:** Diferenciais desejáveis que agregam conveniência ou inovação tecnológica.

Nesta primeira entrega, o backlog apresenta apenas a estrutura inicial do produto. As funcionalidades serão detalhadas como histórias de usuário, com critérios de aceitação e estimativas, na Entrega 2.

---

## Pessoas consideradas e impacto na priorização

As personas orientam a relação entre necessidades e funcionalidades do backlog:

- **Arthur:** agilidade, segurança e consulta sem expor o celular. Essas necessidades reforçam F01, F02, F06 e F08.
- **Kleber:** autonomia para pessoas com deficiência visual e retorno não visual. Essas necessidades reforçam F10 e F11.
- **Fátima:** simplicidade, textos grandes, bom contraste, ritmo adequado da informação e baixa exigência de familiaridade digital. Essas necessidades reforçam F01, F09, F10 e F11.

No MVP, a equipe prioriza o fluxo curto de consulta de linhas, sentidos e previsões em um ponto configurado. A legibilidade e a simplicidade devem orientar esse fluxo desde o início. O modo completo de alto contraste, a leitura em áudio e a interação por voz permanecem, respectivamente, em **Should Have** e **Could Have**, para serem implementados após a consulta básica se houver tempo e viabilidade técnica.

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
> *Projetado primariamente para as personas Kleber (deficiente visual) e Fátima (idosa), além de outros usuários com baixa visão ou pouca familiaridade digital.*

| ID | Funcionalidade | Prioridade |
| :--- | :--- | :--- |
| **F09** | Oferecer modo de alto contraste, textos grandes e legíveis. | **Should Have** |
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

O MVP será concentrado em um ponto previamente configurado, permitindo consultar as linhas disponíveis, seus sentidos e as previsões de chegada. O fluxo básico deverá ser curto, claro e legível para pessoas com diferentes níveis de familiaridade digital. O modo completo de alto contraste, a leitura em áudio e a interação por voz serão desenvolvidos após o funcionamento do fluxo principal, se houver tempo e viabilidade técnica. Reconhecimento de fala e planejamento de rotas são funcionalidades adicionais que poderão ser trabalhadas posteriormente.
