---
title: Modificadores2
category: Entrada
order: 3
---

##### **CompetenciaModificadores** `C:C`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(CompetenciaIndices)=1;"Competência";CompetenciaIndices)){% endhighlight %}


~~~
mm/yyyy
0.###############
~~~


> Matriz correspondente aos meses em que poderão ser lançados modificadores diversos

* * *

##### **ModificadoresIndiceMensalAtualizacao** `F:F`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00000000;(#,##0.00000000)[Red];-
~~~


> Modificadores dos índices mensais de atualização a serem considerados, inserção manual
Modificação dos índices de atualização a serem aplicados aos s.c., inserção manual.

* * *

##### **ModificadoresObservacoes** `I:I`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.00%
0.###############
~~~


> Campo para inserção de observações
Inserção de observações vinculadas aos modificadores.

* * *

##### **ModificadoresPiso** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificadores dos pisos a serem considerados, inserção manual
Modifica o piso salarial a ser considerado na competência, inserção manual.

* * *

##### **ModificadoresSalarios** `G:G`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificadores dos salários de contribuição a serem considerados, inserção manual
Modificação do s.c. relativo à competência, inserção manual.


* * *

##### **ModificadoresTeto** `E:E`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Modificadores dos tetos a serem considerados, inserção manual
Modificação do teto previdenciário relativo à competência, inserção manual.

* * *

##### **ModificadoresUsarPiso** `H:H`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


> Opção para preenchimento automático com base no valor do piso, inserção manual