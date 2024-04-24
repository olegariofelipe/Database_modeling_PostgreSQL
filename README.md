<p align="center">
  <img src=https://github.com/olegariofelipe/Database_modeling_PostgreSQL/assets/112784578/f13f8b25-ff33-4f0f-884b-9d98d966b4a1
    width=200 heigth=200
</p>

# Modelagem Banco de Dados Relacional

Este é um projeto de cunho educacional, o mesmo foi proposto durante a trilha de Dados do programa Desenvolve 2024.

## Contextualização

Este projeto tem como objetivo, a elaboração de um banco de dados relacional que reflita os processos de ***vendas***, ***gerenciamento de estoque*** e ***sistema de pontuação de clientes*** para uma empresa do setor de cosméticos e bem-estar chamada **LuminaCos** (nome meramente ilustrativo), a qual possui diversas franquias distribuídas no território nacional. Uma nova franquia será aberta, e necessita de um sistema para armazenamento de dados e gerenciamento de processos. Para tal, foram construídos ao longo deste projeto, os modelos *conceitual*, *lógico* e *físico* do banco de dados relacional.

## Entendendo o fluxo de processos da LuminaCos

Os produtos da LuminaCos são distribuídos as suas franquias através de Centros de Distribuição (CD), após recebimentos (entrega) das mercadorias, as mesmas devem ser registrados em estoque no sistema interno através de entrada, para isso é utilizado o documento de entrega (nota fiscal ou semelhante), que descreve os produtos que foram entregues entre outras informações. Após registro, o estoque é atualizado com os itens entregues.
<br>
No que diz respeito aos processos de compra e pontuação, ambos os processos precisam estar vinculados a um cliente, sendo assim, os clientes devem ser registrados na base de dados com as informações necessárias. Como dito anteriormente, toda compra deve estar vinculada a um cliente e a pelo menos um produto, ao finalizar uma compra, uma pontuação é gerada, podendo esta ser utilizada posteriormente para descontos em compras futuras, dentro de um prazo de validade pré-estabelecido. Ao fininalizar a compra, também são atualizadas as informações de estoque, diminuindo a quantidade dos produtos que foram vendidos.
<br>

## Modelo Conceitual 
Após análise do fluxo dos processos, é possível identificar as entidades e atributos necessários para a modelagem do banco de dados.
Abaixo você encontra o **modelo conceitual**, que representa as abstrações do nosso modelo de banco de dados, representando as entidades, atributos e relacionamentos.<br>
<br>
![Modelo Conceitual](https://github.com/olegariofelipe/Modelagem_BD_Relacional/assets/112784578/39b07b09-0908-41a1-9b8f-fcb0a05ff959)
<br>
Por se tratar de um projeto fictício, todos os atributos acima foram escolhidos visando atender as necessidades de negócio desse contexto, para uma aplicação real, é recomendado uma análise mais aprofundada das necessidades e regras de negócio.
Abaixo você pode encontrar uma breve descrição das entidades e alguns atributos.

## Descrição de Entidades
Nessa etapa, é possível entender um pouco melhor cada entidade como elas se relacionam.<br>

* __CENTRO_DISTRIBUICAO__: <br>
Descreve o Centro de Distribução (CD) responsável realizar a entrega de produtos, estará diretamente relacionada as entradas de produtos.<br>
    
* __ENTRADA__: <br>
Descreve a entrada de produtos, sendo a parte identificadora da entrada, contendo as informações da entrega, como numero do documento de entrega (nota fiscal ou semelhante), data, CD e valor total da entrada. Toda entrada deve estar vinculada a um centro de distribuição.

* __ITEM_ENTRADA__: <br>
Esta entidade descreve separadamente cada item listado em uma determinada entrada, sendo assim, cada ocorrência deve obrigatoriamente estar vinculado a uma entrada e um produto.

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
Descreve as pontuações vinculadas a cada cliente a partir de suas respectivas compras, sendo assim a pontuação está vinculada tanto ao cliente, quanto a compra que gerou essa pontuação.
Também registra o tipo de movimentação realizada sobre os pontos, tendo em vista que os pontos podem ser gerados e descontados em outras compras, bem como a data de movimentação de cada pontuação.

* __ESTOQUE__:<br>
Descreve o estoque, listando os produtos em estoque e suas respectivas quantidades, sendo assim, deve estar relacionado a produtos.

## Modelo Lógico
A partir do modelo conceitual, foi gerado o __modelo Lógico__, onde as entidade são representadas como tabelas e os atributos como campos. Seguindo algumas regras de normalização, é possível notar na imagem abaixo, que os atributos compostos do modelo conceitual foram convertidos em tabelas separadas, isso foi feito afim de evitar muitos campos dentro de uma mesma tabela.<br>
<br>
![Modelo Lógico](https://github.com/olegariofelipe/Modelagem_BD_Relacional/assets/112784578/c937be9a-5019-4628-9c87-046021ac1d97)
<br>
## Modelo Físico
Por fim, abaixo encontra-se o __modelo físico__, no qual são apresentados os tipos de dados para cada coluna, as relações entre tabelas, bem como as chaves primárias e estrangeiras de cada tabela.<br>
<br>
![Modelo Físico](https://github.com/olegariofelipe/Modelagem_BD_Relacional/assets/112784578/1ff1b2a3-d1ff-4986-8f11-f77b9cc1080d)
<br>

## Ferramentas utilizadas:
 
 * [BrModel](http://www.sis4.com/brModelo/#google_vignette): Desenvolvimento dos modelos conceitual e lógico.
 * [SQL Power Architect](https://dbmstools.com/tools/sql-power-architect): Desenvolvimento do modelo físico.

## Autor:
Felipe Olegario dos Santos<br><br>
[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/olegariofelipe/)



