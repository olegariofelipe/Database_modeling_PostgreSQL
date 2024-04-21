<p align="center">
  <img src=https://github.com/olegariofelipe/Database_modeling_PostgreSQL/assets/112784578/f13f8b25-ff33-4f0f-884b-9d98d966b4a1
    width=200 heigth=200
</p>

# Modelagem Banco de Dados Relacional

Este é um projeto de cunho educacional, o mesmo foi proposto durante a trilha de Dados do programa Desenvolve 2024.

## Contextualização

Este projeto tem como objetivo, a elaboração de um banco de dados que reflita os processos de ***vendas***, ***gerenciamento de estoque*** e ***sistema de pontuação de clientes*** para uma empresa do setor de cosméticos e bem-estar chamada **LuminaCos** (nome meramente ilustrativo), a qual possui diversas franquias distribuídas no território nacional, sendo que uma nova franquia será aberta, e necessita de um sistema para armazenamento de dados e gerenciamento de processos. Para tal, foram construídos os modelos *conceitual*, *lógico* e *físico* do banco de dados relacional, buscando atender a parte de armazenamento dos dados.

## Entendendo o fluxo de trabalho da LuminaCos

Os produtos da LuminaCos são distribuídos as suas franquias através de Centros de Distribuição (CD), após recebimentos (entrega) das mercadorias, as mesmas devem ser registrados em estoque no sistema interno através de entrada, para isso é utilizado o documento de entrega, que descreve os produtos que foram entregues, seus valores unitários e quantidades, bem como a data da entrega e CD que realizou a entrega, após registro, o estoque é atualizado com os produtos e suas respectivas quantidades.
<br>
No que diz respeito aos processos de compra e pontuação, clientes devem serem registrados na base de dados, fornecendo informações como nome, cpf, data de nascimento, sexo, telefone, endereço e e-mail. Toda compra deve obrigatoriamente estar vinculada a um cliente e a pelo menos um produto, ao finalizar uma compra, uma pontuação é gerada, podendo esta ser utilizada para descontos em compras futuras, dentro de um prazo de validade pré-estabelecido. Ao fininalizar a compra, também são atualizadas as informações de estoque, diminuindo a quantidade dos produtos que foram vendidos.

## Modelo Conceitual 
Após análise do fluxo de trabalho, e obtenção de algumas informações adicionais, foi elaborada o modelo conceitual abaixo, descrevendo as entidades e relacionamentos entre elas. <br><br>
[Colocar Imagem Aqui!]

## Descrição de Entidades
Nessa etapa, é possível entender um pouco melhor cada entidade de seus atributos.<br>

* __CENTRO_DISTRIBUICAO__: <br>
Descreve o Centro de Distribução (CD), estará diretamente relacionada as entradas de produtos.<br>
    
* __ENTRADA__: <br>
Descreve a entrada de produtos, sendo a parte identificadora da entrada, contendo as informações da entrega, como numero do documento de entrega, data, CD e valor total da entrada. Toda entrada deve estar vinculada a um centro de distribuição.

* __ITEM_ENTRADA__: <br>
Esta entidade descreve separadamente cada item listado em uma determinada entrada, sendo assim, deve obrigatoriamente estar vinculado a uma entrada e um produto.

* __PRODUTO__:<br>
Descreve os produtos, sendo que cada produto deve estar vinculado a uma categoria.

* __CATEGORIA__:<br>
Descreve as categorias as quais os produtos serão vinculados. É separada em **grupo** e **subgrupo**, sendo o grupo uma caracteristica mais geral e o subgrupo uma caracteristica mais especifica.<br>
__Exemplo__: <br>
_Grupo_ -> Perfumaria<br>
_Subgrupo_ -> Perfumaria Feminina, Perfumaria Masculina, Perfumaria Infantil

* __CLIENTE__:<br>
Descreve os clientes, que serão vinculados as compras e também as pontuações.

* __COMPRA__:<br>
Descreve as compras realizadas pelos clientes, sendo assim, a mesma deve estar vinculada a um cliente e também as pontuaçãos, uma vez que a compra pode gerar uma pontuação. É o descritivo mais geral do processo, possuindo informações como cliente que realizou a compra, data, valor total e desconto (se aplicável).

* __ITEM_COMPRA__:<br>
Descreve separadamente cada item listado em uma determinada compra, sendo assim, deve obrigatoriamente estar vinculado a uma compra e um produto.

* __PONTUACAO__:<br>
Descreve as pontuações vinculadas a cada cliente a partir de suas respectivas compras, sendo assim a pontuação está vinculada tanto a cliente quanto a compra para conseguir estabelecer essa relação entre as duas.
Também registra o tipo de movimentação realizada sobre os pontos, tendo em vista que os pontos podem ser gerados e descontados em outras compras, bem como a data de movimentação de cada pontuação.

* __ESTOQUE__:<br>
Descreve o estoque, listando os produtos em estoque e suas respectivas quantidades, sendo assim, deve estar relacionado a produtos.

## Modelo Lógico
A partir do modelo conceitual, foi gerado o modelo Lógico, onde as entidades passam a ser tabelas e os atributos passam a ser campos. É possível nota na imagem abaixo que os adritubos compostos do modelo conceitual foram convertidos em tabelas, isso foi feito afim de evitar muitos campos dentro de uma mesma tabela.
[Colocar imagem aqui!]

## Modelo Físico
Por fim, temos o modelo Físico, onde é demostrado os tipos de dados.
[Colocar Imagem Aqui!]

## Ferramentas utilizadas:


## Autor:
[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/olegariofelipe/)



