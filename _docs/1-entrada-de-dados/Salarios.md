---
title: Salarios
category: Entrada
order: 4
---

##### **Concomitancia** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(OFFSET(E1;0;0;COUNTA(Salarios!A6:A);1))=1;"Concomitância";MMULT(IF(ISNUMBER(OFFSET(Salarios!E6;0;0;COUNTA(Salarios!A6:A);COLUMNS(Salarios!6:6)-4));SIGN(OFFSET(Salarios!E6;0;0;COUNTA(Salarios!A6:A);COLUMNS(Salarios!6:6)-4));0);TRANSPOSE(SIGN(COLUMN(OFFSET(Salarios!E6;0;0;1;COLUMNS(Salarios!6:6)-4)))))>=2)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **MarcoFinalAplicacaoArt32** `A4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **SalariosContribuicao** `E:E`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00
~~~


~~~
VALUE_IN_RANGE OpcoesAtividadesConcomitantes!A:A
~~~



* * *

##### **ValorAtividadeSecundaria** `A2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00_);[Red](#,##0.00)
~~~


