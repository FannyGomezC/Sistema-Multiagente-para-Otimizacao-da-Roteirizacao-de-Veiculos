# Sistema Multiagente para Otimização da Roteirização de Veículos com Auditoria e Certificação

[![Open in
Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/FannyGomezC/Sistema-Multiagente-para-Otimizacao-da-Roteirizacao-de-Veiculos/blob/main/Sistema_Multiagente_Otimiza%C3%A7%C3%A3o.ipynb)

# Aluna: Fanny Gómez Castillo

# Orientadora: Manoela Kolher

---

Trabalho apresentado ao curso BI MASTER como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

---

## Resumo

Este projeto apresenta o desenvolvimento de um sistema multiagente para
otimização da roteirização de veículos em operações de entrega. O
sistema recebe os dados e as condições operacionais definidos pelo
usuário e busca construir o melhor plano de viagens possível,
considerando diferentes objetivos de otimização e restrições
relacionadas à frota, capacidade, tempo, custos e atendimento dos
clientes.

A proposta vai além da geração de rotas. Após encontrar uma solução, o
sistema verifica sua viabilidade operacional, procura oportunidades de
melhoria e avalia sua qualidade matemática por meio de um processo de
certificação. Para isso, utiliza uma arquitetura de agentes
especializados, coordenados por um orquestrador e apoiados por uma
memória compartilhada, integrando métodos de otimização, auditoria
independente, análise de resultados e mecanismos de continuidade.

O núcleo de solução combina Google OR-Tools e Algoritmos Genéticos.
Quando necessário, agentes adicionais investigam alternativas para
melhorar o plano encontrado e fortalecer os limites matemáticos
utilizados na certificação. Essa abordagem permite distinguir uma
solução válida e operacionalmente utilizável de uma solução cuja
otimalidade foi matematicamente comprovada.

O sistema foi desenvolvido em Python e organizado em um notebook
executável no Google Colab. Sua avaliação experimental contemplou 17
cenários com diferentes dimensões, objetivos e dificuldades
operacionais, incluindo situações deliberadamente inviáveis. Os
resultados demonstraram a capacidade do sistema de produzir e auditar
planos, alcançar certificações de otimalidade em determinados problemas
e obter melhorias relevantes com tempo computacional adicional.

O principal diferencial do trabalho está na integração entre busca,
verificação, melhoria e certificação, oferecendo ao usuário não apenas
um plano de atendimento, mas também informações sobre sua validade,
qualidade e limitações matemáticas.

## Abstract

This project presents the development of a multi-agent system for
vehicle routing optimization in delivery operations. The system receives
user-defined operational data and constraints and seeks to construct the
best possible delivery plan while considering different optimization
objectives and requirements related to fleet availability, vehicle
capacity, time, costs, and customer service.

The proposed approach goes beyond route generation. After obtaining a
candidate solution, the system verifies its operational feasibility,
explores improvement opportunities, and assesses its mathematical
quality through a certification process. Its architecture integrates
specialized agents coordinated by a central orchestrator and supported
by shared memory, combining optimization methods, independent auditing,
result analysis, and optimization continuation mechanisms.

The solution core combines Google OR-Tools and Genetic Algorithms. When
additional computational time is available, specialized agents explore
alternatives to improve the current solution and strengthen the
mathematical bounds used for certification. This approach distinguishes
operationally feasible solutions from those whose optimality has been
mathematically demonstrated.

The system was developed in Python and implemented as an executable
Google Colab notebook. Its experimental evaluation included 17 scenarios
with different sizes, optimization objectives, and operational
complexities, including deliberately infeasible cases. The experiments
demonstrated the system's ability to generate and audit delivery plans,
certify optimality in selected instances, and achieve meaningful
improvements through additional optimization effort.

The main contribution of this work is the integration of solution
search, independent verification, improvement, and mathematical
certification into a coordinated multi-agent framework, providing users
with both an operational plan and a transparent assessment of its
validity, quality, and mathematical limitations.

## Introdução

A roteirização de veículos é um problema relevante para operações
logísticas, pois envolve decisões que influenciam diretamente o
aproveitamento da frota, os custos de transporte, o tempo de atendimento
e a utilização dos recursos disponíveis.

Em situações reais, definir um plano de entregas exige considerar
diferentes condições simultaneamente. Os veículos podem apresentar
capacidades e custos distintos, os clientes podem possuir janelas de
atendimento, o tempo de trabalho pode ser limitado e um mesmo veículo
pode realizar várias viagens ao longo da operação. Além disso, o
objetivo da otimização nem sempre é único: em determinados problemas,
interessa minimizar a distância percorrida; em outros, reduzir o tempo,
o custo ou a quantidade de veículos utilizados.

A combinação dessas condições aumenta a complexidade do problema e torna
importante utilizar métodos computacionais capazes de explorar
diferentes alternativas de solução. Entretanto, encontrar um plano com
bons indicadores não significa necessariamente encontrar uma solução
ótima. Também é necessário verificar se todas as restrições foram
respeitadas e identificar quais evidências matemáticas sustentam a
qualidade do resultado.

Foi a partir dessa necessidade que surgiu a proposta deste projeto:
desenvolver um sistema capaz de integrar diferentes especialistas
computacionais em um processo coordenado, no qual encontrar uma solução,
verificar sua validade, procurar melhorias e avaliar sua qualidade
matemática sejam etapas complementares.

O sistema foi concebido para receber problemas definidos pelo próprio
usuário e conduzir o processo desde a preparação dos dados até a
apresentação de um plano de atendimento acompanhado de indicadores,
diagnósticos, recomendações e informações sobre sua certificação.

Dessa forma, o trabalho procura responder a três questões fundamentais:
qual é a melhor solução encontrada, essa solução respeita efetivamente
as condições operacionais e até que ponto é possível demonstrar
matematicamente sua qualidade?

## Arquitetura Multiagente do Sistema

A arquitetura foi organizada a partir da distribuição de
responsabilidades entre componentes especializados. Em vez de concentrar
todo o processamento em um único algoritmo, o sistema estabelece um
fluxo de cooperação no qual diferentes agentes participam da preparação
do problema, da busca de soluções, da verificação de resultados e da
continuidade da otimização.

Um agente Orquestrador coordena esse trabalho, selecionando e acionando
os componentes necessários conforme as características do problema e o
estágio da execução.

A memória compartilhada mantém disponíveis os dados de entrada, as
soluções encontradas, os resultados de auditoria, os limites
matemáticos, os certificados e o histórico de processamento. Essa
estrutura permite preservar informações relevantes e manter a
consistência entre as diferentes etapas.

O funcionamento geral compreende a recepção e validação dos dados, a
tradução do problema, a construção de sua representação matemática, a
escolha das estratégias de busca, a obtenção de soluções candidatas, a
verificação independente de factibilidade, a auditoria, a certificação e
a apresentação dos resultados.

Quando a otimalidade ainda não foi demonstrada, o usuário pode autorizar
uma etapa adicional de otimização, na qual novos agentes procuram
melhorar a solução ou fortalecer a prova matemática disponível.

A arquitetura procura, assim, combinar especialização, coordenação e
continuidade, preservando a distinção entre o resultado encontrado, o
resultado validado e aquilo que foi efetivamente demonstrado.

## Estratégias de Otimização

O núcleo de otimização utiliza abordagens complementares para explorar o
espaço de soluções e construir planos de atendimento compatíveis com as
condições informadas.

### Google OR-Tools

O agente baseado em Google OR-Tools utiliza recursos especializados de
roteirização para construir soluções considerando as características e
restrições do problema. Essa abordagem permite explorar modelos
estruturados de roteamento e aplicar mecanismos de busca adequados à
organização de visitas, viagens e utilização dos veículos.

### Algoritmos Genéticos

O agente baseado em Algoritmos Genéticos trabalha com populações de
soluções e operadores de busca que permitem explorar diferentes
combinações de rotas, viagens e utilização da frota. Sua função é
ampliar a exploração de alternativas e procurar configurações
promissoras, especialmente em situações nas quais a estrutura do
problema apresenta maior complexidade combinatória.

### Integração das estratégias

A utilização de diferentes métodos amplia as possibilidades de
investigação do problema. O sistema pode selecionar estratégias conforme
suas características e aproveitar soluções candidatas produzidas por
diferentes processos.

Entretanto, nenhuma solução é considerada operacionalmente aceita apenas
por apresentar um bom valor da função objetivo. Antes de ser incorporada
ao resultado, precisa passar pelas verificações de factibilidade e
auditoria previstas pela arquitetura.

## Auditoria e Verificação Independente

A auditoria constitui uma etapa essencial do sistema, pois uma solução
numericamente interessante pode não ser operacionalmente válida. Por
essa razão, o projeto incorpora mecanismos de verificação independentes
do método utilizado para encontrar o plano.

Esses mecanismos conferem aspectos como atendimento dos clientes,
capacidade dos veículos, janelas de tempo, condições do depósito,
organização das viagens, distâncias, tempos, custos e demais restrições
estabelecidas pelo usuário.

A separação entre busca e verificação reduz o risco de apresentar uma
solução que aparentemente oferece bons resultados, mas não atende às
condições necessárias para sua execução.

Esse cuidado também orienta o tratamento de situações em que nenhum
plano válido é encontrado. O sistema procura preservar a diferença entre
não ter encontrado uma solução e ter demonstrado matematicamente que o
problema é inviável.

Assim, a auditoria não funciona apenas como uma conferência final, mas
como um mecanismo de controle da confiabilidade das respostas
apresentadas.

## Certificação Matemática da Solução

Além de verificar a validade operacional do plano, o sistema procura
avaliar sua proximidade em relação ao melhor resultado matematicamente
possível.

Para problemas de minimização, essa avaliação utiliza dois conceitos
fundamentais:

-   UB (Upper Bound): valor associado à melhor solução válida conhecida.
-   LB (Lower Bound): limite inferior matematicamente válido para o
    problema.

A relação entre esses valores permite calcular o GAP, que representa a
margem de incerteza matemática ainda existente entre a melhor solução
conhecida e o limite inferior demonstrado.

Quanto menor o GAP, mais estreito é o intervalo de incerteza sobre a
qualidade da solução. Quando os limites convergem dentro da tolerância
adotada, e as condições matemáticas necessárias são atendidas, existe
evidência para certificar sua otimalidade.

O sistema traduz essas informações em níveis de certificação,
facilitando a interpretação do resultado pelo usuário.

Essa etapa é especialmente importante porque uma solução
operacionalmente válida pode apresentar excelente desempenho sem que
ainda seja possível comprovar sua otimalidade. A certificação permite
comunicar essa diferença de maneira transparente, evitando tratar como
matematicamente comprovado aquilo que permanece em investigação.

## Continuidade da Otimização e Fortalecimento da Certificação

Quando a solução encontrada ainda não possui certificação completa, o
sistema oferece ao usuário a possibilidade de disponibilizar tempo
computacional adicional para continuar a investigação.

A continuidade atua em duas frentes complementares: melhorar o plano
operacional, buscando reduzir o UB, e fortalecer a prova matemática,
procurando elevar o LB.

Para isso, a arquitetura incorpora agentes especializados em otimização
por vizinhança, fortalecimento de limites, investigação da utilização de
diferentes quantidades de veículos, combinação de programações e
certificação exata.

Algumas tarefas podem avançar em paralelo, permitindo aproveitar melhor
o tempo disponível e explorar diferentes oportunidades de melhoria.

Durante esse processo, a melhor solução válida já aprovada é preservada.
Novas alternativas precisam ser verificadas antes de substituir o plano
atual.

A continuidade também considera que nem toda tentativa adicional produz
melhorias. Quando uma estratégia deixa de apresentar avanços, a
diversificação da busca pode ser mais útil do que repetir
indefinidamente o mesmo procedimento.

O resultado dessa etapa pode assumir diferentes formas: um plano
operacional melhor, uma certificação matemática mais forte ou avanços
simultâneos nas duas dimensões.

## Principais Componentes do Sistema

O sistema reúne os seguintes componentes principais, organizados
conforme suas responsabilidades.

### Preparação e representação do problema

-   `SharedMemory` --- memória compartilhada.
-   `UserInterface` --- interação com o usuário e entrada dos dados.
-   `ValidatorAgent` --- validação das informações recebidas.
-   `TranslatorAgent` --- tradução do problema para uma estrutura
    computacional.
-   `ClassifierAgent` --- seleção da estratégia inicial de resolução.
-   `MathAgent` --- representação matemática do problema.

### Busca, verificação e apresentação da solução

-   `ORToolsSolverAgent` --- busca de soluções com Google OR-Tools.
-   `GeneticAlgorithmSolverAgent` --- busca de soluções com Algoritmos
    Genéticos.
-   `IndependentFeasibilityVerifier` --- verificação independente da
    factibilidade.
-   `AuditorAgent` --- auditoria do plano e de seus resultados.
-   `InitialSolutionRefinerAgent` --- refinamento da solução inicial.
-   `OptimalityCertificationAgent` --- avaliação e certificação
    matemática.
-   `DiagnosticAgent` --- diagnóstico e recomendações.
-   `ExplainerAgent` --- explicação dos resultados.

### Continuidade e investigação matemática

-   `ContinuityOptimizationAgent` --- coordenação da continuidade.
-   `NeighborhoodOptimizationAgent` --- otimização por vizinhança.
-   `BoundStrengtheningAgent` --- fortalecimento dos limites inferiores.
-   `KVehicleFeasibilityCertifier` --- investigação da factibilidade com
    diferentes quantidades de veículos.
-   `VehicleProgramColumnAgent` --- combinação de programações de
    veículos.
-   `ContinuityExactCertificationAgent` --- certificação exata durante a
    continuidade.

### Coordenação geral

-   `OrchestratorAgent` --- coordenação do fluxo de execução e da
    cooperação entre os agentes.

Esses componentes são apoiados por ferramentas internas de controle de
recursos, persistência, restauração de sessões, investigação matemática
e comunicação dos resultados.

O notebook principal contém a descrição detalhada das responsabilidades,
da integração e do funcionamento dos agentes.

## Tecnologias Utilizadas

O sistema foi desenvolvido principalmente em Python, utilizando
bibliotecas e ferramentas voltadas à otimização, ao processamento de
dados, à visualização e à execução interativa.

Entre as tecnologias utilizadas estão:

-   Python
-   Google Colab
-   Google OR-Tools
-   PySCIPOpt / SCIP
-   NumPy
-   Pandas
-   SciPy
-   Matplotlib
-   PyDeck
-   OpenPyXL
-   ipywidgets

As bibliotecas auxiliares necessárias são preparadas pela célula de
configuração do ambiente no notebook.

A utilização do Google Colab permite reunir código, documentação
técnica, execução e apresentação de resultados em um único ambiente
acessível pelo navegador.

## Dados de Entrada e Configuração dos Problemas

O sistema foi desenvolvido para permitir que cada usuário configure seus
próprios problemas de roteirização, informando os parâmetros
operacionais e fornecendo os dados correspondentes.

Dependendo das características do problema, podem ser solicitadas
planilhas contendo informações sobre clientes e demandas, capacidades
dos veículos, custos e janelas de atendimento.

Os arquivos podem ser fornecidos em formato `.xlsx` e, nas condições
indicadas no notebook, também em CSV.

Entre os parâmetros considerados estão o objetivo da otimização, a
composição da frota, a capacidade de transporte, o tempo disponível, as
condições de atendimento e as regras de utilização dos veículos.

O sistema também contempla problemas com múltiplos objetivos, permitindo
representar diferentes prioridades por meio de pesos definidos pelo
usuário.

É importante utilizar a mesma unidade de carga para demanda e
capacidade, pois o sistema não realiza conversão automática entre
unidades como toneladas, quilogramas ou caixas.

As orientações detalhadas sobre os formatos de entrada e o preenchimento
das informações estão disponíveis no notebook.

## Como Executar o Sistema

O projeto foi organizado em um notebook executável no Google Colab,
permitindo acompanhar todas as etapas do processo, desde a preparação
dos dados até a interpretação dos resultados.

Para executar o sistema:

1.  Abra o notebook principal no Google Colab utilizando o botão Open in
    Colab, disponível no início deste README.
2.  Utilize a opção `Ambiente de execução → Executar tudo`.
3.  Na seção `ACIONAMENTO DO SISTEMA`, informe os parâmetros do problema
    e carregue as planilhas solicitadas.
4.  Aguarde a execução dos métodos de otimização, das verificações e da
    certificação.
5.  Caso seja oferecida a opção, autorize tempo computacional adicional
    para continuar a otimização.
6.  Consulte a seção `RESULTADOS AO CLIENTE` para visualizar o plano
    consolidado e as informações de avaliação.

O notebook apresenta explicações sobre a arquitetura, os agentes, os
dados necessários e o funcionamento das principais etapas. O sumário
lateral do Google Colab permite navegar entre suas seções.

## Apresentação e Interpretação dos Resultados

Ao final da execução, o sistema apresenta o melhor plano válido
encontrado e informações que auxiliam sua interpretação.

A análise considera três dimensões complementares.

A primeira é operacional e descreve como os clientes, as viagens e os
veículos foram organizados, incluindo indicadores relacionados à
distância, ao tempo, ao custo e à utilização da frota.

A segunda corresponde à factibilidade e informa se o plano atende às
condições e restrições estabelecidas para o problema.

A terceira é a qualidade matemática, que apresenta as evidências
disponíveis sobre a proximidade entre a solução encontrada e o melhor
resultado possível.

O sistema disponibiliza um infográfico com os principais indicadores,
recursos de visualização, detalhamento do plano de atendimento,
diagnósticos e recomendações.

Essa apresentação procura transformar resultados técnicos em informações
compreensíveis e úteis para a análise da operação, sem perder a
distinção entre desempenho observado e garantia matemática.

## Checkpoint e Retomada da Otimização

O sistema permite salvar o estado da otimização em um arquivo de
checkpoint, possibilitando retomar posteriormente o trabalho realizado.

O arquivo preserva informações como dados de entrada, plano encontrado,
certificado e histórico registrado durante a execução.

Quando um checkpoint é carregado, o plano passa novamente pelas
verificações previstas pelo sistema, preservando os controles de
consistência e factibilidade.

Esse mecanismo permite continuar a investigação do mesmo problema sem
desconsiderar o trabalho anterior.

O checkpoint não deve ser utilizado para alterar os dados do problema
mantendo uma certificação obtida anteriormente, pois qualquer mudança
nas condições pode modificar a validade e a qualidade matemática do
resultado.

## Avaliação Experimental

Para analisar o comportamento do sistema em diferentes condições, foi
realizada uma bateria experimental com 17 cenários, variando o número de
clientes, os objetivos de otimização e a dificuldade operacional.

Os testes foram estruturados para observar a obtenção de planos válidos,
o comportamento da certificação em diferentes dimensões de problema, os
efeitos da continuidade e a resposta a situações deliberadamente
inviáveis.

A avaliação também procurou distinguir dois desafios que nem sempre
evoluem da mesma maneira: encontrar uma boa solução operacional e
demonstrar matematicamente que ela é ótima.

Nos problemas menores, o sistema conseguiu alcançar certificações
completas em diferentes configurações. Nos cenários maiores, a obtenção
de planos válidos continuou sendo possível nos casos operacionais
avaliados, mas o fechamento da certificação matemática tornou-se mais
exigente.

Os testes de continuidade permitiram observar melhorias tanto no valor
da função objetivo quanto no fortalecimento dos limites inferiores,
demonstrando que o tempo adicional pode produzir avanços em dimensões
diferentes do processo.

Os resultados completos, as comparações e sua interpretação estão
documentados no notebook principal.

## Resultados Experimentais

A bateria de testes apresentou evidências relevantes sobre a capacidade
de busca, a confiabilidade das verificações e a evolução da
certificação.

### Certificação em problemas de diferentes dimensões

Nos cenários menores, foram obtidas certificações de otimalidade para
problemas com cinco clientes e diferentes objetivos, além de
configurações com oito e dez clientes.

Também foi registrada certificação completa em um dos cenários
operacionais com 12 clientes.

Em problemas maiores, permaneceram margens matemáticas abertas, ainda
que o sistema tivesse encontrado soluções auditadas. Entre os resultados
documentados estão GAPs finais de 20,17% para um cenário com 30
clientes, 7,25% para 45 clientes, 5,55% para 55 clientes e 13,33% para
80 clientes.

Esses valores representam a margem de certificação ainda não fechada e
não devem ser interpretados diretamente como percentual de desperdício
operacional.

### Melhorias obtidas com a continuidade

Os experimentos também mostraram que a continuidade pode produzir ganhos
relevantes.

No cenário D30, com 30 clientes, houve redução de 17,0% no valor da
função objetivo e evolução do GAP de 59,73% para 20,17%.

No cenário O55, com 55 clientes, a função objetivo foi reduzida em
11,7%, enquanto o GAP passou de 26,60% para 5,55%.

No cenário D80, com 80 clientes, foi registrada redução de 36,4% na
função objetivo, acompanhada da diminuição do GAP de 59,50% para 13,33%.

Um resultado particularmente ilustrativo ocorreu no cenário O12. Nesse
caso, o plano operacional não precisou ser alterado, mas o
fortalecimento do limite matemático reduziu o GAP de 9,99% para menos de
0,001%.

Esse comportamento demonstra que melhorar a solução e melhorar a certeza
matemática sobre sua qualidade são contribuições distintas. Mesmo quando
não se encontra uma rota melhor, a continuidade pode acrescentar valor
ao fortalecer a certificação.

### Resposta às restrições operacionais

A avaliação incluiu cenários com 60 clientes e diferentes tempos de
atendimento, mostrando que alterações nas condições operacionais
modificam a estrutura do problema e influenciam o espaço de soluções.

Também foram executados dois controles deliberadamente inviáveis: um
relacionado à incompatibilidade de capacidade e outro às janelas de
tempo.

Nesses casos, nenhum plano auditado foi entregue como solução
operacional.

Esse resultado é importante para a confiabilidade do sistema, embora a
ausência de um plano encontrado não constitua, isoladamente, prova
matemática de inviabilidade.

### Síntese dos resultados

Os experimentos evidenciaram que o sistema consegue combinar diferentes
mecanismos de otimização, submeter soluções à auditoria independente,
reconhecer distintos níveis de certificação e continuar a investigação
quando existe tempo computacional disponível.

Os resultados também mostraram que a dificuldade de comprovar a
otimalidade tende a aumentar conforme cresce a complexidade do problema,
mesmo quando já existe um plano operacional válido.

A contribuição do sistema, portanto, não está apenas na obtenção de boas
soluções, mas na capacidade de apresentar o resultado juntamente com as
evidências que sustentam sua validade e sua qualidade matemática.

## Conclusões

O desenvolvimento deste projeto permitiu construir e avaliar uma
arquitetura multiagente voltada à resolução de problemas de roteirização
de veículos, integrando métodos de otimização, verificação independente,
auditoria, certificação matemática e continuidade da busca.

A experiência demonstrou que a especialização dos agentes produz maior
valor quando acompanhada de uma coordenação consistente e de mecanismos
que preservam as informações e os resultados obtidos ao longo da
execução. A memória compartilhada e o papel do orquestrador foram
fundamentais para organizar essa cooperação.

Outro aprendizado importante foi compreender que a qualidade de uma
solução não pode ser avaliada apenas pelo valor da função objetivo. Um
plano precisa respeitar as restrições operacionais e, quando se pretende
afirmar sua otimalidade, apresentar evidências matemáticas suficientes
para sustentar essa conclusão.

A bateria experimental mostrou que o sistema pode alcançar certificações
completas em determinados cenários e produzir melhorias expressivas em
problemas de maior dimensão. Também evidenciou que o fortalecimento da
prova matemática pode representar um avanço relevante, mesmo quando o
plano operacional permanece inalterado.

Os testes com condições incompatíveis reforçaram a importância de não
apresentar soluções inválidas como recomendações operacionais e de
distinguir resultados inconclusivos de demonstrações formais de
inviabilidade.

O trabalho também revelou oportunidades de evolução relacionadas à
eficiência computacional, à exploração de novas estratégias de busca e
ao fortalecimento dos limites matemáticos em problemas mais complexos.
Essas possibilidades constituem caminhos naturais para o aperfeiçoamento
futuro do sistema.

Mais do que desenvolver um mecanismo para gerar rotas, a proposta foi
construir um processo de otimização capaz de explicar o que foi
encontrado, verificar o que pode ser executado e demonstrar, dentro das
evidências disponíveis, o quanto se conhece sobre a qualidade da
solução.

Nesse sentido, o projeto representa uma aplicação integrada de
Inteligência Artificial e Otimização, orientada não apenas à busca de
resultados, mas também à sua confiabilidade, interpretação e evolução.

## Declaração de Uso de Inteligência Artificial

Durante o desenvolvimento deste projeto, foram utilizadas ferramentas de
Inteligência Artificial Generativa (Gemini, ChatGPT e Codex) como apoio
à programação, análise da arquitetura, revisão de código, identificação
de problemas e avaliação de alternativas técnicas.

A concepção inicial do sistema, a análise crítica das sugestões, as
decisões de desenvolvimento e a validação dos resultados foram
conduzidas pela autora, que também teve papel ativo na identificação de
oportunidades de melhoria e na proposição de novas abordagens para
superar limitações, explorar alternativas de otimização e impulsionar a
evolução do sistema.

A autora permanece responsável pelo conteúdo e pelas conclusões do
trabalho. 

A declaração completa sobre a utilização dessas ferramentas está
disponível no início do notebook.

---

Matrícula: 241.100.158

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação Business Intelligence Master


