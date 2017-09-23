---
title: Salarios
category: Entrada
order: 3
---

##### **MarcoFinalAplicacaoArt32** `A4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}

+ **Formato**:
~~~
dd/MM/yyyy
~~~


> Indica data limite para apuração de atividade secundária nos termos do art. 32, da Lei nº 8.213/91 (fim da tabela de interstício)

* * *

##### **SalariosContribuicao** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}

+ **Formato**:
~~~
0.###############
dd/MM/yyyy
#,##0.00
#,##0.00;(#,##0.00)
~~~

+ **Regra de validação**:
~~~
VALUE_IN_RANGE OpcoesAtividadesConcomitantes!A:A
~~~



* * *

##### **ValorAtividadeSecundaria** `A2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}

+ **Formato**:
~~~
#,##0.00_);[Red](#,##0.00)
~~~


> Indicação do valor apurado no cálculo da atividade secundária, nos termos do art. 32, da Lei nº 8.213/91.
