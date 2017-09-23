---
title: ParametrosRMI
category: Processamento
order: 1
---

##### **AplicacaoProgressivaFatorPrevidenciario** `B18`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(AND(DDA>=DATE(1999;11;29);DDA<=DATE(1999;11;30));1;MIN(DATEDIF(DATE(1999;12;1);DDA;"M")+1;60)){% endhighlight %}

+ **Formato**:
~~~
0.00
~~~


> Quantidade de meses considerados para aplicação da progressividade do fator previdenciário conforme artigo 5º da Lei nº 9.876/99.
"MINIMO(DATADIF)" identifica o menor número de meses entre 60 e 

* * *

##### **BaseIndiceTeto** `B29`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(OR(MID(CriterioPC;1;1)="1";MID(CriterioPC;1;1)="2");IF(ApurarIndiceTetoComFatorPrevidenciario="SIM";SalarioBeneficio;MAX(SalarioBeneficio;MediaSemFatorPrevidenciario));SalarioBeneficio){% endhighlight %}

+ **Formato**:
~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Base de cálculo para apuração do índice de reposição previsto nos artigos 26 da Lei nº 8.870/94 e 21, § 3º da Lei nº 8.880/94.
Considerada a opção "SIM" na planilha "Modificadores1", célula F20, será utilizado o valor após aplicação do fator previdenciário. Caso contrário, será utilizado o valor sem aplicação do fator previdenciário.

* * *

##### **CompetenciaFinal** `B4`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=EOMONTH(DDA;-2)+1{% endhighlight %}

+ **Formato**:
~~~
mm"/"yyyy
~~~


> Mês referente à última competência utilizada para fixação do período básico de cálculo.

* * *

##### **CompetenciaInicial** `B3`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(OR(MID(CriterioPC;1;1)="4";MID(CriterioPC;1;1)="5");EDATE((EOMONTH(DDA;-1)+1);-48);IF(MID(CriterioPC;1;1)="3";EDATE((EOMONTH(DDA;-1)+1);-48);DATE(1994;7;1))){% endhighlight %}

+ **Formato**:
~~~
mm"/"yyyy
~~~


> Mês referente à primeira competência utilizada para fixação do período básico de cálculo.
* Caso CriterioPC (célula D17 da aba Modificadores) seja igual a 4 ou 5, corresponderá ao 48º mês anterior à data do direito adquirido (DDA).
* Caso CriterioPC (célula D17 da aba Modificadores) seja igual a 3, corresponderá ao 15º mês anterior á data do direito adquirido (DDA).
* Caso CriterioPC (célula D17 da aba Modificadores) seja igual a 1 ou 2, corresponderá a julho/94.

* * *

##### **DivisorConsiderado** `B14`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=MAX(PCConsiderado;DivisorMinimo){% endhighlight %}

+ **Formato**:
~~~
0
~~~


> Divisor utilizado, considerados divisor mínimo e período contributivo considerado, identifica o valor máximo entre "PCConsiderado" e "DivisorMinimo".

* * *

##### **DivisorMinimo** `B10`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(MID(CriterioPC;1;1)="2";ROUNDDOWN(TotalCompetencias*0,6);IF(MID(CriterioPC;1;1)="3";12;IF(MID(CriterioPC;1;1)="5";24;ROUNDDOWN(TotalSalariosDDA*0,8)))){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Divisor mínimo a ser utilizado, observado critério de fixação do período contributivo na planilha "Modificadores1" célula D17.

* * *

##### **FatorPrevidenciario** `B17`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=(TCTotalDias/360)*0,31/ExpectativaSobrevida*(1+(IdadeTotal+((TCTotalDias/360)*0,31))/100){% endhighlight %}

+ **Formato**:
~~~
0.0000
~~~


> Fator previdenciário apurado com base na fórmula cosntante do anexo da Lei nº 9.876/99.

* * *

##### **IdadeTotal** `B16`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=DAYS360(DataNascimento;DIB)/360{% endhighlight %}

+ **Formato**:
~~~
0.00
~~~


> Idade total do segurado contada em anos.

* * *

##### **IndiceTeto** `B30`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=MAX(BaseIndiceTeto/TetoDDA;1){% endhighlight %}

+ **Formato**:
~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Índice de reposição apurado previsto nos artigos 26 da Lei nº 8.870/94 e 21, § 3º da Lei nº 8.880/94.
Seleciona o valor máximo entre "1" e a divisão de "BaseIndiceTeto" por "TetoDDA"

* * *

##### **LinhaInicialTabelaIndices** `B5`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=MATCH(CompetenciaInicial;IndicesConsolidados!A:A;0){% endhighlight %}

+ **Formato**:
~~~
0
~~~


> Indica a linha da tabela "IndicesConsolidados" correspondente à competência inicial

* * *

##### **LinhaInicialTabelaModificadores** `B6`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=MATCH(CompetenciaInicial;CompetenciaModificadores;0){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Indica a linha da tabela "Modificadores2" correspondente à competência inicial.


* * *

##### **LinhaInicialTabelaSalarios** `B7`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=MATCH(CompetenciaInicial;CalculoSalarios!A:A;0){% endhighlight %}

+ **Formato**:
~~~
0
~~~


> Indica a linha da tabela "CalculoSalarios" referente à competência inicial.

* * *

##### **MediaComFatorPrevidenciario** `B21`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=((MediaSemFatorPrevidenciario*FatorPrevidenciario*AplicacaoProgressivaFatorPrevidenciario)/60)+((MediaSemFatorPrevidenciario*(60-AplicacaoProgressivaFatorPrevidenciario))/60){% endhighlight %}

+ **Formato**:
~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Resultado da média da somatória dos s.c. atualizados, após aplicação do fator previdenciário (progressivo, se for o caso).

* * *

##### **MediaSemFatorPrevidenciario** `B20`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(AtividadeSecundaria="Sim";(SomaSalarios/DivisorConsiderado)*NumeradorAtividadeSecundaria/DenominadorAtividadeSecundaria;(SomaSalarios/DivisorConsiderado)+ValorAtividadeSecundaria){% endhighlight %}

+ **Formato**:
~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Resultado da divisão entre a soma dos salários e o divisor considerado.
No caso de atividade secundária apurada nos termos do art. 32, da Lei nº 8.213/91, aplica o coeficiente da atividade secundária à média obtida.

* * *

##### **PBCMaximo** `B11`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(MID(CriterioPC;1;1)="3";15;IF(OR(MID(CriterioPC;1;1)="4";MID(CriterioPC;1;1)="5");48;TotalCompetencias)){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Identifica a quantidade máxima de meses contidos no período básico de cálculo, observada a seleção do "CriterioPC" na planilha "Modificadores1".

* * *

##### **PCConsiderado** `B13`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=MIN(TotalSalariosDDA;MAX(PCMaximo;DivisorMinimo)){% endhighlight %}



> Identifica a quantidade de salários de contribuição utilizados, observados divisor mínimo e período contributivo máximo.

* * *

##### **PCMaximo** `B12`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=IF(OR(MID(CriterioPC;1;1)="1";MID(CriterioPC;1;1)="2");ROUNDDOWN(TotalSalariosDDA*0,8);IF(MID(CriterioPC;1;1)="3";12;IF(OR(MID(CriterioPC;1;1)="4";MID(CriterioPC;1;1)="5");36;TotalSalariosDDA))){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Identifica a quantidade máxima de salários de contribuição que podem ser utilizados no cálculo, observada a seleção do "CriterioPC" na planilha "Modificadores1".

* * *

##### **PisoDDA** `B22`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=INDEX(SalarioMinimo;MATCH(EOMONTH(DDA;-1)+1;IndicesConsolidados!A:A;0)){% endhighlight %}

+ **Formato**:
~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Identifica o valor mínimo do benefício considerado na data do direito adquirido.

* * *

##### **RMI** `B28`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=MIN(TetoDDA;MAX(IF(Limitacao12Ultimos="SIM";MIN(SalarioBeneficio*Coeficiente;MediaUltimos12Salarios);SalarioBeneficio*Coeficiente);IF(MID(Especie;1;2)="36";PisoDDA*Coeficiente;PisoDDA))){% endhighlight %}

+ **Formato**:
~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Renda mensal inicial apurada correspondente ao valor do salário-de-benefício multiplicado pelo coeficiente de cálculo, observado o critério de fixação do período contributivo selecionado na planilha "Modificadores1"

* * *

##### **SalarioBeneficio** `B27`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=MIN(TetoDDA;MAX(PisoDDA;IF(OR(MID(CriterioPC;1;1)="4";MID(CriterioPC;1;1)="5");MediaUltimos36SalariosDe48;IF(MID(CriterioPC;1;1)="3";MediaUltimos12SalariosDe15;IF(AplicarFatorPrevidenciario="FACULTATIVO";MAX(MediaComFatorPrevidenciario;MediaSemFatorPrevidenciario);IF(AplicarFatorPrevidenciario="NÃO";MediaSemFatorPrevidenciario;MediaComFatorPrevidenciario)))))){% endhighlight %}

+ **Formato**:
~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Indica o salário-de-benefício, considerados o piso e o teto previdenciário, observados: 
-o critério do período contributivo selecionado na planilha "Modificadores1" célula D17
-aplicação do fator previdenciário


* * *

##### **SomaSalarios** `B19`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=SUM(ARRAYFORMULA(OFFSET(SalarioAtualizado;1;0;TotalCompetencias)*OFFSET(SalarioUtilizado;1;0;TotalCompetencias))){% endhighlight %}

+ **Formato**:
~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Soma dos salários de contribuição   atualizados, extraídos da planilha "CalculoRMI" coluna N.

* * *

##### **TCTotalDias** `B15`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=(TCAnos*360)+(TCMeses*30)+TCDias + (IF(Sexo="Mulher";360*5;0)){% endhighlight %}

+ **Formato**:
~~~
0.00
~~~


> Tempo de contribuição em dias, já consideradas as conversões de períodos e sexo do segurado.

* * *

##### **TetoDDA** `B23`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=INDEX(TetoBeneficio;MATCH(EOMONTH(DDA;-1)+1;IndicesConsolidados!A:A;0)){% endhighlight %}

+ **Formato**:
~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Teto máximo de contribuição considerado na data do direito adquirido

* * *

##### **TotalCompetencias** `B8`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=DATEDIF(CompetenciaInicial;CompetenciaFinal;"M")+1{% endhighlight %}



> Indica a quantidade de competência entre as competências inicial (inclusive) e final (inclusive).

* * *

##### **TotalSalariosDDA** `B9`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=COUNTIF(SalarioAtualizado;">0"){% endhighlight %}

+ **Formato**:
~~~
0.###############
~~~


> Quantidade de meses do período básico de cálculo que possuem salários de contribuição informados