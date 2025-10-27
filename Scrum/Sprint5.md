## Documentação - Sprint 5

---
## 🏅 Desafio

O desafio desta sprint é construir a camada de governança e visibilidade da plataforma. Após sprints focadas nas funcionalidades para usuários, agentes e na implementação de IA, o objetivo agora é criar as ferramentas essenciais para que os administradores possam gerenciar e medir a saúde do sistema. Ao final da sprint, o administrador terá controle total sobre quem acessa a plataforma e uma visão clara dos seus indicadores de desempenho, transformando a aplicação de uma ferramenta funcional em um serviço gerenciável e baseado em dados.

---
## 📋 User Stories

| Prioridade | User Story                                                                                                                                       | Sprint | Requisito do Cliente | Status   |
| :--------: | -----------------------------------------------------------------------------------------------------------------------------------------------  | :----: | :------------------: | :------: |
|    Baixa	 | Como administrador, quero gerenciar os usuários do sistema (adicionar, editar, remover), para ter controle sobre quem acessa a plataforma.       |   5    | R011                 |    ✅    |
|    Baixa	 |	Como administrador, quero visualizar um painel de controle com métricas importantes, para monitorar o desempenho.                               |   5    | R012                 |    ✅    |

---

## 🏅 DoR - Definition of Ready

|  Critério                    | Descrição                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| :--------------------------: | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|Formato da História           |	As histórias estão claras e focadas no valor gerado para o perfil de Administrador.                                                                                                                                                                                                                                                                                                                                                                                                           |
|Critérios de Aceitação Claros |	As regras de negócio e os requisitos de dados estão bem definidos. Exemplo (para R12): "1. O painel deve exibir 3 métricas principais: Total de chamados abertos, Tempo médio de resolução e Total de chamados criados nos últimos 7 dias. 2. Os dados devem ser atualizados ao carregar a página." Exemplo (para R11): "O administrador deve poder alterar o perfil de um usuário (de 'usuário' para 'agente'), mas não pode remover um agente que possua chamados ativos atribuídos a ele." |
|Independência                 |	As histórias podem ser desenvolvidas em paralelo, pois não possuem dependência direta uma da outra.                                                                                                                                                                                                                                                                                                                                                                                           |
|Valor de Negócio              |	O propósito das ferramentas de gestão está claro. Exemplo: A equipe entende que o painel (R12) é o primeiro passo para permitir que a gestão tome decisões informadas sobre a necessidade de contratar mais agentes, por exemplo.                                                                                                                                                                                                                                                             |
|Estimativa Acordada           |	As histórias foram estimadas, considerando o trabalho de backend para agregação de dados e de frontend para a criação das interfaces de gestão.                                                                                                                                                                                                                                                                                                                                               |
|Dependências Mapeadas         |	As ferramentas necessárias foram escolhidas. Exemplo (para R12): "Foi decidido usar a biblioteca Chart.js para a visualização dos gráficos no frontend. A biblioteca já foi adicionada ao projeto."                                                                                                                                                                                                                                                                                           |
|Protótipos/Mockups Anexados   |	As interfaces de administração estão desenhadas. Exemplo (para R11 e R12): "O link do Figma contém os layouts para a tela de 'Gestão de Usuários' (com a tabela e os modais de edição/criação) e para a tela do 'Dashboard'."                                                                                                                                                                                                                                                                 |
|Escopo Técnico Definido       |	Os contratos de API estão definidos. Exemplo (para R12): "O Backend fornecerá um endpoint GET /api/metrics que retornará um único JSON com todos os dados para o painel." Exemplo (para R11): "A gestão de usuários será feita via uma API REST nos endpoints GET, POST, PUT, DELETE /api/users."                                                                                                                                                                                             |

---

## 🏅 DoD - Definition of Done

|  Critério                       | Descrição                                                                                                                                                                                                                                                                                                                                    |
| :-----------------------------: | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: |
|Código em Produção               |	As novas seções de 'Gestão de Usuários' e 'Dashboard' foram integradas à branch principal e estão disponíveis no ambiente de homologação.                                                                                                                                                                                                    |
|Critérios de Aceitação Atendidos |	As regras de negócio e os dados foram validados. Exemplo (para R12): "Os números exibidos no painel foram checados contra consultas diretas no banco de dados para garantir sua precisão." Exemplo (para R11): "Foi confirmado que ao remover um usuário, seus dados são devidamente anonimizados ou removidos conforme a regra de negócio." |
|Testes Unitários/Integrados      |	A segurança e as permissões foram testadas. Exemplo (para R11): "Existem testes automatizados que garantem que um usuário com perfil 'agente' receba um erro de 'Acesso Negado (403)' ao tentar acessar as APIs de gestão de usuários."                                                                                                      |
|Revisão de Código (Code Review)  |	O Pull Request foi revisado com foco em segurança e performance. Exemplo: A revisão do PR do painel (R12) garantiu que as consultas ao banco de dados para agregar as métricas são otimizadas e não causam lentidão.                                                                                                                         |
|Testes Manuais Realizados        |	Os fluxos de administração foram testados de ponta a ponta. Exemplo (para R11): "1. Loguei como admin. 2. Criei um novo usuário 'agente'. 3. Editei o perfil de um usuário existente. 4. Tentei remover um agente com chamados ativos (recebi o erro esperado). 5. Desatribuí os chamados e então consegui remover o agente."                |
|Validação do PO                  |	O Product Owner validou a usabilidade e o valor das ferramentas. Exemplo: "O PO confirmou que o painel (R12) exibe as métricas mais críticas para a operação e que a ferramenta de gestão de usuários (R11) é intuitiva e cobre as necessidades de controle de acesso."                                                                      |
|Documentação Atualizada          |	A documentação da API foi atualizada para refletir os novos endpoints de administração.                                                                                                                                                                                                                                                      |
|Sem Débitos Técnicos Graves      |	As funcionalidades foram implementadas de forma segura, garantindo que as operações de escrita (CRUD de usuários) gerem logs de auditoria.                                                                                                                                                                                                   |

---
## Integrantes 👥 <a id="integrantes"></a>

Função       | Nome                | Github                                                       |
------------ | --------------------| -------------------------------------------------------------|
Project Owner| Christian Fernandes | [Acessar Github](https://github.com/ChristianFernandesLemos) |
Scrum Master | Juan Vargas         | [Acessar Github](https://github.com/RenteriaJuan)            |
Dev Team     | Théo Pinto          | [Acessar Github](https://github.com/Thorphinm)               |
Dev Team     | Ana Beatriz         | [Acessar Github](https://github.com/Anasouza2802)            |
Dev Team     |Gustavo Gramacho     | [Acessar Github](https://github.com/gramachoo)               |
Dev Team     | Lukas Keiji         | [Acessar Github](https://github.com/Lucaskeiji)              |
