# Entrega 1 Definição do Problema API e Planejamento Inicial

## Identificação do projeto

**Nome provisório:** Ponto de Ônibus Inteligente  
**Tema de impacto social:** mobilidade urbana, inclusão digital e acessibilidade  
**Produto proposto:** sistema web executado em um totem instalado em um ponto de ônibus  
**Prazo da Entrega 1:** 15/09

Esta entrega define o problema, o público que será atendido, a fonte de dados abertos, as hipóteses iniciais e o plano de trabalho do projeto. Os resultados de entrevistas e observações ainda devem ser coletados; por isso, as afirmações marcadas como hipóteses serão validadas no diagnóstico.

## 1 Problema e oportunidade

No ponto de ônibus, o passageiro precisa decidir rapidamente se deve esperar, procurar outra linha ou caminhar até outra parada. Hoje, essa decisão costuma depender de um celular com internet, bateria, habilidade para usar aplicativos e disposição para expor o aparelho em um local público. A dificuldade é maior para pessoas idosas, turistas, usuários pouco familiarizados com a região e pessoas com deficiência visual.

O problema central do projeto é:

> Como oferecer, diretamente no ponto de ônibus, informação atualizada e acessível sobre as linhas e a previsão de chegada dos veículos sem exigir que o passageiro tenha um celular disponível?

A solução proposta é um totem interativo que apresenta as linhas atendidas pelo ponto, permite consultar uma linha e informa a previsão de chegada dos ônibus. A interface deverá ter texto grande, contraste adequado, fluxo curto e uma alternativa de saída de áudio. O primeiro produto mínimo viável não dependerá de uma LLM nem de reconhecimento de fala: esses recursos ficam como possibilidades de evolução, enquanto a entrega inicial concentra-se em uma consulta confiável à API da SPTrans.

### Benefício social esperado

O projeto pretende reduzir a assimetria de informação no transporte público e ampliar a autonomia de passageiros que não podem ou não querem usar um smartphone durante a espera. A funcionalidade de áudio também cria uma base para uma experiência mais acessível a pessoas com deficiência visual, desde que seja validada com usuários e testada em condições reais de ruído.

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

- [Mapa de empatia do passageiro Arthur](produto/mapa-de-empatia/mapa-transeunte.md)
- [Mapa de empatia do passageiro com deficiência visual Kleber](produto/mapa-de-empatia/mapa-transeunte-deficiente-visual.md)

Os perfis são personas de trabalho, não resultados de pesquisa. Eles servem para explicitar hipóteses que serão verificadas no diagnóstico.

## 5 Backlog inicial de funcionalidades

O [backlog inicial](produto/backlog.md) foi organizado em épicos e priorizado com a metodologia MoSCoW. Nesta entrega ele apresenta as funcionalidades em nível geral; histórias de usuário, critérios de aceitação e estimativas serão detalhados na Entrega 2.

O primeiro incremento prioriza a consulta de linhas, sentidos e previsões de chegada, além dos recursos básicos de acessibilidade. Reconhecimento de fala e cálculo de rotas multimodais foram mantidos como possibilidades futuras, sujeitos ao diagnóstico e à viabilidade técnica.

## 6 Apoio ferramental e processo Scrum

### Ferramentas

- **GitHub:** repositório, branches, pull requests e histórico do código.
- **GitHub Issues:** uma issue por funcionalidade, defeito ou tarefa de documentação.
- **GitHub Projects:** quadro Kanban associado ao repositório.
- **Markdown:** documentação versionada junto ao projeto.

O uso dessas ferramentas está detalhado no documento de [ferramentas para gestão](gestao/ferramentas-para-gestao.md).

O quadro deverá usar as colunas `Backlog`, `Pronto para Sprint`, `Em andamento`, `Em revisão` e `Concluído`. Cada item deve apontar para uma issue e para o pull request correspondente quando houver código.

### Organização Scrum inicial

- **Sprint:** ciclos curtos de uma semana, com planejamento no início e revisão retrospectiva ao final.
- **Planejamento da Sprint:** selecionar itens de maior prioridade que tenham critério de aceitação claro.
- **Revisão:** demonstrar o incremento funcionando e registrar decisões ou impedimentos.
- **Retrospectiva:** registrar uma melhoria de processo para a próxima Sprint.
- **Definition of Done:** item implementado, revisado por outro integrante, testado no fluxo relevante, documentado quando necessário e integrado à branch principal.

Os nomes dos integrantes e a distribuição de papéis devem ser preenchidos pelo grupo no GitHub, pois não constam no repositório atual.

## 7 Avaliação de diagnóstico

Esta seção define o diagnóstico inicial a ser aplicado antes de fechar a especificação da Entrega 2. Ela separa o que já é decisão do projeto das hipóteses que ainda precisam de evidência.

### Hipóteses a validar

| Código | Hipótese | Evidência planejada |
| --- | --- | --- |
| H1 | Passageiros têm dificuldade para obter uma previsão confiável sem abrir um aplicativo no celular. | Entrevistas curtas e observação em pontos de ônibus. |
| H2 | O risco percebido de furto ou a falta de dados móveis reduz o uso do celular durante a espera. | Pergunta direta sobre contexto de uso e alternativas adotadas. |
| H3 | Um fluxo com poucas opções é mais útil no ponto do que uma tela com muitas informações. | Teste de tarefa com protótipo de baixa fidelidade. |
| H4 | A saída de áudio é necessária para que o totem seja útil a pessoas com deficiência visual. | Entrevista com usuários ou entidade especializada e teste com áudio ambiente. |
| H5 | A previsão da API é compreensível quando apresentada com horário de atualização e destino da linha. | Teste de compreensão com cenários de consulta. |

### Roteiro de coleta

1. Entrevistar pelo menos cinco passageiros com perfis variados, sem coletar nome ou contato.
2. Perguntar como a pessoa escolhe uma linha, como verifica atrasos e o que faz quando não tem acesso ao celular.
3. Observar, sem registrar imagens identificáveis, as dúvidas recorrentes e o tempo necessário para obter informação no ponto.
4. Realizar um teste de tarefa com protótipo: “encontre a próxima chegada da linha que vai para o seu destino”.
5. Registrar achados, frequência, evidência e decisão tomada no backlog.

### Critérios de decisão

- manter no MVP as necessidades relatadas por mais de um perfil e diretamente relacionadas ao problema central;
- revisar ou retirar funcionalidades que não sejam compreendidas em um teste de tarefa;
- tratar acessibilidade como requisito do fluxo principal, não como uma etapa posterior;
- não registrar áudio, imagem ou informação pessoal para fins de diagnóstico sem consentimento específico.

## 8 Riscos e próximos passos

| Risco | Impacto | Mitigação inicial |
| --- | --- | --- |
| Token ou serviço da API indisponível | Alto | Criar uma camada de acesso isolada, mensagem de erro e dados de teste apenas para desenvolvimento. |
| Previsão sem veículos ou com atraso | Alto | Mostrar horário de atualização, estado vazio e ação de atualizar. |
| Ruído no ponto prejudicar o áudio | Médio | Testar volume, repetição, fone e alternativa visual de alto contraste. |
| Escopo crescer para um planejador completo | Alto | Manter o MVP limitado a ponto, linha, sentido e previsão. |
| Inclusão acidental de token no Git | Alto | Usar variáveis de ambiente, revisão de pull request e verificação antes do push. |

Próximos passos para a Entrega 2:

1. realizar o diagnóstico e registrar resultados reais;
2. transformar os itens priorizados em user stories completas;
3. produzir protótipo de média ou alta fidelidade;
4. definir tecnologias e arquitetura inicial;
5. obter um token de desenvolvimento da SPTrans sem publicá-lo no repositório.

## Checklist da Entrega 1

- [x] Descrição do problema e justificativa da API.
- [x] Identificação do público-alvo.
- [x] Mapas de empatia.
- [x] Estrutura inicial do backlog.
- [x] Ferramenta de gestão do projeto e processo Scrum.
- [x] Plano de avaliação de diagnóstico.
- [ ] Preencher integrantes e papéis da equipe.
- [ ] Executar entrevistas e substituir hipóteses por achados observados.
