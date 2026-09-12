# Proposta de Projeto: Totem Interativo de Transporte Urbano 

## 1. Problema 
Muitos passageiros enfrentam dificuldades para descobrir qual linha de ônibus pegar ou quanto tempo falta para o veículo chegar, especialmente quando não possuem familiaridade com a região ou estão sem acesso a um celular com internet no momento (ou não sabem utilizar um). Este documento detalha o problema abordado pelo projeto. 

## 2. Público-Alvo e Benefícios
* **Público-Alvo:** Usuários do transporte público em vias movimentadas, idosos com dificuldade no uso de aplicativos complexos, transeuntes com deficiência visual e turistas ou cidadãos desorientados que não sabem se informar pelo celular. 
* **Por que a solução alivia a dificuldade:** Um totem interativo no ponto de ônibus elimina a necessidade do uso de celulares para se informar sobre o trajeto o qual se tem interesse, beneficiando aqueles que possuem dificuldades no uso desses aparelhos. Além disso, pretendemos também adicionar uma função de comunicação por voz que, caso implementada, beneficiaria aqueles com deficiência visual que utilizam o transporte público urbano em questão, democratizando assim o acesso à informação de mobilidade.

## 3. APIs Utilizadas e Justificativa
* **API de Transporte:** API do Olho Vivo (SPTrans).
* **Justificativa:** É a fonte de dados oficial e gratuita da cidade, fornecendo não apenas as rotas e pontos de parada, mas as posições de GPS em tempo real da frota (endpoint de Previsão). Isso garante que o usuário receba a informação de quantos minutos faltam para o seu ônibus chegar.
* **APIs Complementares:** Speech-to-Text (para captar o áudio do usuário no ponto) e uma LLM (como OpenAI ou Gemini) para interpretar intenções de rotas com base na fala transcrita. Essa API e essa feature é apenas uma pretenção do grupo no momento, sem garantias de implementação.

## 4. Organização da Equipe e Ferramentas
* **Gestão de Tarefas e Versionamento:** GitHub (Issues e Projects) para organização assíncrona.
* **Comunicação:** Reuniões presenciais e onlines entre os integrantes do grupo