# Sistema especialista Classificador de spam

Lê uma mensagem, diz se é spam e recomenda o que fazer com ela.

Trabalho de nteligência Artificial, Linguagens Formais e Automatos, Profa. Kadidja Valéria.

## Como funciona

Uma árvore de decisão treinada em mensagens fictícias classifica o texto como spam ou
não. Essa resposta vira um fato e entra em quatro regras escritas à mão, junto com outro
fato que o usuário informa: se conhece o remetente.

É a combinação dos dois que define a recomendação. Mensagem suspeita de um desconhecido vai
para o lixo; a mesma mensagem vinda de um contato manda confirmar por outro canal, porque a
conta dele pode ter sido invadida.

## Como rodar

Abra o notebook no Google Colab `Sistema_especialista_spam.ipynb` e execute de cima para baixo. As bibliotecas já vêm
instaladas lá.

