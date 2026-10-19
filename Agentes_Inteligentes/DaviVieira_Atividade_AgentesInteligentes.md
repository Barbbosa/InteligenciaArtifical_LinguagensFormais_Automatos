# Atividade sobre agentes inteligentes

Aula 19/10/2026 | Professora Kadidja Valéria | Inteligência artificial

**Disciplina:** Inteligência Artificial, Linguagens Formais e Autômatos

**Estudante:** Davi Vieira Lima | **Turma:** N1_2122

---

## Exercício 2.3

### a. Um agente que detecta apenas informações parciais sobre o estado não pode ser perfeitamente racional.

- **Julgamento:** F
- **Justificativa:** Estar com informação parcial não tira a racionalidade. Ser racional é escolher a ação que maximiza o desempenho esperado com o que o agente percebeu e sabe, e não ter acesso a tudo.
- **Exemplo ou contraexemplo:** O aspirador de pó só enxerga o quadrado em que está e ainda assim é racional no cenário do capítulo (1.000 passos, um ponto por quadrado limpo). Um jogador de pôquer também não vê as cartas dos outros.

### b. Existem ambientes de tarefa nos quais nenhum agente reativo puro pode comportar-se racionalmente.

- **Julgamento:** V
- **Justificativa:** O agente reativo puro olha só a percepção atual. Se a boa decisão depende do que aconteceu antes e o ambiente é parcialmente observável, ele não tem como acertar sempre.
- **Exemplo ou contraexemplo:** No mundo do aspirador com penalidade por movimento, quando os dois quadrados já foram limpos o certo é parar. Ao perceber só [A, Limpo], o agente não sabe se B também está limpo.

### c. Existe um ambiente de tarefa em que todo agente é racional.

- **Julgamento:** V
- **Justificativa:** Basta um ambiente em que nenhuma escolha muda o resultado, porque aí qualquer ação dá o mesmo desempenho e nenhum agente fica pior que o outro.
- **Exemplo ou contraexemplo:** Um ambiente em que a medida de desempenho é sempre a mesma, faça o agente o que fizer. Todos os agentes são racionais nele (é um caso meio artificial, mas serve como prova de existência).

### d. A entrada para o programa de agente é a mesma que a entrada para a função de agente.

- **Julgamento:** F
- **Justificativa:** O programa recebe só a percepção atual. A função de agente recebe a sequência inteira de percepções. Se a ação depende do histórico, o programa precisa guardar essa memória por conta própria.
- **Exemplo ou contraexemplo:** O aspirador reativo da Figura 2.8 usa só [posição, situação]. Já a tabela da Figura 2.3 usa sequências como [A, Limpo], [A, Sujo].

### e. Toda função de agente é implementável por uma combinação de programa/máquina.

- **Julgamento:** F
- **Justificativa:** A função é uma descrição matemática e pode pedir algo que nenhuma máquina consegue executar: memória ou tempo demais, ou até algo não computável.
- **Exemplo ou contraexemplo:** Uma função que devolve a ação certa dependendo de se um programa qualquer vai parar (problema da parada) não tem programa possível. A tabela completa do xadrez (10^150 entradas) também não cabe em máquina nenhuma.

### f. Suponha que um agente selecione sua ação uniformemente ao acaso do conjunto de ações possíveis. Existe um ambiente de tarefa determinista em que esse agente é racional.

- **Julgamento:** V
- **Justificativa:** Se todas as ações levam ao mesmo desempenho, escolher ao acaso é tão bom quanto qualquer outra escolha. Isso pode acontecer num ambiente determinista.
- **Exemplo ou contraexemplo:** Ambiente determinista em que as ações disponíveis dão sempre a mesma pontuação (ou existe só uma ação útil). Sortear a ação não perde nada.

### g. É possível para um dado agente ser perfeitamente racional em dois ambientes de tarefa distintos.

- **Julgamento:** V
- **Justificativa:** Se o comportamento ótimo for o mesmo nos dois ambientes, o mesmo agente pode ser perfeitamente racional em ambos.
- **Exemplo ou contraexemplo:** Dois mundos de aspirador de pó iguais, só que com a cor do piso diferente. A cor não entra na medida de desempenho, então o mesmo agente é racional nos dois.

### h. Todo agente é racional em um ambiente não observável.

- **Julgamento:** F
- **Justificativa:** Sem sensores o agente ainda precisa escolher bem com o que sabe de antemão. Se escolher mal, é irracional do mesmo jeito.
- **Exemplo ou contraexemplo:** Um aspirador sem sensor que sempre responde “Nada” nunca limpa. Sabendo que pode haver sujeira, ele seria melhor alternando Aspirar e mover, então esse agente não é racional.

### i. Um agente jogador de pôquer perfeitamente racional nunca perde.

- **Julgamento:** F
- **Justificativa:** Racionalidade maximiza o desempenho esperado, não o real. No pôquer há sorte nas cartas e informação escondida, então dá para jogar certo e mesmo assim perder.
- **Exemplo ou contraexemplo:** Apostar forte com um par de ases é a decisão racional, mas o adversário pode ter uma trinca de sorte e levar a mão.

---

## Exercício 2.4

### Caso 1 — Jogar futebol

- **Agente analisado:** Jogar futebol. O agente é um jogador de uma equipe (um meio-campista, por exemplo), e não o time inteiro.
- **Objetivo e hipóteses:** Ajudar o time a vencer. Hipótese: partida oficial, 11 contra 11, com árbitro.
- **P — Medida de desempenho:** Gols a favor e contra, vitória da equipe, passes certos, bolas recuperadas, poucas faltas.
- **E — Ambiente:** Campo, bola, companheiros, adversários, árbitro e torcida.
- **A — Atuadores:** Pernas e pés (chute, passe, corrida), cabeça, tronco, voz.
- **S — Sensores:** Olhos, ouvidos, tato e noção do próprio corpo (propriocepção).

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | Não vejo quem está atrás de mim nem o que os outros pretendem fazer. |
| Número de agentes | Multiagente (cooperativo e competitivo) | Coopero com o time e disputo com os adversários. |
| Previsibilidade | Estocástico | A bola quica de forma irregular e ninguém prevê exatamente o que o outro vai fazer. |
| Dependência entre decisões | Sequencial | Um passe ou um posicionamento agora muda as jogadas seguintes. |
| Mudança durante a decisão | Dinâmico | O jogo não para enquanto eu decido. |
| Natureza dos elementos | Contínuo | Posição, velocidade, tempo e movimentos variam de forma suave. |
| Conhecimento do funcionamento | Conhecido | Conheço as regras e a física da bola, mesmo sem ver tudo. |

### Caso 2 — Explorar os oceanos subterrâneos de Titã

- **Agente analisado:** Explorar o oceano sob o gelo de Titã. O agente é um submarino robótico autônomo (cenário hipotético).
- **Objetivo e hipóteses:** Mapear e coletar dados. Hipóteses: há oceano líquido sob o gelo e a comunicação com a Terra tem grande atraso, então o robô decide sozinho.
- **P — Medida de desempenho:** Qualidade e quantidade dos dados e amostras, áreas mapeadas, robô sobrevivendo e energia bem gasta.
- **E — Ambiente:** Água sob o gelo, alta pressão, baixa temperatura, correntes, paredes de gelo e sedimentos.
- **A — Atuadores:** Propulsores, lemes, braço coletor, broca térmica, transmissor acústico.
- **S — Sensores:** Sonar, câmeras, sensores de pressão, temperatura e química, giroscópio e medidor de energia.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | Água escura e turva, sonar com ruído e partes do oceano fora de alcance. |
| Número de agentes | Agente único | Na hipótese adotada não há outros agentes agindo no ambiente. |
| Previsibilidade | Estocástico | Correntes, movimento do gelo e falhas de equipamento são imprevisíveis. |
| Dependência entre decisões | Sequencial | Gastar energia ou entrar numa caverna afeta tudo o que vem depois. |
| Mudança durante a decisão | Dinâmico | Correntes e gelo se movem enquanto o robô decide. |
| Natureza dos elementos | Contínuo | Posição, profundidade, pressão e movimentos são grandezas contínuas. |
| Conhecimento do funcionamento | Desconhecido | Sabemos muito pouco sobre esse ambiente, então o robô precisa aprender. |

### Caso 3 — Comprar livros usados de IA na Internet

- **Agente analisado:** Comprar livros usados de IA na internet. O agente é um programa (softbot) comprador.
- **Objetivo e hipóteses:** Comprar uma lista de títulos. Hipóteses: orçamento fixo e vários sites de vendedores.
- **P — Medida de desempenho:** Livros da lista obtidos, preço total baixo, bom estado, entrega no prazo e nenhum golpe.
- **E — Ambiente:** Sites de venda, buscadores, vendedores, outros compradores, pagamento e transportadoras.
- **A — Atuadores:** Digitar buscas, clicar, comparar ofertas, adicionar ao carrinho, pagar e escrever ao vendedor.
- **S — Sensores:** Páginas dos anúncios (preço, estado, avaliações), e-mails e confirmações de compra.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | Não sei o estado real do livro, se o vendedor é confiável nem o preço em outros sites. |
| Número de agentes | Multiagente (competitivo) | Outros compradores disputam o mesmo exemplar e vendedores têm interesses próprios. |
| Previsibilidade | Estocástico | O livro pode sumir, o preço muda e o vendedor pode falhar na entrega. |
| Dependência entre decisões | Sequencial | O dinheiro gasto em uma compra limita as próximas. |
| Mudança durante a decisão | Dinâmico | Estoque e preços mudam enquanto o agente compara. |
| Natureza dos elementos | Discreto | Itens, preços, cliques e etapas da compra são valores separados. |
| Conhecimento do funcionamento | Conhecido | Sei o que acontece ao clicar em comprar. O que falta é observar tudo (são coisas diferentes). |

### Caso 4 — Jogar uma partida de tênis

- **Agente analisado:** Jogar uma partida de tênis. O agente é um jogador, em jogo de simples.
- **Objetivo e hipóteses:** Vencer a partida. Hipótese: partida oficial contra um adversário.
- **P — Medida de desempenho:** Pontos, games e sets ganhos, poucos erros e menos pontos perdidos para o adversário.
- **E — Ambiente:** Quadra, rede, bola, raquete, adversário e árbitro.
- **A — Atuadores:** Braços e raquete (saque e golpes), pernas para se deslocar.
- **S — Sensores:** Visão, audição, tato na raquete e propriocepção.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | Não sei para onde o adversário vai mandar a bola nem o efeito exato que ela leva. |
| Número de agentes | Multiagente (competitivo) | O ponto de um é o ponto perdido do outro. |
| Previsibilidade | Estocástico | Efeito, vento e as escolhas do adversário tornam o resultado incerto. |
| Dependência entre decisões | Sequencial | Cada golpe prepara o seguinte, e o cansaço e o placar pesam no resto do jogo. |
| Mudança durante a decisão | Dinâmico | A bola não espera. |
| Natureza dos elementos | Contínuo | Posição, velocidade e ângulos da bola são contínuos. |
| Conhecimento do funcionamento | Conhecido | Regras e física da bola são conhecidas. |

### Caso 5 — Praticar tênis contra uma parede

- **Agente analisado:** Praticar tênis contra a parede. O agente é o jogador treinando sozinho.
- **Objetivo e hipóteses:** Melhorar a técnica. Hipóteses: parede lisa, sem vento e bola em bom estado.
- **P — Medida de desempenho:** Rebatidas seguidas sem errar, precisão dos golpes e evolução da técnica.
- **E — Ambiente:** Parede, piso, bola e raquete.
- **A — Atuadores:** Braços e raquete, pernas para se posicionar.
- **S — Sensores:** Visão, audição (som da bola) e tato na raquete.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Completamente observável | Na hipótese adotada vejo a bola e a parede, que é tudo o que importa para decidir. |
| Número de agentes | Agente único | A parede não busca nenhum objetivo, só devolve a bola pela física. |
| Previsibilidade | Determinístico | Com parede lisa e sem vento, a volta da bola é previsível pela física. |
| Dependência entre decisões | Sequencial | Cada rebatida define a posição e o tempo da seguinte. |
| Mudança durante a decisão | Dinâmico | A bola continua se movendo enquanto decido. |
| Natureza dos elementos | Contínuo | Posições, velocidades e movimentos são contínuos. |
| Conhecimento do funcionamento | Conhecido | Sei como a bola quica e volta da parede. |

### Caso 6 — Realizar um salto de altura

- **Agente analisado:** Realizar um salto de altura. O agente é o atleta saltador.
- **Objetivo e hipóteses:** Passar o sarrafo. Hipótese: uma tentativa de salto, sem interferência de outros atletas.
- **P — Medida de desempenho:** Altura superada sem derrubar o sarrafo e pouco desperdício de tentativas.
- **E — Ambiente:** Pista de corrida, sarrafo, colchão de queda e o vento.
- **A — Atuadores:** Pernas (corrida e impulsão), braços, tronco e coluna para curvar o corpo.
- **S — Sensores:** Visão do sarrafo e da pista, equilíbrio, propriocepção e tato dos pés.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | Não vejo meu corpo no ar e não percebo bem o vento. |
| Número de agentes | Agente único | Na hipótese adotada ninguém interfere no meu salto. |
| Previsibilidade | Estocástico | Pequenas variações do corpo e do vento mudam o resultado. |
| Dependência entre decisões | Sequencial | Corrida, impulsão e passagem pelo sarrafo dependem uma da outra. |
| Mudança durante a decisão | Dinâmico | O corpo já está em movimento enquanto se decide. |
| Natureza dos elementos | Contínuo | Velocidade, ângulos e altura variam continuamente. |
| Conhecimento do funcionamento | Conhecido | As regras e a física do salto são conhecidas. |

### Caso 7 — Participar de um leilão de um item, realizando lances

- **Agente analisado:** Dar lances num leilão. O agente é um programa (ou pessoa) licitante.
- **Objetivo e hipóteses:** Ganhar o item pagando menos que seu valor para mim. Hipóteses: orçamento limitado e leilão com prazo.
- **P — Medida de desempenho:** Valor do item menos o preço pago (ganhar barato), sem estourar o limite.
- **E — Ambiente:** Plataforma do leilão, leiloeiro, item, outros licitantes e o relógio.
- **A — Atuadores:** Enviar lance, definir lance máximo e desistir.
- **S — Sensores:** Preço atual, histórico de lances, tempo restante e número de participantes.

| Propriedade | Classificação | Justificativa |
|---|---|---|
| Observabilidade | Parcialmente observável | Vejo os lances, mas não o limite que cada concorrente aceita pagar. |
| Número de agentes | Multiagente (competitivo) | Quanto mais eles pagam, pior fico. |
| Previsibilidade | Estocástico | Na prática não dá para prever os lances dos outros. (Pela definição estrita do livro, essa incerteza vinda só de outros agentes não contaria.) |
| Dependência entre decisões | Sequencial | Lances anteriores sobem o preço e consomem o orçamento. |
| Mudança durante a decisão | Dinâmico | Outros podem dar lance e o tempo corre enquanto penso. |
| Natureza dos elementos | Discreto | Lances são valores definidos e as ações são eventos separados. |
| Conhecimento do funcionamento | Conhecido | As regras do leilão são conhecidas. |

### Comparação final

1. **Tênis contra pessoa e contra a parede.** Contra uma pessoa o ambiente é multiagente e competitivo, parcialmente observável e estocástico, porque preciso adivinhar o que o adversário vai fazer. Contra a parede sou o único agente e o resultado é bem mais previsível, então dá para treinar técnica sem pensar em estratégia.
2. **Livros usados.** O agente não vê tudo: o estado real do livro, se o vendedor entrega, se outro comprador leva o exemplar antes e quanto custa em outros sites. Ele decide sem ter essas informações, por isso o ambiente é parcialmente observável e estocástico.
3. **Outros agentes no futebol e no leilão.** No futebol, os companheiros ajudam e os adversários atrapalham, e o que eu faço de melhor depende do que eles fazem. No leilão é pura competição: os lances dos outros definem o preço e se eu ganho ou não.

---

## Exercício 2.5

### Agente

- **Definição:** Qualquer coisa que percebe o ambiente por meio de sensores e age sobre ele por meio de atuadores.
- **Exemplo:** Um robô aspirador que usa sensores para achar sujeira e rodas e escovas para limpar.

### Função de agente

- **Definição:** Descrição matemática que associa cada sequência de percepções possível a uma ação. Diz o que o agente faz, mas não como.
- **Exemplo:** A tabela do mundo do aspirador, em que [A, Sujo] leva a Aspirar.

### Programa de agente

- **Definição:** É o código que implementa a função de agente numa máquina. Recebe só a percepção atual e, se precisar do histórico, tem que guardá-lo.
- **Exemplo:** O programa do aspirador reativo: se está sujo, aspira; senão vai para o outro quadrado.

### Racionalidade

- **Definição:** Escolher a ação que se espera que maximize a medida de desempenho, dado o que o agente percebeu e sabe. Não é perfeição nem adivinhar o futuro.
- **Exemplo:** Olhar para os dois lados antes de atravessar a rua é racional, mesmo que algo caia do céu.

### Autonomia

- **Definição:** Quando o agente usa o que aprende com as próprias percepções, e não só o conhecimento que o projetista colocou nele.
- **Exemplo:** Um aspirador que aprende em que horários a sujeira aparece mais. O besouro de esterco, que repete o plano mesmo sem a bola, não tem autonomia.

### Agente reativo

- **Definição:** Escolhe a ação só pela percepção atual, com regras do tipo condição-ação, sem lembrar do passado.
- **Exemplo:** Um carro que começa a frear quando a luz de freio do carro da frente acende.

### Agente baseado em modelo

- **Definição:** Mantém um estado interno atualizado com um modelo de como o mundo funciona, para lidar com o que não está vendo agora.
- **Exemplo:** Um táxi que lembra de um carro que saiu do campo de visão e está no ponto cego.

### Agente baseado em objetivos

- **Definição:** Escolhe ações pensando nas consequências, para chegar a uma situação desejada. Usa busca e planejamento.
- **Exemplo:** Um táxi que escolhe o caminho para chegar ao destino do passageiro.

### Agente baseado em utilidade

- **Definição:** Compara os estados por uma função de utilidade (grau de satisfação) e escolhe a ação de maior utilidade esperada. Ajuda quando os objetivos conflitam.
- **Exemplo:** Um táxi que equilibra tempo de viagem, segurança e custo ao escolher a rota.

### Agente com aprendizagem

- **Definição:** Melhora o próprio desempenho com a experiência. Tem elemento de desempenho, elemento de aprendizado, crítico e gerador de problemas.
- **Exemplo:** Um táxi que aprende que frear em pista molhada demora mais e ajusta a distância que mantém.

---

## Síntese com autômatos

Escolhi o Caso 7 (leilão), com o agente sendo o licitante.

- **Estados internos:** Observando (ainda não dei lance); Liderando (meu lance é o mais alto); Fora (desisti).
- **Percepções:** lance de outro dentro do meu limite; lance de outro acima do meu limite; nenhum lance novo.
- **Ações:** Dar lance; Desistir; Esperar (ação padrão quando não há novidade).
- **Regra 1:** Observando + lance de outro dentro do limite → Liderando, Dar lance.
- **Regra 2:** Liderando + lance de outro acima do limite → Fora, Desistir.

**Como o estado guarda o passado:** “Liderando” resume que eu já dei um lance e que ele é o mais alto, então não preciso reler toda a sequência de percepções. O estado carrega a parte do histórico que importa para decidir.

**Limitação:** com só três estados o agente não lembra quanto já gastou, quantos concorrentes existem nem como cada um costuma dar lance, e também não lida com probabilidades. Um autômato finito tão pequeno simplifica demais o leilão real.

---

## Referências

Material-base: Capítulo 2 — Agentes inteligentes, disponibilizado para a aula de 19/10/2026.

Referências adicionais consultadas: nenhuma além do capítulo.
