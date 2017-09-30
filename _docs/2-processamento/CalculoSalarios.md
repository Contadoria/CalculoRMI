---
title: CalculoSalarios
category: Processamento
order: 0
---

##### **Concomitancia** `C:C`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(OFFSET(D1;0;0;COUNTA(Salarios!A6:A);1))=1;"Concomitância";MMULT(IF(ISNUMBER(OFFSET(Salarios!D6;0;0;COUNTA(Salarios!A6:A);COLUMNS(Salarios!6:6)-3));SIGN(OFFSET(Salarios!D6;0;0;COUNTA(Salarios!A6:A);COLUMNS(Salarios!6:6)-3));0);TRANSPOSE(SIGN(COLUMN(OFFSET(Salarios!D6;0;0;1;COLUMNS(Salarios!6:6)-3)))))>=2)){% endhighlight %}


~~~
0.###############
~~~


> Fórmula Matriz (ArrayFormula) identifica por "verdadeiro" ou "falso" as linhas onde há concomitância de valores a título de salários, selecionando a partir da planilha "salários".

* * *

##### **ResultadoSalariosFornecidos** `B:B`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(OFFSET(D1;0;0;COUNTA(Salarios!A6:A);1))=1;"Soma";MMULT(IF(ISNUMBER(OFFSET(D1;0;0;COUNTA(Salarios!A6:A);COLUMNS(D1:1)));OFFSET(D1;0;0;COUNTA(Salarios!A6:A);COLUMNS(D1:1));0);TRANSPOSE(SIGN(COLUMN(OFFSET(D1;0;0;1;COLUMNS(D1:1)))))))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Fórmula Matriz (ArrayFormula) identifica soma dos s.c. concomitantes no mês/ano de competência, selecionando a partir da planilha "salários".