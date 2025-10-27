## Documentação - Sprint 4

---
## 🏅 Desafio

O desafio desta sprint é evoluir nossa Inteligência Artificial em duas frentes críticas: criar um ciclo de aprendizado contínuo e implementar o autoatendimento inteligente. O objetivo é fazer com que a IA não apenas execute tarefas, mas que aprenda com o trabalho dos agentes para se tornar mais precisa com o tempo. Simultaneamente, vamos expor essa inteligência diretamente ao usuário final, oferecendo soluções instantâneas baseadas em uma base de conhecimento, com o potencial de resolver problemas comuns antes mesmo que um chamado seja formalmente criado.

---
## 📋 User Stories

| Prioridade | User Story                                                                                                                                       | Sprint | Requisito do Cliente | Status   |
| :--------: | -----------------------------------------------------------------------------------------------------------------------------------------------  | :----: | :------------------: | :------: |
|    Média   |	Como administrador, quero que a IA aprenda com dados de chamados para melhorar suas sugestões, para que sua precisão aumente com o tempo.       |   4    | R09                  |    ✅    |
|    Média   |	Como usuário, quero que a IA sugira uma resposta com base em uma base de conhecimento, para que eu receba uma solução rápida para meu problema. |   4    | R010                 |    ✅    |

---

## 🏅 DoR - Definition of Ready

|  Critério                    | Descrição                                                                                                                                                                                                                                                                                                                                                                                                   |
| :--------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|Formato da História           |	As histórias focam em novos perfis (Administrador) e em novas interações (Usuário + IA).                                                                                                                                                                                                                                                                                                                   |
|Critérios de Aceitação Claros |	Os critérios são específicos sobre o comportamento e os limites da IA. Exemplo (para R10): "1. Ao digitar o título do problema, uma sugestão de solução deve aparecer antes do botão 'Enviar'. 2. A resposta deve ser claramente identificada como 'Sugestão da IA'. 3. Se a IA não encontrar uma resposta, ela deve informar 'Não encontrei uma solução, por favor, continue com a abertura do chamado'." |
|Independência                 |	As dependências de dados e arquitetura estão claras. Exemplo: A história R09 (aprendizado) depende dos dados corrigidos pelos agentes na Sprint 3. A história R10 (autoatendimento) depende da criação de uma base de conhecimento inicial (ex: 15 artigos de ajuda).                                                                                                                                      |
|Valor de Negócio              |	O retorno sobre o investimento (ROI) da funcionalidade está claro. Exemplo: A equipe entende que a R10 tem o potencial de reduzir em 20% o volume de chamados repetitivos, liberando os agentes para casos mais complexos.                                                                                                                                                                                 |
|Estimativa Acordada           |	As histórias foram estimadas considerando a pesquisa e implementação de novas arquiteturas de IA (Fine-tuning, RAG - Retrieval-Augmented Generation).                                                                                                                                                                                                                                                      |
|Dependências Mapeadas         |	As ferramentas e dados necessários estão prontos. Exemplo (para R10): "A base de conhecimento inicial foi escrita e o banco de dados de vetores (ex: Pinecone, PGvector) foi escolhido e configurado." Exemplo (para R09): "Temos um conjunto de pelo menos 100 chamados corrigidos para usar no primeiro ciclo de fine-tuning."                                                                           |
|Protótipos/Mockups Anexados   |	A interface de interação com a IA está desenhada e validada. Exemplo (para R10): "O Figma detalha como a sugestão de resposta será exibida na tela de criação de chamado e como o usuário pode dar feedback se a sugestão foi útil ou não."                                                                                                                                                                |
|Escopo Técnico Definido       |	A abordagem técnica foi decidida. Exemplo (para R10): "Foi definida a arquitetura RAG: o sistema irá vetorizar a pergunta do usuário, buscar os artigos mais relevantes na base de conhecimento e enviá-los como contexto para a IA generativa montar a resposta." Exemplo (para R09): "Foi definido que usaremos a API de Fine-Tuning do nosso provedor para criar um modelo customizado."                |

---

## 🏅 DoD - Definition of Done

|  Critério                       | Descrição                                                                                                                                                                                                                                                                                                                                                         |
| :-----------------------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|Código em Produção               |	Os novos serviços de IA (fine-tuning e RAG) foram integrados e estão operacionais no ambiente de homologação.                                                                                                                                                                                                                                                     |
|Critérios de Aceitação Atendidos |	As funcionalidades foram validadas contra os critérios. Exemplo (para R10): Foi confirmado que a IA não "alucina" (inventa respostas) e se restringe a responder com base na base de conhecimento. Exemplo (para R09): O processo de re-treino foi executado e um relatório comparando a precisão do modelo antigo com o novo foi gerado.                         |
|Testes Unitários/Integrados      |	A nova arquitetura está coberta por testes. Exemplo (para R10): Existe um teste de integração que valida todo o fluxo RAG, desde a vetorização da pergunta até a formatação final da resposta da IA.                                                                                                                                                              |
|Revisão de Código (Code Review)  |	O código foi revisado com foco em performance e custo. Exemplo: O PR foi analisado para garantir que não estamos fazendo chamadas desnecessárias e custosas para a API da IA.                                                                                                                                                                                     |
|Testes Manuais Realizados        |	O fluxo foi testado com perguntas abertas e cenários de falha. Exemplo (para R10): "1. Fiz uma pergunta cuja resposta está na base -> resposta veio correta. 2. Fiz uma pergunta ambígua -> a IA pediu mais detalhes ou deu uma resposta genérica segura. 3. Fiz uma pergunta mal-intencionada (prompt injection) -> o sistema tratou a entrada de forma segura." |
|Validação do PO                  |	O Product Owner validou o impacto no negócio. Exemplo: O PO confirmou que o novo modelo treinado (R09) comete visivelmente menos erros de classificação e que as respostas automáticas (R10) são úteis e podem efetivamente desviar chamados.                                                                                                                     |
|Documentação Atualizada          |	A documentação reflete as novas capacidades e processos. Exemplo: Foi criada uma página na documentação interna explicando como o administrador pode disparar o processo de re-treinamento da IA e como analisar os resultados.                                                                                                                                   |
|Sem Débitos Técnicos Graves      |	A solução é monitorável e segura. Exemplo: Foram implementados logs para monitorar o custo e a latência das chamadas à IA e para registrar o feedback dos usuários sobre as respostas sugeridas.                                                                                                                                                                  |

---

Função       | Nome                | Github                                                       |
------------ | --------------------| -------------------------------------------------------------|
Project Owner| Christian Fernandes | [Acessar Github](https://github.com/ChristianFernandesLemos) |
Scrum Master | Juan Vargas         | [Acessar Github](https://github.com/RenteriaJuan)            |
Dev Team     | Théo Pinto          | [Acessar Github](https://github.com/Thorphinm)               |
Dev Team     | Ana Beatriz         | [Acessar Github](https://github.com/Anasouza2802)            |
Dev Team     |Gustavo Gramacho     | [Acessar Github](https://github.com/gramachoo)               |
Dev Team     | Lukas Keiji         | [Acessar Github](https://github.com/Lucaskeiji)              |
