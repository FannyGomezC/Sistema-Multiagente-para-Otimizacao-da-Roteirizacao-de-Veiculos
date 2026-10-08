# Sistema-Multiagente-para-Otimizacao-da-Roteirizacao-de-Veiculos

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/FannyGomezC/Sistema-Multiagente-para-Otimizacao-da-Roteirizacao-de-Veiculos/blob/main/Sistema_Multiagente_Otimiza%C3%A7%C3%A3o.ipynb)

Este projeto apresenta um sistema  que recebe um problema de otimização de roteirização de veículos orientado a entregas e busca encontrar o melhor plano de viagens possível, considerando os objetivos e as restrições definidos pelo usuário. 

Após encontrar uma solução, o sistema verifica sua viabilidade operacional, busca oportunidades de melhoria e avalia sua qualidade matemática por meio de um processo de certificação baseado na relação entre a melhor solução encontrada e um limite matemático calculado.

O sistema foi desenvolvido em Python e organizado em um notebook executável no Google Colab, permitindo acompanhar desde a entrada dos dados até a apresentação e interpretação dos resultados.

Trata-se de um sistema robusto, que combina especialização dos agentes, coordenação, auditoria, continuidade e rigor na interpretação das evidências matemáticas.

A arquitetura multiagente distribui as diferentes responsabilidades entre componentes especializados. Há agentes responsáveis por receber e validar os dados, traduzir o problema, construir sua representação matemática, buscar soluções, verificar sua factibilidade, realizar auditorias, explicar os resultados e avaliar a qualidade matemática da solução. Um agente Orquestrador coordena esse trabalho, enquanto uma memória compartilhada mantém os dados, soluções, certificados e histórico disponíveis ao longo da execução.

Assim, além de responder à pergunta “Qual foi a melhor solução encontrada?”, o sistema também procura responder: essa solução é realmente válida? Ainda é possível melhorá-la? Quão próxima ela está da solução ótima?

## Estratégias de otimização

O núcleo de otimização combina diferentes abordagens de busca:

1.	OR-Tools: O agente baseado em Google OR-Tools utiliza recursos especializados de roteirização para construir soluções considerando as características do problema informado.
   
2.	Algoritmos Genéticos: O agente baseado em Algoritmos Genéticos trabalha com populações de soluções e operadores de busca para explorar diferentes combinações de rotas e utilização dos veículos.
   
As soluções produzidas pelos métodos de busca são tratadas como candidatas. Antes de serem aceitas como plano operacional, passam pelas etapas de verificação previstas pelo sistema.

## Auditoria e verificação

O sistema possui mecanismos independentes de verificação e auditoria para conferir aspectos como:

•	atendimento dos clientes;

•	capacidade dos veículos;

•	horários;

•	depósito;

•	viagens;

•	distâncias;

•	tempos;

•	custos;

•	demais restrições definidas no problema.

Essa separação reduz o risco de uma solução numericamente interessante ser apresentada mesmo violando alguma condição operacional.

## Certificação da solução

O sistema procura avaliar quão próxima uma solução encontrada está do melhor resultado matematicamente possível.

Para isso, trabalha com dois conceitos:

•	UB (Upper Bound) — valor associado à melhor solução válida conhecida;

•	LB (Lower Bound) — limite inferior matematicamente válido para o problema.

A diferença entre esses valores é utilizada para calcular o GAP.

Quanto menor o GAP, menor é a região de incerteza entre a solução encontrada e o limite matemático conhecido.

Quando UB e LB convergem dentro da tolerância adotada, existe evidência matemática para certificar a otimalidade da solução.

O sistema traduz essas informações em níveis de certificação para facilitar a interpretação do resultado.

## Continuidade da otimização

Se ainda não foi possível comprovar a otimalidade da solução, o sistema oferece ao usuário a possibilidade de continuar o processo por um tempo computacional adicional.

A continuidade atua principalmente em duas frentes: melhorar o plano encontrado, reduzindo o UB, e fortalecer a prova matemática, elevando o LB. Algumas tarefas podem ser executadas em paralelo para aproveitar melhor o tempo computacional disponível e reduzir o GAP.

Para isso, o sistema conta com agentes especializados em otimização por vizinhança, fortalecimento de limites, investigação de soluções com diferentes quantidades de veículos, combinação de programações e certificação exata.

Durante esse processo, o melhor plano já aprovado é preservado.

Ao final, o sistema apresenta o melhor plano encontrado por meio de um infográfico que reúne os principais indicadores e resultados. Também é apresentado um plano de atendimento com o detalhamento da solução e recomendações adicionais.

## Principais componentes do sistema:

Entre os componentes implementados no sistema estão:

•	SharedMemory — memória compartilhada;

•	UserInterface — interação e entrada dos dados;

•	ValidatorAgent — validação;

•	TranslatorAgent — tradução do problema;

•	ClassifierAgent — seleção da estratégia inicial;

•	MathAgent — representação matemática;

•	ORToolsSolverAgent — solução baseada em OR-Tools;

•	GeneticAlgorithmSolverAgent — solução baseada em Algoritmo Genético;

•	IndependentFeasibilityVerifier — verificação independente;

•	AuditorAgent — auditoria;

•	InitialSolutionRefinerAgent — refinamento da solução inicial;

•	OptimalityCertificationAgent — certificação;

•	DiagnosticAgent — diagnóstico;

•	ExplainerAgent — explicação dos resultados;

•	ContinuityOptimizationAgent — coordenação da continuidade;

•	NeighborhoodOptimizationAgent — otimização de vizinhança;

•	BoundStrengtheningAgent — fortalecimento de limites;

•	KVehicleFeasibilityCertifier — investigação da factibilidade com diferentes quantidades de veículos;

•	VehicleProgramColumnAgent — combinação de programações;

•	ContinuityExactCertificationAgent — certificação exata durante a continuidade;

•	OrchestratorAgent — coordenação geral do sistema.

O notebook contém a descrição detalhada das responsabilidades e do funcionamento desses componentes.

## Tecnologias utilizadas

O projeto foi desenvolvido principalmente com:

•	Python;

•	Google Colab;

•	Google OR-Tools;

•	PySCIPOpt / SCIP;

•	NumPy;

•	Pandas;

•	SciPy;

•	Matplotlib;

•	PyDeck;

•	OpenPyXL;

•	ipywidgets.

Outras bibliotecas auxiliares são instaladas automaticamente pela célula de preparação do ambiente.

## Como executar

O sistema foi preparado para ser executado diretamente no Google Colab.

1.	Abra o arquivo Sistema_Multiagente_Otimizacao.ipynb no Google Colab.
2.	Utilize a opção executar tudo.
3.	Na seção ACIONAMENTO DO SISTEMA deverá inserir os parâmetros do problema e enviar as planilhas solicitadas.
4.	Aguarde a execução da otimização e das verificações.
5.	Caso deseje, autorize tempo adicional para continuidade da otimização.
6.	Na seção RESULTADOS AO CLIENTE poderá visualizar o resultado consolidado.

O próprio notebook contém instruções detalhadas sobre o formato dos dados e sobre cada etapa da execução.

## Dados de entrada

Dependendo da configuração escolhida, o sistema pode solicitar planilhas contendo:

•	clientes e demandas;

•	capacidades dos veículos;

•	custos;

•	janelas de atendimento.

Os arquivos podem ser fornecidos em .xlsx e, nas condições indicadas no notebook, também em CSV.

É importante utilizar a mesma unidade para demanda e capacidade, pois o sistema não realiza conversão automática entre unidades de carga.

## Resultados

Ao final da execução, o sistema apresenta não apenas as viagens encontradas, mas informações para auxiliar na avaliação do resultado.

A análise considera três dimensões principais:

•	Operacional: como clientes, viagens e veículos foram organizados.

•	Factibilidade: se o plano respeita as condições e restrições informadas.

•	Qualidade matemática: quais evidências existem sobre a proximidade entre a solução encontrada e a solução ótima.

O sistema também disponibiliza recursos de diagnóstico, visualização e explicação dos resultados.

## Checkpoint e continuidade

O estado da otimização pode ser salvo em um checkpoint para permitir que o trabalho seja retomado posteriormente.

O arquivo preserva informações como dados de entrada, plano, certificado e histórico registrado. Ao ser carregado novamente, o plano passa pelas verificações previstas pelo sistema.

O checkpoint é destinado à retomada do mesmo problema e não à alteração dos dados mantendo uma certificação anterior.

## Avaliação experimental

O sistema foi avaliado em uma bateria de 17 cenários, variando porte, objetivo e dificuldade operacional.

Os testes foram utilizados para observar, entre outros aspectos:

•	obtenção de planos válidos;
•	comportamento da certificação em diferentes tamanhos de problema;
•	melhoria da solução com tempo adicional;
•	fortalecimento dos limites matemáticos;
•	resposta a situações deliberadamente inviáveis.

Os resultados completos e sua interpretação estão documentados no notebook.

Um dos principais aprendizados observados nos experimentos é que encontrar uma boa solução e provar matematicamente que ela é ótima são tarefas diferentes. Em problemas maiores, o sistema pode encontrar e melhorar planos operacionais mesmo quando a certificação completa exige esforço computacional adicional.

## Sobre este projeto

Este trabalho foi desenvolvido como um projeto de aplicação de técnicas de Inteligência Artificial e Otimização, explorando a cooperação entre agentes para resolver e avaliar problemas de roteirização.

Mais do que produzir uma rota, a proposta foi construir um processo capaz de separar claramente o que foi encontrado, o que foi validado e o que foi matematicamente demonstrado.

As explicações detalhadas da arquitetura, dos agentes, da execução, dos experimentos e das lições aprendidas durante a execução do projeto estão disponíveis no notebook principal.

## Declaração de uso de Inteligência Artificial

Durante o desenvolvimento deste projeto, foram utilizadas ferramentas de Inteligência Artificial Generativa (Gemini, ChatGPT e Codex) como apoio à programação, análise da arquitetura, revisão de código, identificação de problemas e avaliação de alternativas técnicas.

A concepção inicial do sistema, a análise crítica das sugestões, as decisões de desenvolvimento e a validação dos resultados foram conduzidas pela autora, que também teve papel ativo na identificação de oportunidades de melhoria e na proposição de novas abordagens para superar limitações, explorar alternativas de otimização e impulsionar a evolução do sistema.

A autora permanece responsável pelo conteúdo e pelas conclusões do trabalho.

A declaração completa sobre a utilização dessas ferramentas está disponível no início do notebook.


