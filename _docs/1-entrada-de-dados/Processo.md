---
title: Processo
category: Entrada
order: 0
---

##### **AtividadeSecundaria** `D16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_LIST Não,Sim
~~~

> Opção de cálculo do valor da renda mensal referente à atividade secundária (artigo 32 da Lei 8.213/91)

* * *

##### **Autor** `D6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Nome do autor

* * *

##### **BeneficioDeficiente** `K9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~

> Opção de cálculo para adequar à sistemática da Lei COmplementar nº 142/2013

* * *

##### **Citacao** `D9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Data da citação do Réu.

* * *

##### **Coeficiente** `K8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
~~~


> Coeficiente de cálculo da renda mensal inicial do benefício (percentual)


* * *

##### **DIB** `K7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}



~~~
DATE_IS_VALID_DATE 
~~~

> Data de início do benefício

* * *

##### **DataNascimento** `D13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/mm/yyyy
~~~


> Data de nascimento do segurado

* * *

##### **DenominadorAtividadeSecundaria** `D18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Tempo mínimo em anos necessário ao benefício (denominador) conforme artigo 32 da Lei nº 8.213/91

* * *

##### **Especie** `K6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE ListaBeneficios!A:A
~~~

> Código referente à espécie do benefício

* * *

##### **NB** `K5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Número do benefício

* * *

##### **NumeradorAtividadeSecundaria** `D17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Tempo de contribuição em anos referente à atividade secundária (numerador) conforme artigo 32 da Lei nº 8.213/91

* * *

##### **Processo** `D5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Número do processo

* * *

##### **Protocolo** `D8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Data do protocolo inicial do processo

* * *

##### **Reu** `D7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0
~~~


> Nome do Réu

* * *

##### **Sexo** `D12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_LIST Homem,Mulher
~~~

> Sexo do segurado


* * *

##### **TCAnos** `K12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
NUMBER_GREATER_THAN_OR_EQUAL_TO 0
~~~

> Número de anos referentes ao tempo de contribuição do segurado

* * *

##### **TCDias** `K14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
NUMBER_GREATER_THAN_OR_EQUAL_TO 0
~~~

> Número de dias referentes ao tempo de contribuição do segurado

* * *

##### **TCMeses** `K13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
NUMBER_GREATER_THAN_OR_EQUAL_TO 0
~~~

> Número de meses referentes ao tempo de contribuição do segurado