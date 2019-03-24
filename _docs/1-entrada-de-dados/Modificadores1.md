---
title: Modificadores1
category: Entrada
order: 2
---

##### **AplicarFatorPrevidenciario** `D18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(AplicarFatorPrevidenciarioModificado<>"PADRÃO";AplicarFatorPrevidenciarioModificado<>"");
AplicarFatorPrevidenciarioModificado;IF(DDA<DATEVALUE("1999-11-29");"NÃO";IF(AND(MID(Especie;1;2)="42";OR(BeneficioDeficiente="Sim";
 AND(ISNUMBER(PontuacaoMinima);Pontos>=PontuacaoMinima;TCTotalAnos>=TCMinimoPontuacao)));"FACULTATIVO";
INDEX(ListaBeneficios!A:E;MATCH(Especie;ListaBeneficios!A:A;0);5)))){% endhighlight %}


~~~
dd/MM/yyyy
~~~




* * *

##### **AplicarFatorPrevidenciarioModificado** `F18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE ListaBeneficios!E:E
~~~



* * *

##### **ApurarIndiceTetoComFatorPrevidenciario** `D20`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(ApurarIndiceTetoComFatorPrevidenciarioModificado<>"PADRÃO";ApurarIndiceTetoComFatorPrevidenciarioModificado<>"");ApurarIndiceTetoComFatorPrevidenciarioModificado;"SIM"){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~




* * *

##### **ApurarIndiceTetoComFatorPrevidenciarioModificado** `F20`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_LIST SIM,NÃO
~~~



* * *

##### **CriterioPC** `D17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(MID(CriterioPCModificado;1;1)<>"0";CriterioPCModificado<>"");CriterioPCModificado;INDEX(OpcoesPC!A:A;INDEX(ListaBeneficios!A:E;MATCH(Especie;ListaBeneficios!A:A;0);IF(DDA<DPL;3;4))+1)){% endhighlight %}





* * *

##### **CriterioPCModificado** `F17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE OpcoesPC!A:A
~~~



* * *

##### **DDA** `D14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DDAModificada);DDAModificada;DIB){% endhighlight %}


~~~
dd/MM/yyyy
~~~




* * *

##### **DDAModificada** `F14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DPL** `D7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **DataInicioVigenciaPontos** `D8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~




* * *

##### **ExpectativaSobrevida** `D16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DDA<DATEVALUE("1999-11-29");"";IF(ISNUMBER(ExpectativaSobrevidaModificada);ExpectativaSobrevidaModificada;INDEX(TabuasMortalidade!A:CD;MATCH(TabuaMortalidadeUtilizada;TabuasMortalidade!A:A;0);MATCH(DATEDIF(DataNascimento;DIB;"Y");TabuasMortalidade!1:1;0)))){% endhighlight %}


~~~
#,##0.00
~~~




* * *

##### **ExpectativaSobrevidaModificada** `F16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **Idade** `D6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DAYS360(DataNascimento;DIB)/360{% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~




* * *

##### **Limitacao12Ultimos** `D19`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(Limitacao12UltimosModificada<>"PADRÃO";Limitacao12UltimosModificada<>"");Limitacao12UltimosModificada;IF(DDA<DATEVALUE("2015-03-01");"NÃO";INDEX(ListaBeneficios!A:F;MATCH(Especie;ListaBeneficios!A:A;0);6))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~




* * *

##### **Limitacao12UltimosModificada** `F19`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE ListaBeneficios!F:F
~~~



* * *

##### **Pontos** `D13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(PontosModificados);PontosModificados;IF(AND(ISNUMBER(TCAnos);ISNUMBER(TCMeses);ISNUMBER(TCDias);ISNUMBER(DataNascimento));TCAnos+(TCMeses/12)+(TCDias/360)+Idade;0)){% endhighlight %}


~~~
#,##0.00
~~~




* * *

##### **PontosModificados** `F13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~




* * *

##### **PontuacaoMinima** `D10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DDA<DataInicioVigenciaPontos;"não se aplica";INDEX(TabelaPontuacao!A:C;MATCH(DDA;TabelaPontuacao!A:A;1);IF(Sexo="Homem";2;3))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~




* * *

##### **TCMinimoPontuacao** `D11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(Sexo="Homem";35;30){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~




* * *

##### **TCTotalAnos** `D9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(ISNUMBER(TCAnos);ISNUMBER(TCMeses);ISNUMBER(TCDias);ISNUMBER(DataNascimento));TCAnos+(TCMeses/12)+(TCDias/360);0){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~




* * *

##### **TabuaMortalidadeUtilizada** `D15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(TabuaMortalidadeUtilizadaModificada);TabuaMortalidadeUtilizadaModificada;INDEX(TabuasMortalidade!A:A;ARRAYFORMULA(COUNTIF(OFFSET(TabuasMortalidade!A:A;1;COUNTA(TabuasMortalidade!B1:1);COUNTA(TabuasMortalidade!B:B)-1);"<="&DIB))+1;1)){% endhighlight %}


~~~
###0
~~~




* * *

##### **TabuaMortalidadeUtilizadaModificada** `F15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
###0
~~~




* * *

##### **UltimaTabuaMortalidade** `D12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MAX(TabuasMortalidade!A:A){% endhighlight %}


~~~
###0
~~~


