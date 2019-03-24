---
title: CalculoSalarios
category: Processamento
order: 0
---

##### **CompetenciaSalarios** `A:A`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Competência";CompetenciaIndices)){% endhighlight %}


~~~
mm/yyyy
~~~




* * *

##### **ResultadoSalariosFornecidos** `B:B`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(OFFSET(C1;0;0;COUNTA(Salarios!A6:A);1))=1;"Soma";MMULT(IF(ISNUMBER(OFFSET(C1;0;0;COUNTA(Salarios!A6:A);COLUMNS(C1:1)));OFFSET(C1;0;0;COUNTA(Salarios!A6:A);COLUMNS(C1:1));0);TRANSPOSE(SIGN(COLUMN(OFFSET(C1;0;0;1;COLUMNS(C1:1)))))))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


