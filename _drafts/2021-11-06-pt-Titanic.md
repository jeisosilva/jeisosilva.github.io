---
layout: post
title: "Desafio do Kaggle - Titanic"
date: 2021-11-02
lang: pt
ref: Kaggle
author: jeiso
description: Quem vive ou morre, será que conseguimos preversss?
image: images\desafio-kaggle-titanic\img\titanic.jpg
---

<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\titanic.jpg"/>      
    <!--
    <i>Photo by <u><a href='#' target="_blank" https://www.kaggle.com">Brett Jordan</a></u> on <u><a href='https://unsplash.com' target="_blank" style="color: inherit">Unsplash</a></u></i>
    -->
</div>

> Quando algo é importante o suficiente, você realiza, mesmo que as chances não estejam a seu favor. – Elon Musk

## <span style="color:#36648B">Prefácio</span><br> <a name="prefacio"></a>
<p>
Creio que assim com eu, todos que estão de alguma forma iniciando seu estudado em data science ou mesmo estudando sozinhos, sabem o quão dificil é não ter aquele "parceiro(a)" nas horas de dúvidas, não é mesmo? Como também estou iniciando minha jornada neste novo mundo chamado <a href='https://www.kaggle.com' target="_blank">Kaggle</a>, decide então começar a documentar cada desafio em que participo, para que este post também possa ajudar a outras pessoas.
<br>
Nosso 1° desafio será ninguém mais e ninguém menos que o tão famoso <b>Desafio do Titanic</b>, o desafio recomendado para nós, os iniciantes :)
<br>
Então sem mais de longas, vamos começar!
</p>

## <span style="color:#36648B"> Índice</span>

* [Quickly Start](#introducao)
    * [O Que é o Kaggle?](#o-que-e-kaggle)
    * [Como Funciona o Kaggle?](#como-funciona-o-kaggle)
    * [Como Funciona os Desafios?](#como-funciona-os-desafios)
* [Workflow](#workflow)
    * [Definição do Problema](#definicao-do-problema)
    * [Obtenção dos Dados](#obtencao-dos-dados)
    * [Exploração dos Dados](#exploracao-dos-dados)
    * [Preparação dos Dados](#preparacao-dos-dados)
    * [Modelagem](#modelagem)
    * [Avaliação](#avaliacao)


<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Quickly Start</span><br> <a name="introducao"></a>

### <span style="color:#36648B">O Que é o Kaggle?</span><br> <a name="o-que-e-kaggle"></a>
<p>
O kaggle é uma das plataformas mais conhecidas para competições de Data Scence, O kaggle foi fundado no ano de 2010 por <a href='https://en.wikipedia.org/wiki/Anthony_Goldbloom' target="_blank" >Anthony Goldbloom</a>, e foi adquirida pelo Google em 2017.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

### <span style="color:#36648B">Como Funciona o Kaggle?</span><br> <a name="como-funciona-o-kaggle"></a>
<p>
De uma forma bem resumida, o Kaggle hospeda competições públicas, privadas e acadêmicas em sua plataforma, existem compatições patrocinadas que oferencem um prêmio em dinheiro pela melhor solução e também existe as competições de aprendizagem que são muitas vezes disponibilizadas pelo próprio Kaggle.
<br>
A plataforma também disponibiliza dados de assuntos diversos (os famosos datasets) além de possuir fóruns e uma comunidade disposta a trocar conhecimentos.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

### <span style="color:#36648B">Como Funciona os Desafios?</span><br> <a name="como-funciona-os-desafios"></a>
<p>
Para o caso do Titanic é bem simples, basicamente temos os datasets de Treino, Teste e a Gender_submission. O que precisamos fazer é criar um modelo que preveja se um determinado tripulante do RMS Titanic sobreviveu a colisão com o iceberg no dia 14 abril de 1912.
Com o modelo ja criado devemos prever nossa base de <b>Teste</b>, e assim criar a nossa submission na qual faremos o upload para o kaggle que avaliará a previsão.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Workflow</span><br> <a name="workflow"></a>
<p>
Todo projeto de Data Science precisa seguir um fluxo de trabalho com algumas etapas essenciais para se fazer uma boa análise.

Ao iniciar um novo projeto de data Science, se a primeira coisa que vocês faz é criar um notebook, carregar os arquivos em memória e já sair escrevendo código, em algum momento durante sua análise você vai se perder.

Para este Projeto do Titanic, as etapas que vamos seguir são as seguintes:
</p>
#### 1. Definição do Problema
#### 2. Obtenção dos Dados
#### 3. Exploração dos Dados
#### 4. Preparação dos Dados
#### 5. Modelagem
#### 6. Avaliação
<p>
Seguindo estas etapas, dividimos o problema em etapas e deixamos a análise mais estruturada.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

### <span style="color:#36648B">Definição do Problema</span><br> <a name="definicao-do-problema"></a>
<p>
Particularmente eu sempre gosto de <b>gasta um bom tempo no começo para entender</b> sobre o problema (ou negócio) que estamos trabalhando. No nosso caso, entender o problema
também incluí fazer pesquisas sobre a historia do Titanic.
</p>

<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\titanic_caracteristicas.gif"/>      
</div>
<p>
O RMS Titanic começo a ser construido em março de 1912, foi a segunda embarcação da <b>Classe Olimpic</b> e levou cerca de de 2 anos até sua conclusão. Com 269 metros de comprimento
28 metros de largura e 53 metros de altura, o titanic operava com uma tripulação de 892 pessoas e era capaz de transportar 2.435 passageiros espalhados em três classes. Além disso, a embarcaçào também carregava correio e por isso recebeu o prefixo <b>Royal Mail Ship</b> (RMS). (Isso fica como uma curiosidade, mas confesso que eu também não sabia dessa.)
<br>
<br>
Este incrível navio, foi pensado para ser <b>a mais segura e luxuosa embarcação da época</b>, ganhando a reputação de ser <b>"inafundável"</b>.
<br>
<br>
O naufrágio do RMS Titanic aconteceu no dia 14 de abril de 1912 quando colidiu as 23h40 contra um iceberg nas águas do Oceano Atlântico. Naquela noite, 1.514 pessoas morreram, embora aqueles que escaparam com vida tiveram uma boa dose de sorte, havia determinados grupos de pessoas que eram mais propensos a escaparem com vida que outros. Exemplo, mulheres, crianças e passageiros da 1ª Classe. Este comportamente pode ser observado nos dados que vamos coletar mais adiante.
<br>
A descrição completa desta competição, assim como os dados que vamos usar podem ser encontrado na página do kaggle  <a href='https://www.kaggle.com/c/titanic/overview' target="_blank">Titanic: Machine Learning from Disaster</a>.
</p>

#### Objetivo

* Utilizar os dados disponíveis para medir a probabilidade de sobrevivência dos passageiros do RMS Titanic. 
* Análisar quais variáveis tiveram maior influência na probablidade de sobrevivência.

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Obtenção dos Dados</span><br> <a name="obtencao-dos-dados"></a>
<p>
A primeira coisa que precisamos fazer é o download dos datasets, para isso você tem duas opções: 
</p>
* Fazer o download  através do página do Kaggle <a href='https://www.kaggle.com/c/titanic/overview' target="_blank">Titanic: Machine Learning from Disaster</a> 
<br>
<br>
ou 
<br>
<br>
* Utilizar da API do Kaggle. 
<br>
No meu caso estarei usando a API, mas isso fica a seu critério. 
<br>
<br>
(Caso queria conhecer sobre a API acesse <a href='https://www.kaggle.com/docs/api' target='_blank'>Documentação Kaggle API</a>)
<p style="font-size:18px;color:gray">
Note: Para conseguir baixar os dados, é obrigatório fazer o cadastro no Kaggle.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Exploração dos Dados</span><br> <a name="exploracao-dos-dados"></a>

### <b>Dicionário de Dados</b>

* PassengerId: Número de identificação do passageiro
* Survived: Informa se o passageiro sobreviveu ao desastre
    * 0 = Não
    * 1 = Sim
* Pclass: Classe do bilhete
    * 1 = 1ª Classe
    * 2 = 2ª Classe
    * 3 = 3ª Classe
* Name: Nome do passageiro
* Sex: Sexo do passageiro
* Age: Idade do passageiro
* SibSp: Quantidade de cônjuges e irmãos a bordo
* Parch: Quantidade de pais e filhos a bordo
* Ticket: Número da passagem
* Fare: Preço da Passagem
* Cabin: Número da cabine do passageiro
* Embarked: Porto no qual o passageiro embarcou
    * C = Cherbourg
    * Q = Queenstown
    * S = Southampton

### <b>Importando as bibliotecas</b>
```python
# Loading packges
import pandas as pd
import numpy as np
```

### <b>Lendo os arquivos</b>
```python
# Loading files
train = pd.read_csv('./inputs/train.csv')
```

```python
train.head()
```

<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\treino-5registros.png"/>      
</div>

### <b>Distribuição estatística</b>
<p>
Aqui podemos ter um visão geral a respeito da distribuição de cada variável e sobre posisveis outliers e valores faltantes. Isso vai ser muito útil na próxima etapa, quando iremos trabalhar a limpeza dos dados e decidir se vamos excluir um registro que tenha um valor faltante ou preencheremos com a média/mediana, por exemplo.
</p>

```python
train.describe()
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\describe.png"/>      
</div>

```python 
train.hist(figsize=(10,8))
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\hist1.png"/>      
</div>

### <b>Grupos com mais chances de sobrevivência</b>
<p>
Esta é a hora de testar um hipótese que vimos na etapa de <u>Definição do Problema</u>, será que as mulheres e crianças tiveram de fato mais chances de sobrevivência?
<br>
<br>
Vamos aos plots.
</p>
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\distribuicao-sex.png"/>      
</div>
<br>
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\sobreviventes-sex.png"/>      
</div>
<br>
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\sobreviventes-classe.png"/>      
</div>
<br>
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\sobreviventes-embarque.png"/>      
</div>

Observando os gráficos acima, vemos que:
<br>
* Há muito mais homens que Mulheres a bordo.
* Mulheres tem muito mais chance de sobreviverem que os homens, 74% vs. 19%.
* Passageiros da 3ª Classe tem menos da metade de chance de escaparem do desastre que os passageiros que estão na 1ª Classe, cerca de 24% vs. 63%.
<br>
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\survived-age.png"/>      
</div>

<p>
Observando os gráficos acima, vemos que:
<br>
A distribuição das idades dos sobreviventes e mortos, vemos que há um pico no lado dos sobreviventes para crianças pequenas. O comportamento 
dos dois gráficos é bem parecido, mas esse detalhe é bem importante pois confirma a hipótese que crianças também tem maior chance de 
sobreviverem: “Crianças e mulheres primeiro”.
<br>
Por fim, vamos dar uma olhada no heatmap para entender como as variáveis estão correlacionadas, positiva ou negativamente.
</p>

```python
plt.figure(figsize=(16,9))
sns.heatmap(train.corr(), annot=True, fmt='.2f',square=True,cmap="coolwarm")
```

<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\heatmap.png"/>      
</div>

<p>
Depois de entender melhor sobre os dados nos quais estamos trabalhando, chegou a hora de fazer uma limpeza na casa, então pegue a vassoura e pá, e vamos lá.
</p>

### <b>Limpeza de Dados</b>
```python
# Verificando os tipos das variáveis
train.info() 
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\info.png"/>      
</div>

```python
# Verificando os dados faltantes
train.isna().sum()
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\isna.png"/>      
</div>
<p>
Agora que já sabemos os tipos e as quantidade de dados faltantes em cada variável, vamos começar tratar os dados.
<br>
<br>
Quando falamos de dados faltantes, vale lembrar que são dados com valores <b>NaN</b> ou <b>NULL</b>, um exemplo de um dados faltantes que não seriam detectados pelo método
acima, são dados com valores " " (string vázia). Por este motivo não devemos confiar plenamente em apenas um output e sim verificar o que realmente pode estar acontecendo com os dados.
<br>
<br>
Voltando ao tema de dados faltantes, para este caso, não vou tratar os dados da variável <b>Cabin</b>, pois a proporção de dados faltantes é bem significativa em relação a
quantidade total de registros, por este motivo não vou usar esta variável para os próximos passos. 
</p>

```python
# Apagando a coluna `Cabin`
train.drop(['Cabin'],axis=1, inplace=True)
```

Para a variávei <b>Age</b>  vou preencher os dados com a <u>média</u> de valores presentes da própria variável. (Sim, eu sei que a média em muitos casos não
é a melhor opção, mas creio que irá funcionar bem para estes casos). 


```python
# Preenchendo os valores `NaN` pela média de Idades
train.Age.fillna(train.Age.mean(),inplace=True)
```

Agora para a variável <b>Embarked</b>, como se trata de apenas 2 registros faltantes, vou eliminar estes dados da nossa base.

```python
# Eliminando os 2 registros `NaN`
train = train[~train.Embarked.isna()].reset_index(drop=True)
```

```python
# Verificando os dados faltantes
train.isna().sum()
```

<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\isna2.png"/>      
</div>

<p>
Pronto!, temos tudo que precisamos para começar a preparar os dados para o modelo.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Preparação dos Dados</span><br> <a name="preparacao-dos-dados"></a>
<p>
Para começar desta etapa devemos ter em mente uma coisa, modelos de Machine Learning só entendem números, ou seja, variáveis categóricas como por exempo, a
variável <b>Sex</b>, no qual temos os valores, <b>male</b> e <b>female</b>, vão geral um erro quando rodarmos o modelo.
<br>
Então o que devemos fazer? 
<br>
Basicamente devemos transformar os valores (String) em valores numéricos. Então, além da variável <b>Sex</b>, criaremos uma nova variável com o nome de <b>sex_binario</b>, e
para todos os valores da variável Sex que forem igual a "male", a nova variável receberá o valor de 0, e para cada "female" receberá o valor 1.
</p>

```python
train['sex_binario'] = train.Sex.map({'male':0,'female':1})
```
<p>
Agora aplicaremos este mesmo conceito para a variável <b>Embaked</b>.
</p>

```python
train['embarked_binario'] = train.Embarked.map({'S':1,'Q':2,'C':3})
```
### <b>Seleção das Features</b>
<p>

</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Modelagem</span><br> <a name="modelagem"></a>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Avaliação</span><br> <a name="avaliacao"></a>




