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

<!-- Notació Gitbook per poder fer blocs ressaltats-->
{% hint style="danger" %}
**Important:** si les variables que afecten a la condició no estan ben inicialitzades i no s'actualitzen correctament es crearà un `while` infinit, per tant, cal anar amb molt de compte.
{% endhint %}

## Sentència `do-while`
La sentència `do-while` és molt similar a la sentència `while` i només difereix en com avalua la condició:
* en el cas del `while` primer s'avalua la condició i, segons el resultat, s'executa, o no, el bloc de codi intern;
* en canvi, en el cas del `do-while`, primer s'executa el bloc de codi intern i, després, s'avalua la condició de tal manera que, si aquesta és certa, es torna a executar el bloc de codi.

Així doncs, podem dir que en el `do-while` el bloc de codi intern sempre s'executa, com a mínim, una vegada.

L'estructura de la sentència `do-while` és la següent:
```java
    do {
        //Bloc de codi que volem executar (i anar repetint); com a mínim s'executa sempre una vegada
    }
    while(condition);
```

La Figura 6.2 mostra el diagrama de flux corresponent a la sentència `do-while`, de tal manera que:
1. Primer s'executen les instruccions que hi ha abans del `do-while` (bloc 1);
2. A continuació s'executa el bloc de codi intern del `do-while` (bloc 2), el qual haurà d'**actualitzar el valor de les variables de la condició** en algun moment
3. Un cop executat el codi, s'avalua la condició del `do-while`
4. Si la condició és `true` es tornen a executar les instruccions internes del `do-while` (bloc 2), és a dir, es torna al pas 2
5. Si la condició és `false`, el `do-while` acaba i s'executa el codi que hi ha a continuació (bloc 3)

![Figura 6.2: diagrama de flux de la sentència `do-while`](img/dowhile_flowchart.png)

## Sentència `for`
En els dos apartats anteriors s'ha vist que les sentències `while` i `do-while` gestionen el nombre d'iteracions (voltes) que fa el bucle mitjançant una condició general, més o menys complexa. La sentència `for`, en canvi, s'utilitza molt quan hi ha un *comptador* de voltes, és a dir, d'alguna manera se sap quantes iteracions s'han de fer, sigui perquè és un nombre fixe o perquè hi ha una variable que les comptabilitza.

L'estructura de la sentència `for` és la següent
```java
    for(initialization; condition; update) {
        //Bloc de codi que volem executar (i anar repetint)
    }
```
on:
`initialization`: inicialitza les variables que afecten la condició; si la inicialització té múltiples instruccions, aquestes se separen per coma (,)
`condition`: és la condició que permet entrar dins del bloc de codi del `for` (en cas que s'avaluï `true`); la condició s'avalua **abans de cada iteració**
`update`: instruccions que actualitzen el valor de les variables que afecten la condició; si hi ha múltiples instruccions, aquestes se separen per coma (,); l'actualització s'executa al **final de cada iteració**