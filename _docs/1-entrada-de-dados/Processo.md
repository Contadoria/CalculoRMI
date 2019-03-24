---
title: Processo
category: Entrada
order: 1
---

##### **AtividadeSecundaria** `D16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_LIST Não,Sim
~~~



* * *

##### **Autor** `D6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~




* * *

##### **BeneficioDeficiente** `K9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0
~~~


~~~
VALUE_IN_LIST Sim,Não
~~~



* * *

##### **Citacao** `D9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **Coeficiente** `K8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0%
~~~




* * *

##### **DIB** `K7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}



~~~
DATE_IS_VALID_DATE 
~~~



* * *

##### **DataNascimento** `D13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/mm/yyyy
~~~




* * *

##### **DenominadorAtividadeSecundaria** `D18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~




* * *

##### **Especie** `K6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE ListaBeneficios!A:A
~~~



* * *

##### **EspecieDescricao** `L6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IFERROR(INDEX(ListaBeneficios!A:B;MATCH(Especie;ListaBeneficios!A:A;0);2);""){% endhighlight %}


~~~
0.###############
~~~




* * *

##### **NB** `K5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~




* * *

##### **NumeradorAtividadeSecundaria** `D17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~




* * *

##### **Processo** `D5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~




* * *

##### **Protocolo** `D8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **Reu** `D7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0
~~~




* * *

##### **Sexo** `D12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_LIST Homem,Mulher
~~~



* * *

##### **TCAnos** `K16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
NUMBER_GREATER_THAN_OR_EQUAL_TO 0
~~~



* * *

##### **TCDias** `K18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
NUMBER_GREATER_THAN_OR_EQUAL_TO 0
~~~



* * *

##### **TCMeses** `K17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
NUMBER_GREATER_THAN_OR_EQUAL_TO 0
~~~

