---
title: CalculoRMI
category: Processamento
order: 3
---

##### **AdmiteZero** `H:H`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(AdmiteZero)=1;"Admite Zero?";IF(ROW(AdmiteZero)<=TotalCompetencias+1;UPPER(OFFSET(ModificadoresUsarPiso;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1))<>"SIM";""))){% endhighlight %}



> Matriz referentes às competências em que são admitidos valores iguais a zero. Caso contrário, haverá preenchimento com o valor do salário-mínimo (ModificadoresUsarPiso na aba Modificadores2, coluna H).

* * *

##### **Competencia** `A:A`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Competencia)=1;"Competência";IF(ROW(Competencia)<=TotalCompetencias+1;EOMONTH(CompetenciaInicial;ROW(Competencia)-2);""))){% endhighlight %}


~~~
mm/yyyy
~~~


> Fórmula Matriz (ArrayFormula) 
Seleciona as competências do PBC a partir da planilha "ParametrosRMI" entre CompetênciaInicial e TotalCompetencias.

* * *

##### **FatorAtualizacao** `M:M`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(FatorAtualizacao)=1;"Fator Atualização";IF(ROW(FatorAtualizacao)<=TotalCompetencias+1;jef_INDICE_ACUMULADO(OFFSET(IndiceMensalAtualizacao;0;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
0.00000000
~~~


> Fórmula Matriz (ArrayFormula) 
calcula os índices acumulados a partir de uma matriz construída pelos índices mensais (coluna J) em relação ao total de competências.

* * *

##### **IndiceMensalAtualizacao** `J:J`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacao)=1;"Índice Mensal";IF(ROW(IndiceMensalAtualizacao)<=TotalCompetencias+1;IF(ISNUMBER(IndiceMensalAtualizacaoModificado);IndiceMensalAtualizacaoModificado;OFFSET(IndiceSalarios;LinhaInicialTabelaIndices-2;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
0.00000000
~~~


> Fórmula Matriz (ArrayFormula) 
Seleciona os índices mensais a partir da planilha "IndicesConsolidados" coluna N, assumindo modificações inseridas.

* * *

##### **IndiceMensalAtualizacaoAjustado** `L:L`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoAjustado)=1;"Índice Ajustado";IF(ROW(IndiceMensalAtualizacaoAjustado)<=TotalCompetencias+1;OFFSET(AjusteMoeda;LinhaInicialTabelaIndices-2;0;TotalCompetencias+1)*OFFSET(IndiceMensalAtualizacao;0;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
0.00000000
~~~


> Fórmula Matriz (ArrayFormula) 
Seleciona os índices mensais a partir da planilha "IndicesConsolidados" observado o ajuste de moeda, coluna I.

* * *

##### **IndiceMensalAtualizacaoModificado** `K:K`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoModificado)=1;"Modificador";IF(ROW(IndiceMensalAtualizacaoModificado)<=TotalCompetencias+1;OFFSET(ModificadoresIndiceMensalAtualizacao;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
0.0000000000
~~~


> Fórmula Matriz (ArrayFormula) 
Seleciona os índices mensais modificados a partir da planilha "Modificadores2" coluna F.

* * *

##### **IndiceModificado** `K:K`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(IndiceMensalAtualizacaoModificado)=1;"Modificador";IF(ROW(IndiceMensalAtualizacaoModificado)<=TotalCompetencias+1;OFFSET(ModificadoresIndiceMensalAtualizacao;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
0.0000000000
~~~


> Fórmula Matriz (ArrayFormula) 
Seleciona os índices mensais modificados a partir da planilha "Modificadores2" coluna F.

* * *

##### **Piso** `B:B`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Piso)=1;"Piso";IF(ROW(Piso)<=TotalCompetencias+1;IF(ISNUMBER(PisoModificado);PisoModificado;OFFSET(SalarioMinimo;LinhaInicialTabelaIndices-2;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Fórmula Matriz (ArrayFormula) 
indica o piso salarial a partir do salário mínimo constante da planilha "IndicesConsolidados" coluna B, ou, "PisoModificado" inserido.

* * *

##### **PisoModificado** `C:C`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(PisoModificado)=1;"Modificador";IF(ROW(PisoModificado)<=TotalCompetencias+1;OFFSET(ModificadoresPiso;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Fórmula Matriz (ArrayFormula) 
indica o piso salarial modificado extraído da planilha "Modificadores2" coluna D.

* * *

##### **SalarioAjustado** `I:I`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioAjustado)=1;"Salário Ajustado";IF(ROW(SalarioAjustado)<=TotalCompetencias+1;IF(SalarioBruto>0;IF(SalarioBruto>Teto;Teto;SalarioBruto);IF(AdmiteZero;0;Piso));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Fórmula Matriz (ArrayFormula) indica o salário ajustado mediante: 
-limitação do salário bruto ao teto
-assume piso salarial quando não admite zero

* * *

##### **SalarioAtualizado** `N:N`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioAtualizado)=1;"Salário Atualizado";IF(ROW(SalarioAtualizado)<=TotalCompetencias+1;ROUND(SalarioAjustado*FatorAtualizacao;2);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Fórmula Matriz (ArrayFormula) apura o salário atualizado em cada competência mediante aplicação do fator de atualização sobre o salário ajustado.

* * *

##### **SalarioBruto** `F:F`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioBruto)=1;"Salário Bruto";IF(ROW(SalarioBruto)<=(TotalCompetencias+1);IF(ISNUMBER(SalarioBrutoModificado);SalarioBrutoModificado;OFFSET(ResultadoSalariosFornecidos;LinhaInicialTabelaSalarios-2;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Fórmula Matriz (ArrayFormula) 
Seleciona os salários totais por competência da planilha "CalculoSalarios" coluna B, assumindo os modificadores.

* * *

##### **SalarioBrutoModificado** `G:G`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioBrutoModificado)=1;"Modificador";IF(ROW(SalarioBrutoModificado)<=TotalCompetencias+1;OFFSET(ModificadoresSalarios;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
0.00
~~~


> Fórmula Matriz (ArrayFormula) 
Seleciona os salários modificados constantes da planilha "Modificadores2" coluna G.

* * *

##### **SalarioUtilizado** `O:O`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(SalarioUtilizado)=1;"Salários Utilizados";IF(ROW(SalarioUtilizado)<=TotalCompetencias+1;IF(OR(MID(CriterioPC;1;1)="1";MID(CriterioPC;1;1)="2");IF(ISNUMBER(SalarioAtualizado);IF(SalarioAtualizado>0; SalarioAtualizado>=LARGE(SalarioAtualizado;PCConsiderado);FALSE);"");2);""))){% endhighlight %}



> Fórmula Matriz (ArrayFormula) 
indica por "VERDADEIRO" ou "FALSO" as competências com salários selecionados para o cálculo.

* * *

##### **Teto** `D:D`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(Teto)=1;"Teto";IF(ROW(Teto)<=TotalCompetencias+1;IF(ISNUMBER(TetoModificado);TetoModificado;OFFSET(TetoBeneficio;LinhaInicialTabelaIndices-2;0;TotalCompetencias+1));""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Fórmula Matriz (ArrayFormula) 
indica o teto do benefício constante da planilha "IndicesConsolidados" coluna E, ou, "TetoModificado" inserido.

* * *

##### **TetoModificado** `E:E`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
{% highlight erlang %}=ARRAYFORMULA(IF(ROW(TetoModificado)=1;"Modificador";IF(ROW(TetoModificado)<=TotalCompetencias+1;OFFSET(ModificadoresTeto;LinhaInicialTabelaModificadores-2;0;TotalCompetencias+1);""))){% endhighlight %}


~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Fórmula Matriz (ArrayFormula) 
indica o teto do benefício modificado extraído da planilha "Modificadores2" coluna E.