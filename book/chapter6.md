# Control de flux iteratiu
En el [Capítol 5](chapter5.md) hem vist que el control de flux condicional permet l'execució d'un determinat bloc de codi si es compleix una condició. El control de flux iteratiu, en canvi, permet **repetir** un tros de codi (bloc de codi) mentre una determinada condició es compleixi, és a dir, sigui certa. Cada execució o repetició del bloc codi gestionat pel control de flux iteratiu s'anomena iteració o volta.

Hi ha tres sentències de **control de flux iteratiu** bàsiques, les quals, s'acostumen a mal anomenar *bucles*:
1. la sentència `while`;
2. la sentència `do-while` i
3. la sentència `for`.

L'ús d'aquestes estructures de control 
* evita crear codi duplicat (sempre que un programador té la intenció de fer *copy/paste* s'ha de preguntar si el codi es pot posar dins d'un *bucle*);
* simplifica la implementació dels algorismes i 
* facilita la detecció d'errors.

## Característiques que han de complir totes les estructrues de control de flux iteratiu
Tota sentència de control de flux iteratiu ha de complir 3 característques bàsiques:
1. Ha d'inicialitzar els valors de totes aquelles variables que intervenen en la condició de manera adequada
2. Ha de definir quina és la condició que permet entrar dins del bloc de codi del *bucle* i fer una nova repetició (iteració o volta)
3. A cada volta ha d'actualitzar els valors de les variables que intervenen en la condició per tal que, en un determinat moment, la condició sigui falsa (`false`) i, per tant, el codi pugui sortir de les iteracions; en cas contrari es crea un *bucle* infinit i l'algorisme queda bloquejat.

## Sentència `while`
La sentència `while` defineix un bloc de codi que es va repetint una i altra vegada mentre una determinada condició es compleix, és a dir, la condició s'avalua a `true`.

L'estructura de la sentència `while` és la següent:
```java
    while(condition) {
        //Bloc de codi que volem executar (i anar repetint) mentre condition és true
    }
```

La Figura 6.1 mostra el diagrama de flux corresponent a la sentència `while`, de tal manera que:
1. Primer s'executen les instruccions que hi ha abans del `while` (bloc 1); en algun punt d'aquest conjunt d'instruccions s'hauran d'**inicialitzar els valors de les variables que afecten la condició** del `while`
2. A continuació s'avalua la condició del `while`, la qual serà `true` o `false`
3. Si la condició és `true` s'executa el bloc de codi de dins del `while` (bloc 2), el qual haurà d'**actualitzar les variables de la condició** en algun moment, i, un cop executat, es torna al capdamunt del `while` per tornar a avaluar la condició (es torna al pas 2)
4. Si la condició és `false` el `while` s'acaba i s'executen les instruccions que hi ha a continuació (bloc 3)

![Figura 6.1: diagrama de flux de la sentència `while`](img/while_flowchart.png)

<div style="background-color: #f44336; color: #ffffff;">
    <span style="font-weight: bold">Important</span>: si les variables que afecten a la condició no estan ben inicialitzades i no s'actualitzen correctament es crearà un <code>while</code> infinit, per tant, cal anar amb molt de compte.
</div>