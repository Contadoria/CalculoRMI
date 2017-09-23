---
title: ParametrosDemonstrativos
category: Processamento
order: 4
---

##### **DadosObrigatoriosFaltantes** `A23`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(ISNUMBER(Especie);"";"Espécie#")& IF(ISNUMBER(DIB);"";"DIB#")&IF(ISNUMBER(Coeficiente);"";"Coeficiente#")
{% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Indica os dados obrigatórios não preenchidos.

* * *

##### **ModeloSumulaBeneficio** `D2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}

+ **Formato**:
~~~
0.###############
~~~


> Indica os dados do benefício que devem constar da Súmula.

* * *

##### **TextoObservacoes** `A12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(MostrarObservacoesAutomaticas="Sim";IF(ISTEXT(CONCATENATE(TextoObservacoesModificadores));"Modificadores:"&CHAR(10)&CONCATENATE(TextoObservacoesModificadores)&CHAR(10)&CHAR(10);"");"")&IF(ISTEXT(CONCATENATE(ObservacoesFinais));"Observações finais:"&CHAR(10)&ObservacoesFinais;""){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Extrai o texto das observações inseridas na planilha, caso ativada a  opção "MostrarObservacoesAutomaticas"

* * *

##### **TextoObservacoesModificadores** `A2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=JOIN(CHAR(10);FILTER(OFFSET(ModificadoresObservacoes;5;0);OFFSET(ModificadoresObservacoes;5;0)<>"")){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Extrai observações inseridas nos modificadores.



* * *

##### **TextoSumula** `D8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}="DADOS DO BENEFÍCIO:"&CHAR(10)& SUBSTITUTE(SUBSTITUTE(SUBSTITUTE(CONCATENATE(ModeloSumulaBeneficio);"${Especie}";Especie&" - "&INDEX(ListaBeneficios!A:B;MATCH(Especie;ListaBeneficios!A:A;0);2);1);"${RMI}";RMI);"${DIB}";DIB){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Indica o texto que deve constar da Súmula.