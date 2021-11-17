---
layout: post
title: "#01 Titanic - Competição Kaggle"
date: 2021-11-12
lang: pt
ref: Kaggle
author: jeiso
description: Quem vive ou morre, será que conseguimos prever?
image: images\desafio-kaggle-titanic\img\titanic.jpg
---

<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\titanic.jpg"/>      
    <!--
    <i>Photo by <u><a href='#' target="_blank" https://www.kaggle.com">Brett Jordan</a></u> on <u><a href='https://unsplash.com' target="_blank" style="color: inherit">Unsplash</a></u></i>
    -->
</div>

> Quando algo é importante o suficiente, você realiza, mesmo que as chances não estejam a seu favor. – Elon Musk

## <span style="color:#36648B">Prefácio</span><a name="prefacio"></a>
<p>
Creio que assim com eu, todos que estão de alguma forma estão iniciando seus estudos em data science ou mesmo estudando sozinhos, sabem o quão dificil é não ter aquele "parceiro(a)" nas horas de dúvidas, não é mesmo? Como também estou iniciando minha jornada neste novo mundo chamado <a href='https://www.kaggle.com' target="_blank">Kaggle</a>, decide então começar a documentar cada desafio em que participo, para que este post também possa ajudar a outras pessoas.
<br>
Nosso 1° desafio será ninguém mais e ninguém menos que o tão famoso <b>Desafio do Titanic</b>, o desafio recomendado para nós, os iniciantes :)
<br>
Então sem mais de longas, vamos começar!
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

## <span style="color:#36648B"> Índice</span>

* [QuickStart](#introducao)
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
    * [Submission](#submissio)


<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">QuickStart</span><a name="introducao"></a>

### <span style="color:#36648B">O Que é o Kaggle?</span> <a name="o-que-e-kaggle"></a>
<p>
O kaggle é uma das plataformas mais conhecidas para competições de Data Scence, O kaggle foi fundado no ano de 2010 por <a href='https://en.wikipedia.org/wiki/Anthony_Goldbloom' target="_blank" >Anthony Goldbloom</a>, e foi adquirida pelo Google em 2017.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

### <span style="color:#36648B">Como Funciona o Kaggle?</span><br> <a name="como-funciona-o-kaggle"></a>
<p>
De uma forma bem resumida, o Kaggle hospeda competições públicas, privadas e acadêmicas em sua plataforma, existem competições patrocinadas que oferecem um prêmio em dinheiro pela melhor solução, também existe as competições de aprendizagem que são muitas vezes disponibilizadas pelo próprio Kaggle.
<br>
A plataforma também disponibiliza dados de assuntos diversos (os famosos datasets) além de possuir fóruns e uma comunidade disposta a trocar conhecimentos.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

### <span style="color:#36648B">Como Funciona os Desafios?</span><br> <a name="como-funciona-os-desafios"></a>
<p>
Para o caso do Titanic é bem simples, basicamente temos os datasets de Treino, Teste e a Gender_submission. O que precisamos fazer é criar um modelo que preveja se um determinado tripulante do RMS Titanic sobreviveu a colisão com o iceberg no dia 14 abril de 1912.
Com o modelo ja criado devemos prever nossa base de <b>Teste</b>, e assim criar a nossa submission na qual faremos o upload para o kaggle que avaliará a acurácia do modelo.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">WorkFlow</span> <a name="workflow"></a>
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
Seguindo estas etapas deixamos a análise mais estruturada.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

### <span style="color:#36648B">Definição do Problema</span><a name="definicao-do-problema"></a>
<p>
Particularmente eu sempre gosto de <b>dedicar um bom tempo no começo para entender</b> sobre o problema (ou negócio) que estamos trabalhando. No nosso caso, entender o problema
também inclui fazer pesquisas sobre a historia do Titanic.
</p>

<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\titanic_caracteristicas.gif"/>      
</div>
<p>
O RMS Titanic começou a ser construído em março de 1912, foi a segunda embarcação da <b>Classe Olimpic</b> e levou cerca de de 2 anos até sua conclusão. Com 269 metros de comprimento
28 metros de largura e 53 metros de altura, o titanic operava com uma tripulação de 892 pessoas e era capaz de transportar 2.435 passageiros espalhados em três classes. Além disso, a embarcação também carregava correio e por isso recebeu o prefixo <b>Royal Mail Ship</b> (RMS). (Isso fica como uma curiosidade, mas confesso que eu também não sabia dessa.)
<br>
<br>
Este incrível navio, foi pensado para ser <b>a mais segura e luxuosa embarcação da época</b>, ganhando a reputação de ser <b>"inafundável"</b>.
<br>
<br>
O naufrágio do RMS Titanic aconteceu no dia 14 de abril de 1912 quando colidiu as 23h40 contra um iceberg nas águas do Oceano Atlântico. Naquela noite, 1.514 pessoas morreram, embora aqueles que escaparam com vida tiveram uma boa dose de sorte, havia determinados grupos de pessoas que eram mais propensos a escaparem com vida que outros. Exemplo, mulheres, crianças e passageiros da 1ª Classe.
<br>
A descrição completa desta competição, assim como os dados que vamos usar podem ser encontrado na página do kaggle  <a href='https://www.kaggle.com/c/titanic/overview' target="_blank">Titanic: Machine Learning from Disaster</a>.
</p>

#### Objetivo

* Utilizar os dados disponíveis para medir a probabilidade de sobrevivência dos passageiros do RMS Titanic. 
* Analisar quais variáveis tiveram maior influência na probablidade de sobrevivência.

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Obtenção dos Dados</span> <a name="obtencao-dos-dados"></a>
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
No meu caso, vou usar o Kaggle API, mas isso fica a seu critério. 
<br>
<br>
(Caso queira conhecer sobre a API acesse <a href='https://www.kaggle.com/docs/api' target='_blank'>Documentação Kaggle API</a>)
<p style="font-size:18px;color:gray">
Note: Para conseguir baixar os dados, é obrigatório fazer o cadastro no Kaggle.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Exploração dos Dados</span> <a name="exploracao-dos-dados"></a>

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
Aqui podemos ter um visão geral a respeito da distribuição de cada variável e sobre possiveis outliers e valores faltantes. Isso vai ser muito útil na próxima etapa, quando iremos trabalhar a limpeza dos dados e decidir se vamos excluir um registro que tenha um valor faltante ou preencheremos com a média/mediana, por exemplo.
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
Esta é a hora de testar a hipótese que vimos na etapa de <u>Definição do Problema</u>, será que as mulheres e crianças tiveram de fato mais chances de sobrevivência?
<br>
<br>
Que venham os plots.
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
Observando o gráfico acima, vemos que:
<br>
O comportamento das duas linhas são bem parecidas, porém vemos que há um pico de crianças pequenas sobreviventes. Detalhe importante pois confirma a hipótese de que crianças também tem maiores chances de sobreviver. “Crianças e mulheres primeiro!”

<br>
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
Depois de entender melhor sobre os dados nos quais estamos trabalhando, chegou a hora de fazer uma limpeza na casa, então pegue a vassoura e pá, e vamos lá!
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
Quando falamos de dados faltantes, vale lembrar que não são penas dados com valores <b>NaN</b> ou <b>NULL</b>, um exemplo de um dados faltantes que não seriam detectados pelo método acima, são dados com valores " " (string vázia), ou mesmo dados digitados erroneamente. Por este motivo não devemos confiar plenamente em apenas um output e sim verificar o que realmente pode estar acontecendo com os dados.
<br>
<br>
Voltando ao tema de dados faltantes, para este caso, não vou tratar os dados da variável <b>Cabin</b>, pois a proporção de dados faltantes é bem significativa em relação a
quantidade total de registros, por este motivo não vou usar esta variável para os próximos passos. 
</p>

```python
# Apagando a coluna `Cabin`
train.drop(['Cabin'],axis=1, inplace=True)
```

Para a variável <b>Age</b>  vou preencher os dados com a <u>média</u> de valores presentes da própria variável. (Sim, eu sei que a média em muitos casos não
é a melhor opção, mas creio que irá funcionar bem para este caso). 


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
Pronto! Temos tudo que precisamos para começar a preparar os dados para o modelo.
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Preparação dos Dados</span> <a name="preparacao-dos-dados"></a>
<p>
Para começar essa etapa devemos ter em mente uma coisa, modelos de Machine Learning só entendem números, ou seja, variáveis categóricas como por exempo, a
variável <b>Sex</b>, no qual temos os valores, <b>male</b> e <b>female</b>, vão gerar um erro quando rodarmos o modelo.
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
Agora é hora de escolhermos as variáveis que vamos usar para treinar o modelo, como eu havia dito anteriormente, a etapa de <u>Análise Exploratória</u> é muito 
importante, pois foi através dela que comprovamos hipóteses e também nos ajudou a eliminar variáveis duplicadas/redundantes que não seria intesessante para o modelo.
</p>

```python
# Seleção das features
features = ['Survived','Pclass','Age','SibSp','Parch','sex_binario','embarked_binario']
base = train[features].copy()
```
```python
# 5 primeiros registros
base.head()
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\head-base.png"/>      
</div>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Modelagem</span><a name="modelagem"></a>
<p>
E finalmente estamos na etapa de modelagem. A primeira coisa que precisamos fazer é separar nosso <b>X</b> e <b>y</b>, sendo X o conjunto de features e y nossa variável target.
</p>

```python
# Pegando os conjutos de dados e nossa variável target
X = base.drop('Survived', axis=1)
y = base['Survived']
```
<p>
O modelo escolhido para este desafio foi o <u>RandomFlorest</u>, pois é um modelo que costuma ter uma boa performace nestes tipos de classificação. RandomFlorest é um modelo baseado em arvores de decisão que particularmente eu gosto bastante.
<br>
Normalmente quando você esta nesta etapa de modelagem, é bem comum testarmos mais de um tipo de modelo, e assim avaliarmos qual deles teve uma melhor performace, ou mesmo cogitar
um ensemble de modelos, mas este é um assunto para outro artigo.
</p>

```python
# Importando libs
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
```
<p>
Agora que já importamos as bibliotecas, vamos fazer a separação dos dados de treino e teste.
</p>

```python 
# Dividimos os dados em 50% para treino e 50% para teste
Xtrain, Xtest, ytrain, ytest = train_test_split(X,y, test_size=.5)
```

```python 
# Criando o modelo
mdl_rf = RandomForestClassifier(n_estimators=1000, n_jobs=6, random_state=0, class_weight='balanced')
mdl_rf.fit(Xtrain,ytrain)
```
<p>
Para o modelo usamos os seguintes parâmetros:
</p>
* n_estimators = 1000, que é o número de arvores dentro da floresta.
* n_jobs = 6, que é o número de jobs que rodará em paralelo.
* random_state = 0, para sempre gerar uma sequência única de dados pseudoaleatorios.
* class_weight = 'balanced', como temos classes desbalanceadas, isso é, mais exemplos de uma determinada label que de outra, este parâmentro basicamente
faz o balanço das classes para que o modelo não fique enviesado.

```python 
# Fazendo o predict
p = mdl_rf.predict(Xtest)
```

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Avaliação</span><a name="avaliacao"></a>

<p>
As métricas que vamos observar são:
</p>


* Acurácia (Accuracy/Taxa de Acerto) - É basicamente o número de acertos divido pelo número total de exemplos.
* Precisão (Precision) - É a porcentagem de todos os dados classificados como positivos, quantos são realmente positivos.



```python
# importando métricas
from sklearn.metrics import precision_score, accuracy_score
```

```python 
acc = round(accuracy_score(ytest, p),4)
precis = round(precision_score(ytest, p),4)

print(f'Accuracy: {acc} | Precision: {precis}')
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\metricas.png"/>      
</div>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>

# <span style="color:#36648B">Submission</span><br> <a name="submissio"></a>
<p>
Muito bem! chegamos na etapa final.
<br>
Depois de ter feito a análise exploratório e usando o conhecimento adquirido, fomos capazes de selecionar e tratar os dados a partir da base de treino (train.csv)
fornecida pelo Kaggle, depois criamos o 1° modelo para este desafio. 
<br>
Assim como no mundo real, coletamos, analisamos, tratamos, criamos o modelo e avaliamos. Chegou a hora de usar os dados do arquivo de test.csv, lembra dele?
Os passos a seguir são os mesmos que usamos quando tratamos os dados de treino, a única diferença é que não vamos ter a variável <b>Survived</b>, pois é o que queremos prever.
</p>

```python 
test = pd.read_csv('./inputs/test.csv')
test['sex_binario'] = test.Sex.map({'male':0,'female':1})
test['embarked_binario'] = test.Embarked.map({'S':1,'Q':2,'C':3})
test.Age.fillna(test.Age.mean(),inplace=True)
base_test = test[['Pclass','Age','SibSp','Parch','sex_binario','embarked_binario']].copy()
base_test.isna().sum()
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\test-isna.png"/>      
</div>

```python 
base_test.head()
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\test-head.png"/>      
</div>

```python
# Fazendo a predição na base test
p = mdl_rf.predict(base_test)
```
<p>
Agora é só criar o arquivo de submission e enviar para o Kaggle.
</p>

```python 
sub = pd.Series(p, index=test.PassengerId, name='Survived')
sub
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\submission.png"/>      
</div>

```python
# Salvando o arquivo no diretório `output`
sub.to_csv('./outputs/titanic_submission_artigo.csv', header=True)
```

<p>
Como dito no inicío deste artigo, a nossa submission pode ser enviar para o Kaggle de duas formas, 1ª entrando no desafio <a href='https://www.kaggle.com/c/titanic/overview' target="_blank">Titanic: Machine Learning from Disaster</a> e fazendo o upload do arquivo e 2ª Fazendo o upload do arquivo usando a Kaggle API, que é o que vamos fazer agora.
</p>

```python 
# upload submission
!kaggle competitions submit -c titanic -f outputs/titanic_submission_artigo.csv -m "Primeiro modelo artigo"
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\upload-sub.png"/>      
</div>

Por fim, podemos ver o <b>score</b> (acurácia) que obtemos com nosso primeiro modelo.

```python 
# Score submission
!kaggle competitions submissions -c titanic
```
<div align="center" style='color:gray' >
    <img  style="width:700px; margin:0px" src="../../../images\desafio-kaggle-titanic\img\score.png"/>      
</div>

<p>
Como podemos observar acima, nosso <b>score</b> foi abaixo do esperado quando submetemos ao Kaggle, e isso é comum. 
<br>
Comforme você for envoluindo como um cientista de dados, você aprenderá novos métodos e ferramentas para minimizar essa diferença. Embora nossa score tenha sido baixo, 
<b> chegar a quase 80% de acurácia no 1ª modelo é surpreendente </b> :)
</p>

<div align="center"> <strong>.&nbsp;&nbsp;.&nbsp;&nbsp;.</strong></div>
<p>
Obrigado por ler este artigo! Espero que ele possa ter te ajudado de alguma forma. Fique a vontade para acessar meu github e se conectar comigo via LinkeIdn, todos os links estão no rodapé deste artigo.
<br>
<br>
Até o nosso próximo desafio!
</p>

