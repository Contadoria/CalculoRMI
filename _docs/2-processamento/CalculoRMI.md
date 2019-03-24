---
title: CalculoRMI
category: Processamento
order: 2
---

##### **AdmiteZero** `H:H`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(AdmiteZero)=1;"Admite Zero?";IF(ROW(AdmiteZero)<=TotalCompetencias+1;UPPER(OFFSET(ModificadoresUsarPiso;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1))<>"SIM";""))){% endhighlight %}





* * *

##### **Competencia** `A:A`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Competencia)=1;"Competência";IF(ROW(Competencia)<=TotalCompetencias+1;EOMONTH(CompetenciaInicial;ROW(Competencia)-3)+1;""))){% endhighlight %}


~~~
mm/yyyy
~~~




* * *

##### **FatorAtualizacao** `M:M`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorAtualizacao)=1;"Fator Atualização";IF(ROW(FatorAtualizacao)<=TotalCompetencias+1;jef_INDICE_ACUMULADO(OFFSET(IndiceMensalAtualizacaoAjustado;0;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
0.00000000
~~~




* * *

##### **IndiceMensalAtualizacao** `J:J`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacao)=1;"Índice Mensal";IF(ROW(IndiceMensalAtualizacao)<=TotalCompetencias+1;IF(ISNUMBER(IndiceMensalAtualizacaoModificado);IndiceMensalAtualizacaoModificado;OFFSET(IndiceSalarios;LinhaInicialTabelaIndices-2;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
0.00000000
~~~




* * *

##### **IndiceMensalAtualizacaoAjustado** `L:L`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoAjustado)=1;"Índice Ajustado";IF(ROW(IndiceMensalAtualizacaoAjustado)<=TotalCompetencias+1;OFFSET(MultiplicadorMoeda;LinhaInicialTabelaIndices-2;0;TotalCompetencias+1)*OFFSET(IndiceMensalAtualizacao;0;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
0.00000000
~~~




* * *

##### **IndiceMensalAtualizacaoModificado** `K:K`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoModificado)=1;"Modificador";IF(ROW(IndiceMensalAtualizacaoModificado)<=TotalCompetencias+1;OFFSET(ModificadoresIndiceMensalAtualizacao;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
0.0000000000
~~~




* * *

##### **IndiceModificado** `K:K`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoModificado)=1;"Modificador";IF(ROW(IndiceMensalAtualizacaoModificado)<=TotalCompetencias+1;OFFSET(ModificadoresIndiceMensalAtualizacao;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
0.0000000000
~~~




* * *

##### **Piso** `B:B`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Piso)=1;"Piso";IF(ROW(Piso)<=TotalCompetencias+1;IF(ISNUMBER(PisoModificado);PisoModificado;OFFSET(SalarioMinimo;LinhaInicialTabelaIndices-2;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **PisoModificado** `C:C`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PisoModificado)=1;"Modificador";IF(ROW(PisoModificado)<=TotalCompetencias+1;OFFSET(ModificadoresPiso;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **SalarioAjustado** `I:I`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioAjustado)=1;"Salário Ajustado";IF(ROW(SalarioAjustado)<=TotalCompetencias+1;IF(SalarioBruto>0;IF(SalarioBruto>Teto;Teto;SalarioBruto);IF(AdmiteZero;0;Piso));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **SalarioAtualizado** `N:N`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioAtualizado)=1;"Salário Atualizado";IF(ROW(SalarioAtualizado)<=TotalCompetencias+1;ROUNDDOWN(SalarioAjustado*FatorAtualizacao;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **SalarioBruto** `F:F`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioBruto)=1;"Salário Bruto";IF(ROW(SalarioBruto)<=(TotalCompetencias+1);IF(ISNUMBER(SalarioBrutoModificado);SalarioBrutoModificado;OFFSET(ResultadoSalariosFornecidos;LinhaInicialTabelaSalarios-2;0;TotalCompetencias+1)+OFFSET(BeneficioEvoluido1;LinhaInicialTabelaSalarios+10;0;TotalCompetencias+1)+OFFSET(BeneficioEvoluido2;LinhaInicialTabelaSalarios+10;0;TotalCompetencias+1)+OFFSET(BeneficioEvoluido3;LinhaInicialTabelaSalarios+10;0;TotalCompetencias+1)+OFFSET(BeneficioEvoluido4;LinhaInicialTabelaSalarios+10;0;TotalCompetencias+1)+OFFSET(BeneficioEvoluido5;LinhaInicialTabelaSalarios+10;0;TotalCompetencias+1)+OFFSET(BeneficioEvoluido6;LinhaInicialTabelaSalarios+10;0;TotalCompetencias+1)+OFFSET(BeneficioEvoluido7;LinhaInicialTabelaSalarios+10;0;TotalCompetencias+1)+OFFSET(BeneficioEvoluido8;LinhaInicialTabelaSalarios+10;0;TotalCompetencias+1)+OFFSET(BeneficioEvoluido9;LinhaInicialTabelaSalarios+10;0;TotalCompetencias+1)+OFFSET(BeneficioEvoluido10;LinhaInicialTabelaSalarios+10;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **SalarioBrutoModificado** `G:G`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioBrutoModificado)=1;"Modificador";IF(ROW(SalarioBrutoModificado)<=TotalCompetencias+1;OFFSET(ModificadoresSalarios;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
0.00
~~~




* * *

##### **SalarioUtilizado** `O:O`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioUtilizado)=1;"Salários Utilizados";IF(ROW(SalarioUtilizado)<=TotalCompetenciasPBC+1;IF(OR(MID(CriterioPC;1;1)="1";MID(CriterioPC;1;1)="2");IF(ISNUMBER(SalarioAtualizado);IF(SalarioAtualizado>0; IF(SalarioAtualizado>MenorSalarioNoPC;TRUE;IF(SalarioAtualizado=MenorSalarioNoPC;IF(Competencia>=CompetenciaLimiteMenorSalario;TRUE;FALSE);FALSE));FALSE);"");IF(SalarioAtualizado=0;FALSE;IF(Competencia<CompetenciaMaisAntigaPC;FALSE;TRUE)));""))){% endhighlight %}





* * *

##### **Teto** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Teto)=1;"Teto";IF(ROW(Teto)<=TotalCompetencias+1;IF(ISNUMBER(TetoModificado);TetoModificado;OFFSET(TetoContribuicao;LinhaInicialTabelaIndices-2;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **TetoModificado** `E:E`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TetoModificado)=1;"Modificador";IF(ROW(TetoModificado)<=TotalCompetencias+1;OFFSET(ModificadoresTeto;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~




* * *

##### **ValoresUtilizados** `P:P`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(ValoresUtilizados)=1;"Valores Utilizados";IF(ROW(SalarioAtualizado)<=TotalCompetencias+1;IF(SalarioUtilizado=TRUE();SalarioAtualizado;0);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


