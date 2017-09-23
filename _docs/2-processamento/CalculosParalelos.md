---
title: CalculosParalelos
category: Processamento
order: 2
---

##### **MediaUltimos12Salarios** `F2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=AVERAGE(E:E){% endhighlight %}

+ **Formato**:
~~~
#,##0.00;(#,##0.00)[Red];-
~~~


> Média dos 12 (doze) últimos salários de contribuição atualizados para verificação da limitação prevista no artigo 29, § 10 da Lei 8.213/91 (incluído pela Medida Provisória nº 664/2014, convertida na Lei 13.135/2015 

* * *

##### **MediaUltimos12SalariosDe15** `M2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=SUM(E:E)/12{% endhighlight %}



> Resultado da divisão entre a soma dos salários e o divisor considerado (salário-maternidade)

* * *

##### **MediaUltimos36SalariosDe48** `K2`{: style="background-color: lightgrey; color: black; border-radius: 5px; padding:3px;"}
+ **Fórmula**:
{% highlight erlang %}=SUM(J:J)/(IF(MID(CriterioPC;1;1)="5";MAX(MIN(COUNTIF(SalarioAtualizado;">0");36);24);MIN(COUNTIF(SalarioAtualizado;">0");36))){% endhighlight %}



> Resultado da divisão entre a soma dos salários e o divisor considerado conforme sistemática anterior à Lei nº 9.876/99