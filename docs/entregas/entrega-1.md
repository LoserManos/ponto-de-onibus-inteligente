# Entrega 1 Definição do Problema API e Planejamento Inicial

## Identificação do projeto

**Nome provisório:** Ponto de Ônibus Inteligente  
**Tema de impacto social:** mobilidade urbana, inclusão digital e acessibilidade  
**Produto proposto:** sistema web executado em um totem instalado em um ponto de ônibus  
**Prazo da Entrega 1:** 15/09

Esta entrega define o problema, o público que será atendido, a fonte de dados abertos e o planejamento inicial do projeto.

## 1 Problema e oportunidade

No ponto de ônibus, o passageiro precisa decidir rapidamente se deve esperar, procurar outra linha ou caminhar até outra parada. Hoje, essa decisão costuma depender de um celular com internet, bateria, habilidade para usar aplicativos e disposição para expor o aparelho em um local público. A dificuldade é maior para pessoas idosas, turistas, usuários pouco familiarizados com a região e pessoas com deficiência visual.

O problema central do projeto é:

> Como oferecer, diretamente no ponto de ônibus, informação atualizada e acessível sobre as linhas e a previsão de chegada dos veículos sem exigir que o passageiro tenha um celular disponível?

A solução proposta é um totem interativo que apresenta as linhas atendidas pelo ponto, permite consultar uma linha e informa a previsão de chegada dos ônibus. O fluxo deverá ser curto e legível. Alto contraste, saída de áudio e outras melhorias de acessibilidade serão priorizados depois que a consulta básica estiver funcionando. O primeiro produto mínimo viável não dependerá de uma LLM, reconhecimento de fala ou planejamento de rotas: esses recursos ficam como possibilidades de evolução, enquanto o incremento inicial concentra-se em uma consulta confiável à API da SPTrans.

### Benefício social esperado

O projeto pretende reduzir a assimetria de informação no transporte público e ampliar a autonomia de passageiros que não podem ou não querem usar um smartphone durante a espera. Caso seja implementada, a funcionalidade de áudio poderá tornar a experiência mais acessível a pessoas com deficiência visual.

## 2 Escolha da API de dados abertos

### API selecionada

Será utilizada a **API do Olho Vivo da SPTrans**, que fornece dados do sistema de ônibus municipal de São Paulo em formato JSON. A documentação oficial descreve autenticação por token e consultas de linhas, pontos, itinerários e previsão de chegada.

Base prevista para o consumo:

```text
https://api.olhovivo.sptrans.com.br/v2.1
```

Endpoints relevantes para o MVP:

| Necessidade do produto | Operação da API | Uso na solução |
| --- | --- | --- |
| Autenticar a aplicação | `POST /Login/Autenticar?token={token}` | Inicializar o cliente da API no servidor |
| Buscar uma linha | `GET /Linha/Buscar?termosBusca={termosBusca}` | Encontrar a linha por número ou nome |
| Buscar um ponto | `GET /Parada/Buscar?termosBusca={termosBusca}` | Localizar um ponto quando necessário |
| Listar pontos de uma linha | `GET /Parada/BuscarParadasPorLinha?codigoLinha={codigoLinha}` | Exibir o trajeto e os pontos atendidos |
| Consultar chegada | `GET /Previsao?codigoParada={codigoParada}&codigoLinha={codigoLinha}` | Mostrar a previsão atualizada do ônibus |

O token será mantido somente no ambiente do servidor e em variáveis de ambiente. Ele não será incluído no código-fonte, no histórico do Git ou na interface do totem.

### Justificativa

1. A API é uma fonte oficial de dados do transporte municipal de São Paulo.
2. A previsão de chegada permite que a solução entregue informação operacional, e não apenas um mapa estático.
3. As operações de linhas, pontos e previsões cobrem o núcleo do problema sem exigir, no MVP, outra fonte de dados.
4. A API atende diretamente ao requisito da disciplina de integrar dados abertos à solução.

Referência: [Documentação oficial da API do Olho Vivo](https://www.sptrans.com.br/desenvolvedores/api-do-olho-vivo-guia-de-referencia/documentacao-api/).

### Limites conhecidos da API

A API informa dados do sistema de ônibus, mas não resolve sozinha todos os problemas de uma viagem porta a porta. O MVP não prometerá um planejador completo combinando ônibus, metrô e caminhada. A previsão também pode estar indisponível, atrasada ou sem veículos próximos; nesses casos, a interface deverá comunicar a indisponibilidade claramente e oferecer nova tentativa.

## 3 Público-alvo

### Público primário

Passageiros que aguardam ônibus em pontos movimentados e precisam de uma resposta rápida sobre qual linha utilizar ou quanto tempo falta para o próximo veículo.

### Públicos prioritários para acessibilidade

- pessoas com deficiência visual que precisam de retorno sonoro e identificação clara da linha;
- pessoas idosas ou com baixa familiaridade com aplicativos de mobilidade;
- turistas e passageiros em regiões desconhecidas;
- pessoas sem smartphone, sem dados móveis, com pouca bateria ou que preferem não expor o aparelho no ponto.

### Necessidades comuns

- descobrir as linhas atendidas pelo ponto;
- identificar o destino e o sentido da linha;
- consultar a previsão de chegada;
- obter informação legível e, quando necessário, audível;
- concluir a consulta em poucos passos, sem criar conta e sem entregar dados pessoais.

## 4 Mapas de empatia

Foram definidos dois perfis complementares para orientar as decisões de produto:

- [Mapa de empatia do passageiro Arthur](../produto/mapa-de-empatia/mapa-transeunte.md)
- [Mapa de empatia do passageiro com deficiência visual Kleber](../produto/mapa-de-empatia/mapa-transeunte-deficiente-visual.md)

Os perfis são personas de trabalho utilizadas para representar necessidades relevantes dos públicos considerados pelo grupo.

## 5 Backlog inicial de funcionalidades

O [backlog inicial](../produto/backlog.md) foi organizado em épicos e priorizado com a metodologia MoSCoW. Nesta entrega ele apresenta as funcionalidades em nível geral; histórias de usuário, critérios de aceitação e estimativas serão detalhados na Entrega 2.

O primeiro incremento prioriza a consulta de linhas, sentidos e previsões de chegada em um ponto previamente configurado. Recursos adicionais de acessibilidade são desejáveis, mas não condicionam a conclusão do fluxo principal. Reconhecimento de fala e planejamento de rotas poderão ser considerados se houver tempo e viabilidade técnica.

## 6 Apoio ferramental e processo Scrum

### Ferramentas

- **GitHub:** repositório, branches, pull requests e histórico do código.
- **GitHub Issues:** uma issue por funcionalidade, defeito ou tarefa de documentação.
- **GitHub Milestones:** agrupamento das issues de cada entrega da disciplina.
- **GitHub Projects:** quadro Kanban que será criado para acompanhar visualmente as tarefas.
- **Markdown:** documentação versionada junto ao projeto.

O uso dessas ferramentas está detalhado no documento de [ferramentas para gestão](../gestao/ferramentas-para-gestao.md).

Cada tarefa deve ser registrada em uma issue e associada à milestone correspondente. Quando houver alteração no repositório, a issue também deve apontar para o pull request relacionado. O quadro do GitHub Projects será organizado nas colunas `Backlog`, `Em andamento`, `Em revisão` e `Concluído`.

### Organização Scrum inicial

- **Backlog:** as funcionalidades são mantidas e priorizadas no GitHub.
- **Organização do trabalho:** no início de cada ciclo, o grupo seleciona os itens que pretende concluir.
- **Acompanhamento:** as atualizações são registradas de forma assíncrona nas issues e pull requests.
- **Revisão:** antes de cada entrega, o grupo verifica o que foi concluído e ajusta o backlog.

## Checklist da Entrega 1

- [x] Descrição do problema e justificativa da API.
- [x] Identificação do público-alvo.
- [x] Mapas de empatia.
- [x] Estrutura inicial do backlog.
- [x] Ferramenta de apoio à gestão do projeto.
