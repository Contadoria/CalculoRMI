---
title: ParametrosRMI
category: Processamento
order: 1
---

##### **AplicacaoProgressivaFatorPrevidenciario** `B25`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AND(DDA>=DATE(1999;11;29);DDA<=DATE(1999;11;30));1;MIN(DATEDIF(DATE(1999;12;1);DDA;"M")+1;60)){% endhighlight %}


~~~
0.00
~~~




* * *

##### **BaseIndiceTeto** `B34`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(OR(MID(CriterioPC;1;1)="1";MID(CriterioPC;1;1)="2");IF(ApurarIndiceTetoComFatorPrevidenciario="SIM";MediaComFatorPrevidenciario;MAX(MediaComFatorPrevidenciario;MediaSemFatorPrevidenciario));MediaSemFatorPrevidenciario){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **CompetenciaFinal** `B4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=EOMONTH(DIB;-2)+1{% endhighlight %}


~~~
mm"/"yyyy
~~~




* * *

##### **CompetenciaInicial** `B3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(OR(MID(CriterioPC;1;1)="4";MID(CriterioPC;1;1)="5");EDATE((EOMONTH(DDA;-1)+1);-48);IF(MID(CriterioPC;1;1)="3";EDATE((EOMONTH(DDA;-1)+1);-15);DATE(1994;7;1))){% endhighlight %}


~~~
mm"/"yyyy
~~~




* * *

##### **CompetenciaLimiteMenorSalario** `B18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(OR(MID(CriterioPC;1;1)="1";MID(CriterioPC;1;1)="2");IF(NumeroSalariosExcedentes>0;MIN(QUERY(QUERY(SORT(FILTER({OFFSET(Competencia;1;0;PBCMaximo)\OFFSET(SalarioAtualizado;1;0;PBCMaximo)};OFFSET(Competencia;1;0;PBCMaximo)<>"";OFFSET(SalarioAtualizado;1;0;PBCMaximo)=MenorSalarioNoPC);1;FALSE);"Select * limit "&NumeroMenoresSalariosUtilizados);"Select Col1"));INDEX(OFFSET(Competencia;0;0;COUNTA(Competencia);COLUMN(SalarioAtualizado));MATCH(MenorSalarioNoPC;SalarioAtualizado;0);1));CompetenciaInicial){% endhighlight %}


~~~
dd/MM/yyyy
~~~




* * *

##### **CompetenciaMaisAntigaPC** `B21`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(OR(MID(CriterioPC;1;1)="3";MID(CriterioPC;1;1)="4";MID(CriterioPC;1;1)="5");MIN(QUERY(QUERY(QUERY(SORT(FILTER({OFFSET(Competencia;1;0;PBCMaximo)\OFFSET(SalarioAtualizado;1;0;PBCMaximo)};OFFSET(Competencia;1;0;PBCMaximo)<>"");1;FALSE);"Select * limit "&PBCMaximo);"Select * WHERE Col2<>0 limit "&PCNormal);"Select Col1"));CompetenciaInicial){% endhighlight %}


~~~
dd/MM/yyyy
~~~




* * *

##### **DivisorConsiderado** `B19`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MAX(PCConsiderado;DivisorMinimo){% endhighlight %}


~~~
0
~~~




* * *

##### **DivisorMinimo** `B11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MID(CriterioPC;1;1)="2";ROUNDDOWN(TotalCompetencias*0,6);IF(MID(CriterioPC;1;1)="3";12;IF(MID(CriterioPC;1;1)="5";24;ROUNDDOWN(TotalSalariosDDA*0,8)))){% endhighlight %}


~~~
0.###############
~~~




* * *

##### **FatorPrevidenciario** `B24`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DDA<DATEVALUE("1999-11-29");"";(TCTotalDias/360)*0,31/ExpectativaSobrevida*(1+(IdadeTotal+((TCTotalDias/360)*0,31))/100)){% endhighlight %}


~~~
0.0000
~~~




* * *

##### **IdadeTotal** `B23`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DAYS360(DataNascimento;DIB)/360{% endhighlight %}


~~~
0.00
~~~




* * *

##### **IndiceTeto** `B35`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(DDA>DATEVALUE("1991-4-4");MAX(BaseIndiceTeto/TetoDIB;1);""){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **LinhaInicialTabelaIndices** `B5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(CompetenciaInicial;CompetenciaIndices;0){% endhighlight %}


~~~
0
~~~




* * *

##### **LinhaInicialTabelaModificadores** `B6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(CompetenciaInicial;CompetenciaModificadores;0){% endhighlight %}


~~~
0.###############
~~~




* * *

##### **LinhaInicialTabelaSalarios** `B7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MATCH(CompetenciaInicial;CompetenciaSalarios;0){% endhighlight %}


~~~
0
~~~




* * *

##### **MediaComFatorPrevidenciario** `B28`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=((ROUNDDOWN(SomaSalarios/DivisorConsiderado;2)*FatorPrevidenciario*AplicacaoProgressivaFatorPrevidenciario)/60)+((ROUNDDOWN(SomaSalarios/DivisorConsiderado;2)*(60-AplicacaoProgressivaFatorPrevidenciario))/60)+ValorAtividadeSecundaria{% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **MediaSemFatorPrevidenciario** `B27`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AtividadeSecundaria="Sim";(SomaSalarios/DivisorConsiderado)*NumeradorAtividadeSecundaria/DenominadorAtividadeSecundaria;(ROUNDDOWN(SomaSalarios/DivisorConsiderado;2))+ValorAtividadeSecundaria){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **MediaUltimos12SC** `B31`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ROUNDDOWN(SUM(QUERY(SORT(FILTER({OFFSET(Competencia;1;0)\OFFSET(SalarioAtualizado;1;0)};OFFSET(Competencia;1;0)<>"";OFFSET(SalarioAtualizado;1;0)<>0);1;FALSE);"Select Col2 limit 12"))/SUM(ARRAYFORMULA(SIGN(QUERY(SORT(FILTER({OFFSET(Competencia;1;0)\OFFSET(SalarioAtualizado;1;0)};OFFSET(Competencia;1;0)<>"";OFFSET(SalarioAtualizado;1;0)<>0);1;FALSE);"Select Col2 limit 12"))));2){% endhighlight %}


~~~
#,##0.00;(#,##0.00)
~~~




* * *

##### **MenorSalarioNoPC** `B15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(OR(MID(CriterioPC;1;1)="1";MID(CriterioPC;1;1)="2");LARGE(OFFSET(SalarioAtualizado;1;0;PBCMaximo);PCConsiderado);0){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **NumeroMenoresSalariosUtilizados** `B17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=COUNTIF(SalarioAtualizado;"="&MenorSalarioNoPC)-NumeroSalariosExcedentes{% endhighlight %}


~~~
0
~~~




* * *

##### **NumeroSalariosExcedentes** `B16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(OR(MID(CriterioPC;1;1)="1";MID(CriterioPC;1;1)="2");COUNTIF(OFFSET(SalarioAtualizado;1;0;PBCMaximo);">="&MenorSalarioNoPC)-PCConsiderado;0){% endhighlight %}


~~~
0
~~~




* * *

##### **PBCMaximo** `B12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(MID(CriterioPC;1;1)="3";15;IF(OR(MID(CriterioPC;1;1)="4";MID(CriterioPC;1;1)="5");48;TotalCompetencias)){% endhighlight %}





* * *

##### **PCConsiderado** `B14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=MIN(TotalSalariosDDA;MAX(PCNormal;DivisorMinimo)){% endhighlight %}





* * *

##### **PCNormal** `B13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(OR(MID(CriterioPC;1;1)="1";MID(CriterioPC;1;1)="2");ROUNDDOWN(TotalSalariosDDA*0,8);IF(MID(CriterioPC;1;1)="3";12;IF(OR(MID(CriterioPC;1;1)="4";MID(CriterioPC;1;1)="5");36;TotalSalariosDDA))){% endhighlight %}


~~~
0.###############
~~~




* * *

##### **PisoDIB** `B29`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=IF(AtividadeSecundaria="Sim";0;INDEX(SalarioMinimo;MATCH(EOMONTH(DIB;-1)+1;IndicesConsolidados!A:A;0))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **RMI** `B33`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ROUND(MIN(TetoDIB;MAX(IF(Limitacao12Ultimos="SIM";MIN(SalarioBeneficio*Coeficiente;MediaUltimos12SC);SalarioBeneficio*Coeficiente);IF(MID(Especie;1;2)="36";PisoDIB*Coeficiente;PisoDIB)));2){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **SalarioBeneficio** `B32`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ROUNDDOWN (MIN(TetoDIB;MAX(PisoDIB;IF(AplicarFatorPrevidenciario="NÃO";MediaSemFatorPrevidenciario; IF(AplicarFatorPrevidenciario="FACULTATIVO";MAX(MediaComFatorPrevidenciario;MediaSemFatorPrevidenciario);MediaComFatorPrevidenciario))));2){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **SomaSalarios** `B26`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=SUM(ARRAYFORMULA(OFFSET(SalarioAtualizado;1;0;TotalCompetencias)*OFFSET(SalarioUtilizado;1;0;TotalCompetencias))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TCTotalDias** `B22`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=(TCAnos*360)+(TCMeses*30)+TCDias + (IF(Sexo="Mulher";360*5;0)) + (IF(Especie=57;360*5;0)){% endhighlight %}


~~~
0
~~~




* * *

##### **TetoDIB** `B30`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=INDEX(TetoContribuicao;MATCH(EOMONTH(DIB;-1)+1;IndicesConsolidados!A:A;0)){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TotalCompetencias** `B8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=DATEDIF(CompetenciaInicial;CompetenciaFinal;"M")+1{% endhighlight %}





* * *

##### **TotalCompetenciasPBC** `B9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=COUNTIF(Competencia;"<"&EOMONTH(DDA;-1)+1){% endhighlight %}


~~~
0.###############
~~~




* * *

##### **TotalSalariosDDA** `B10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=COUNTIFS(SalarioAtualizado;">0";Competencia;"<"&EOMONTH(DDA;-1)+1){% endhighlight %}


~~~
0.###############
~~~


