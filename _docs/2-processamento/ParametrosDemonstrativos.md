---
title: ParametrosDemonstrativos
category: Processamento
order: 3
---

##### **DadosObrigatoriosFaltantes** `A23`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(Especie);"";"Espécie#")& IF(ISNUMBER(DIB);"";"DIB#")&IF(ISNUMBER(Coeficiente);"";"Coeficiente#")
{% endhighlight %}


~~~
0.###############
~~~




* * *

##### **ModeloSumulaBeneficio** `D2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~




* * *

##### **TextoObservacoes** `A12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MostrarObservacoesAutomaticas="Sim";IF(ISTEXT(CONCATENATE(TextoObservacoesModificadores));"Modificadores:"&CHAR(10)&CONCATENATE(TextoObservacoesModificadores)&CHAR(10)&CHAR(10);"");"")&IF(ISTEXT(CONCATENATE(ObservacoesFinais));"Observações finais:"&CHAR(10)&ObservacoesFinais;""){% endhighlight %}


~~~
0.###############
~~~




* * *

##### **TextoObservacoesModificadores** `A2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=JOIN(CHAR(10);FILTER(OFFSET(ModificadoresObservacoes;5;0);OFFSET(ModificadoresObservacoes;5;0)<>"")){% endhighlight %}


~~~
0.###############
~~~




* * *

##### **TextoSumula** `D8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}="DADOS DO BENEFÍCIO:"&CHAR(10)& SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(CONCATENATE(ModeloSumulaBeneficio);"${Especie}";Especie&" - "&INDEX(ListaBeneficios!A:B;MATCH(Especie;ListaBeneficios!A:A;0);2);1);"${RMI}";RMI);"${DIB}";DIB){% endhighlight %}


~~~
0.###############
~~~


