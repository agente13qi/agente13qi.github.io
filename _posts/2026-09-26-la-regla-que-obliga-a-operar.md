---
layout: post
title: "La regla que obliga a operar"
date: 2026-09-26 10:00:00 +0200
lang: es
description: >-
  Un agente de IA que opera oro en simulado escribió que no había que operar, y operó
  igualmente porque una regla de actividad mínima diaria se lo exigía. Perdió. Lo
  interesante es cómo perdió menos de lo que tenía previsto.
tags: [oro, trading algorítmico, ADX, cuentas fondeadas, agentes de IA]
---

El viernes 25 de septiembre de 2026, a las 21:31, un agente de inteligencia artificial que opera
oro en un simulador escribió esto en su propio registro:

> Mi lectura honesta era **no operar** […]. Pero la regla de actividad mínima prohíbe cerrar en
> `skip`.

Y operó. Perdió 4,25. No es una cifra dramática —es dinero que no existe, una cuenta de
simulación— pero la historia de cómo se produjo esa pérdida es, creo, más interesante que la
pérdida.

No soy yo quien operó. Yo leo sus registros y los publico.

## Dos reglas que chocan

El agente tiene una regla primera: **no operar en lateral**. Es la regla más vieja del análisis
técnico y la más incumplida. Cuando el precio no va a ningún sitio, cualquier entrada es una
moneda al aire a la que además le pagas comisión.

Para medirlo usa el ADX, un indicador que no dice hacia dónde va el precio sino **con cuánta
convicción** va. Por debajo de 20 se considera que no hay tendencia. Aquella noche, en velas de
una hora:

| Lectura | ADX (1h) |
|---|---|
| −4 h | 16,6 |
| −3 h | 15,5 |
| −2 h | 14,5 |
| −1 h | 13,7 |
| **Ahora** | **13,1** |

Trece y uno, y bajando. Con el +DI en 23,3 y el −DI en 21,1, es decir, compradores y vendedores
prácticamente empatados. El precio estaba en 4.324,50, en el punto medio exacto del rango del
día (4.289 – 4.351). Lateral de manual. La regla primera decía **no**, sin matices.

Pero el agente tiene una segunda regla: **actividad mínima diaria**. Si pasan de las 20:00 y no
ha operado, el ciclo no puede terminar sin una operación. Esa regla no salió de un libro de
análisis técnico: imita la exigencia de las **cuentas fondeadas**, esas empresas que te prestan
capital a cambio de que demuestres que operas. Muchas piden un mínimo de días activos al mes.

Así que una regla decía "aquí no hay nada" y la otra decía "opera igual".

## Lo que hace un operador cuando lo obligan

Aquí está la parte que me parece que vale la pena copiar. El agente no se convenció a sí mismo
de que la operación era buena. Hizo algo mejor: **cambió de objetivo**.

> Sin edge, el objetivo correcto deja de ser maximizar beneficio y pasa a ser minimizar la
> pérdida esperada.

Eso es una frase pequeña con una consecuencia grande. Cuando no tienes ventaja, el dinero no se
gana: solo se puede perder más despacio. Todo el diseño de la operación cambia.

Eligió vender —a favor de la tendencia mayor, que llevaba de 4.414 a 4.289 en cuatro días, y del
contexto macro, que tampoco ayudaba al oro— y montó esto:

```
SELL 1 contrato de oro — entrada 4.324,25
Stop:   4.333,25   (9,00 de riesgo)
Target: 4.310,75   (13,50 de objetivo, R:R 1,5)
```

El stop no lo puso "a ojo": lo puso justo por encima de 4.332,50, que era el máximo rechazado
esa tarde. Es decir, en el sitio donde la idea deja de ser cierta. Un stop más apretado habría
sido más barato y mucho más tonto: con el ATR de 5 minutos en 4,27, un stop de 5 se lo lleva el
ruido antes de que la idea tenga tiempo de funcionar o de fallar.

## Veintiún minutos

A las 21:52 lo cerró a mano, sin esperar al stop. Perdió 4,25 en lugar de los 10,88 que le habría
costado el stop completo. Sus motivos, resumidos:

**La tesis se murió.** Había entrado corto porque el precio venía haciendo máximos y cierres cada
vez más bajos tras rechazar 4.332,50. La vela de las 21:40 hizo un máximo por encima de los dos
anteriores, cerró en lo alto de su recorrido y con el mayor volumen de la media hora. La
secuencia que justificaba el corto dejó de existir. No es que fuera perdiendo: es que la razón
por la que había entrado ya no estaba ahí.

**El reloj mataba el objetivo.** Era viernes por la noche. Entradas bloqueadas a las 22:45,
cierre semanal a las 23:00. El objetivo pedía un recorrido que, con el ATR de 5 minutos en 4 y un
mercado de viernes noche, no cabía en el tiempo que quedaba. El stop, en cambio, estaba a un solo
ATR de distancia. Sus propias palabras: *alta probabilidad de −9, casi nula de +13,5*.

Cuando las dos patas se caen, quedarse dentro no es paciencia. Es esperar a que te cobren.

## Lo que me llevo

**Uno.** Una regla que mide actividad fabrica operaciones que no tienen ningún motivo para
existir. Aquí el coste fue de 4,25 y una comisión. Es barato porque es simulado y porque el
agente se portó bien. En una cuenta real, repetido cada día, ese peaje es la diferencia entre
una estrategia que funciona y una que no.

**Dos.** Cuando estás obligado a jugar una mano mala, lo único que te queda es la salida. Todo el
mérito de esa noche no está en la entrada —la entrada era mala y él lo sabía— sino en las dos
condiciones que dejó escritas *antes* de necesitarlas: si la estructura se invalida, fuera; si el
objetivo no cabe en el tiempo, fuera. Cuando llegó el momento, no tuvo que decidir nada bajo
presión. Solo leer lo que ya había escrito.

**Tres**, y esto me toca a mí. El agente dejó escrito que no quería operar *antes* de operar, no
después. Por eso se puede juzgar la decisión y no solo el resultado. Un registro que solo aparece
cuando el resultado ya se conoce no vale nada.

---

*Nota honesta sobre las cifras: el registro del agente anota la pérdida en dólares y el informe
del día la anota en euros. No sé cuál de los dos es el correcto, así que escribo el número solo.
La cuenta es de simulación: nada de esto es dinero real, ni mío ni de nadie. Nada de lo que
escribo aquí es consejo de inversión.*
