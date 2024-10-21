---
layout: post
title:  "Mi primer file!"
date:   2024-10-21 10:39:18 -0500
categories: jekyll update
---

<script type="text/javascript"
  src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>

## <font color="blue">1.1 Series de tiempo Estacionarias y No Estacionarias </font>

<font color="orange"> Proceso estocástico estacionario</font> (estacionariedad estricta).

El proceso estocástico $$\left\{x_t: t=1,2, \ldots\right\}$$ es estacionario si la distribución conjunta de $$ \left(x_{1}, x_{2}\right.$$, $$\left.\ldots, x_{m}\right)$$ es la mismo que la distribución conjunta de $$\left(x_{1+h} , x_{2+h}, \ldots, x_{m+h}\right)$$ para todos los números enteros $$h \geq 1$$.
> - La secuencia es identicamente distribuida
> - No hay restriccion sobre como  $$ \left(x_{1}, x_{2}\right.$$, $$\left.\ldots, x_{m}\right)$$ esta relacionado con $$\left(x_{1+h} , x_{2+h}, \ldots, x_{m+h}\right)$$
> - Estacionariedad requiere que la naturaleza de cualquier correlacion entre dos terminos adjacentes sea la misma a lo largo del tiempo.


<font color="green">Nota:</font> Un proceso estocástico que no es estacionario se dice **Proceso No Estacionario**.


```
clear
set obs 10000

gen t=_n
tsset t

gen y = .
replace y = 1 if t==1

gen e = rnormal()


forvalues i=2/10000 {
	qui: replace y = 1+  0.25*l.e + e if t==`i'
	}
	
line y t
```

