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
Creio que assim com eu, todos que estão de alguma forma iniciando seu estudado em data science ou mesmo estudando sozinhos, sabem o quão dificil é não ter aquele "parceiro(a)" nas horas de dúvidas, não é mesmo? Como também estou iniciando minha jornada neste novo mundo chamado <a href='https://www.kaggle.com' target="_blank" style="color: inherit">Kaggle</a>, decide então começar a documentar cada desafio em que participo, para que este post também possa ajudar a outras pessoas.
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
    * [Obtenção dos Dados](#definicao-do-problema)
    * [Exploração dos Dados](#definicao-do-problema)
    * [Preparação dos Dados](#definicao-do-problema)
    * [Modelagem](#definicao-do-problema)
    * [Avaliação](#definicao-do-problema)
* [Downloads dos Dados](#download-dados)
* [Lendo os Dados](#lendo-os-dados)
* [Entendendo os Dados](#entendendo-os-dados)



<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>


# <span style="color:#36648B">Quickly Start</span><br> <a name="introducao"></a>

### <span style="color:#36648B">O Que é o Kaggle?</span><br> <a name="o-que-e-kaggle"></a>
<p>
O kaggle é uma das plataformas mais conhecidas para competições de Data Scence, O kaggle foi fundado no ano de 2010 por <a href='https://en.wikipedia.org/wiki/Anthony_Goldbloom' target="_blank" style="color: inherit">Anthony Goldbloom</a>, e foi adquirida pelo Google em 2017.
</p>

### <span style="color:#36648B">Como Funciona o Kaggle?</span><br> <a name="como-funciona-o-kaggle"></a>
<p>
De uma forma bem resumida, o Kaggle hospeda competições públicas, privadas e acadêmicas em sua plataforma, existem compatições patrocinadas que oferencem um prêmio em dinheiro pela melhor solução e também existe as competições de aprendizagem que são muitas vezes disponibilizadas pelo próprio Kaggle.
<br>
A plataforma também disponibiliza dados de assuntos diversos (os famosos datasets) além de possuir fóruns e uma comunidade disposta a trocar conhecimentos.
</p>

### <span style="color:#36648B">Como Funciona os Desafios?</span><br> <a name="como-funciona-os-desafios"></a>
<p>
Para o caso do Titanic é bem simples, basicamente temos os datasets de Treino, Teste e a Gender_submission. O que precisamos fazer é criar um modelo que preveja se um determinado tripulante do RMS Titanic sobreviveu a colisão com o iceberg no dia 14 abril de 1912.
Com o modelo ja criado devemos prever nossa base de <b>Teste</b>, e assim criar a nossa submission na qual faremos o upload para o kaggle que avaliará a previsão.
</p>

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
O naufrágio do RMS Titanic aconteceu no dia 14 de abril de 1912 quando colidiu as 23h40 contra um iceberg nas águas do Oceano Atlântico. Naquela noite, 1.514 pessoas morreram, embora aqueles que escaparam com vida tiveram uma boa dose de sorte, havia determinados grupos de pessoas que eram mais propensos a escaparem com vida que outros. Exemplo, mulheres, crianças e passageiros das


segundo a Junta Comercial Britânica. Após a tragédia, 

</p>

#### Objetivo
<p>
O objetivo deste desafio de Data Science é utilizar os dados disponíveis para medir a probabilidade de sobrevivência dos passageiros do RMS Titanic.
<br>
</p>









# <span style="color:#36648B">Downloads dos Dados</span><br> <a name="download-dados"></a>
<p>
A primeira coisa que precisamos fazer é o download dos datasets, para isso você tem duas opções, Fazer o download na própria plataforma do kaggle ou utilizar da API do Kaggle. No meu caso estou usando a API, mas isso fica a seu critério. (caso queria conhecer sobre a API acesse o link abaixo)
<br>
<br>
<a href='https://www.kaggle.com/docs/api' target='_blank'>Documentação Kaggle API</a>
<br>
<br>
As bibliotecas que vou utiliza, são: Pandas e Nunmpy, pretendo fazer um artigo introdutório sobre eles em breve, mas por enquanto vou deixar o link das documentações aqui embaixo.
<br>
<br>
<a href='https://pandas.pydata.org/docs/' target='_blank'>Documentação Pandas</a>
<br>
<a href='https://numpy.org/doc/' target='_blank'>Documentação Numpy</a>
<br>
<br>
</p>

# <span style="color:#36648B">Lendo os Dados</span><br> <a name="lendo-os-dados"></a>
<p>Importando as bibliotecas</p>

```python
# Loading packges
import pandas as pd
import numpy as np
```
<p>Lendo os arquivo de treino e teste</p>

```python
# Loading files
train = pd.read_csv('./inputs/train.csv')
test = pd.read_csv('./inputs/test.csv')
```

```python
train.head()
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\treino-5registros.png"/>      
</div>
```python
test.head()
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\teste-5registros.png"/>      
</div>

# <span style="color:#36648B">Entendendo os Dados</span><br> <a name="entendendo-os-dados"></a>
<p>
A primeira coisa que precisamos entender é o que cada coluna representa, então para deixa mais claro, segue essa tabela para 
</p>