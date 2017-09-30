---
title: Modificadores1
category: Entrada
order: 1
---

##### **AplicarFatorPrevidenciario** `D18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(AplicarFatorPrevidenciarioModificado<>"PADRÃO";AplicarFatorPrevidenciarioModificado<>"");AplicarFatorPrevidenciarioModificado;IF(AND(MID(Especie;1;2)="42";OR(BeneficioDeficiente="Sim"; AND(ISNUMBER(PontuacaoMinima);Pontos>=PontuacaoMinima;TCTotalAnos>=TCMinimoPontuacao)));"FACULTATIVO";INDEX(ListaBeneficios!A:E;MATCH(Especie;ListaBeneficios!A:A;0);5))){% endhighlight %}


~~~
dd/MM/yyyy
~~~


> Identifica a aplicação do fator previdenciário (SIM; NÃO; FACULTATIVA) mediante:
- identificação da espécie do benefício, observada a correspondência na planilha "ListaBenefícios" coluna E
- identificação da implementação de pontuação mínima na espécie "42" 

* * *

##### **AplicarFatorPrevidenciarioModificado** `F18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE ListaBeneficios!E:E
~~~

> Modificador do critério referente à aplicação do fator previdenciário, inserido manualmente, selecionando "SIM", "NÃO" ou "FACULTATIVO"

* * *

##### **ApurarIndiceTetoComFatorPrevidenciario** `D20`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(ApurarIndiceTetoComFatorPrevidenciarioModificado<>"PADRÃO";ApurarIndiceTetoComFatorPrevidenciarioModificado<>"");ApurarIndiceTetoComFatorPrevidenciarioModificado;"SIM"){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~


> Indica a necessidade de apuração do índice de limitação ao teto do salário de benefício  (artigo 26 da Lei 8.870/94 e artigo 21, §3º da Lei 8.880/94) após a publicação da Lei 9.876/99, que criou o fator previdenciário

* * *

##### **ApurarIndiceTetoComFatorPrevidenciarioModificado** `F20`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_LIST SIM,NÃO
~~~

> Modificador do critério referente à apuração do índice de reposição ao teto, inserido manualmente selecionando "SIM" ou "NÃO"

* * *

##### **CriterioPC** `D17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(MID(CriterioPCModificado;1;1)<>"0";CriterioPCModificado<>"");CriterioPCModificado;INDEX(OpcoesPC!A:A;INDEX(ListaBeneficios!A:E;MATCH(Especie;ListaBeneficios!A:A;0);IF(DDA<DPL;3;4))+1)){% endhighlight %}



> Critério para fixação do período contributivo conforme espécie e data do direito adquirido 


* * *

##### **CriterioPCModificado** `F17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE OpcoesPC!A:A
~~~

> Modificador para fixação do período contributivo conforme espécie e data do direito adquirido, selecionado manualmente 

* * *

##### **DDA** `D14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(DDAModificada);DDAModificada;DIB){% endhighlight %}


~~~
dd/MM/yyyy
~~~


> Data do direito adquirido, anterior a DER

* * *

##### **DDAModificada** `F14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Modificador referente a DDA, inserção manual

* * *

##### **DPL** `D7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Data da publicação da Lei 9.876/99

* * *

##### **DataInicioVigenciaPontos** `D8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
dd/MM/yyyy
~~~


> Data da publicação da Medida Provisória nº 676/2015, convertida na Lei nº 11.183/2015

* * *

##### **ExpectativaSobrevida** `D16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(ExpectativaSobrevidaModificada);ExpectativaSobrevidaModificada;INDEX(TabuasMortalidade!A:CD;MATCH(TabuaMortalidadeUtilizada;TabuasMortalidade!A:A;0);MATCH(Idade;TabuasMortalidade!1:1;0))){% endhighlight %}


~~~
#,##0.00
~~~


> Expectativa de sobrevida (ambos os sexos) conforme tábua de mortalidade utilizada

* * *

##### **ExpectativaSobrevidaModificada** `F16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~


> Modificador da expectativa de sobrevida, inserido manualmente

* * *

##### **Idade** `D6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DATEDIF(DataNascimento;DIB;"Y"){% endhighlight %}


~~~
#,##0;(#,##0)
~~~


> Idade do segurado na DER

* * *

##### **Limitacao12Ultimos** `D19`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(Limitacao12UltimosModificada<>"PADRÃO";Limitacao12UltimosModificada<>"");Limitacao12UltimosModificada;IF(DDA<DATEVALUE("2015-03-01");"NÃO";INDEX(ListaBeneficios!A:F;MATCH(Especie;ListaBeneficios!A:A;0);6))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~


> Identifica aplicação da limitação do valor da Renda Mensal Inicial conforme previsto na Medida Provisória nº 664/2014, convertida na Lei 13.135/2015 (média dos doze últimos salários de contribuição) mediante verificação  da data de início do benefício e correspondência da espécie com a planilha "ListaBeneficios" coluna F.

* * *

##### **Limitacao12UltimosModificada** `F19`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
0.###############
~~~


~~~
VALUE_IN_RANGE ListaBeneficios!F:F
~~~

> Modificador do critério referente à limitação do valor da Renda Mensal Inicial conforme previsto na Medida Provisória nº 664/2014, convertida na Lei 13.135/2015 (média dos doze útlimos salários de contribuição) 

* * *

##### **Pontos** `D13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(PontosModificados);PontosModificados;IF(AND(ISNUMBER(TCAnos);ISNUMBER(TCMeses);ISNUMBER(TCDias);ISNUMBER(DataNascimento));TCAnos+(TCMeses/12)+(TCDias/360)+Idade;0)){% endhighlight %}


~~~
#,##0.00
~~~


> Indica os pontos apurados na DER, nos termos da MP nº 676/2015 (idade + tempo de contribuição)

* * *

##### **PontosModificados** `F13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
#,##0.00
~~~


> Modificador dos pontos apurados na DER, inserido manualmente.

* * *

##### **PontuacaoMinima** `D10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DDA<DataInicioVigenciaPontos;"não se aplica";INDEX(TabelaPontuacao!A:C;MATCH(DDA;TabelaPontuacao!A:A;1);IF(Sexo="Homem";2;3))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~


> Indica a pontuação necessária para possibilitar aplicação facultativa do fator previdenciário (apenas para aposentadoria por tempo de contribuição) conforme artigo 29-C da Lei nº 8.213/91 (incluído pela Medida Provisória nº 676/2015, convertida na Lei nº 11.183/2015)

* * *

##### **TCMinimoPontuacao** `D11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(Sexo="Homem";35;30){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~


> Tempo de contribuição mínimo necessário para possibilitar aplicação facultativa do fator previdenciário (apenas para aposentadoria por tempo de contribuição) conforme artigo 29-C, I e II da Lei nº 8.213/91 (incluído pela Medida Provisória nº 676/2015, convertida na Lei nº 11.183/2015)

* * *

##### **TCTotalAnos** `D9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(ISNUMBER(TCAnos);ISNUMBER(TCMeses);ISNUMBER(TCDias);ISNUMBER(DataNascimento));TCAnos+(TCMeses/12)+(TCDias/360);0){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~


> Tempo de contribuição total considerado, em anos.

* * *

##### **TabuaMortalidadeUtilizada** `D15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(ISNUMBER(TabuaMortalidadeUtilizadaModificada);TabuaMortalidadeUtilizadaModificada;MIN(YEAR(DDA)-2;UltimaTabuaMortalidade)){% endhighlight %}


~~~
###0
~~~


> Ano-base dos dados utilizados na elaboração da tábua de mortalidade utilizada (publicada em dezembro do ano seguinte)

* * *

##### **TabuaMortalidadeUtilizadaModificada** `F15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}


~~~
###0
~~~


> Modificador referente ao ano da tábua de mortalidade a ser utilizada, inserção manual.

* * *

##### **UltimaTabuaMortalidade** `D12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MAX(TabuasMortalidade!A:A){% endhighlight %}


~~~
###0
~~~


> Ano-base dos dados utilizados na elaboração da última tábua de mortalidade publicada pelo IBGE.