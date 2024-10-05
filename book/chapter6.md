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
En els dos apartats anteriors s'ha vist que les sentències `while` i `do-while` gestionen el nombre d'iteracions (voltes) que fa el bucle mitjançant una condició general, més o menys complexa. La sentència `for`, en canvi, s'utilitza quan hi ha un *comptador* de voltes, és a dir, d'alguna manera se sap quantes iteracions s'han de fer, sigui perquè és un nombre fixe o perquè hi ha una variable que les comptabilitza. Per exemple, comptar el nombre d'elements dins d'una estructura de dades, mostrar seqüències de nombres, etc.

L'estructura de la sentència `for` és la següent
```java
    for(initialization; condition; update) {
        //Bloc de codi que volem executar (i anar repetint)
    }
```
on:
* `initialization`: inicialitza les variables que afecten la condició; si la inicialització té múltiples instruccions, aquestes se separen per coma (,)
* `condition`: és la condició que permet entrar dins del bloc de codi del `for` (en cas que s'avaluï `true`); la condició s'avalua **abans de cada iteració**
* `update`: instruccions que actualitzen el valor de les variables que afecten la condició; si hi ha múltiples instruccions, aquestes se separen per coma (,); l'actualització s'executa al **final de cada iteració**

La Figura 6.3 mostra el diagrama de flux corresponent a la sentència `for`, de tal manera que:
1. Primer s'executen les instruccions que hi ha abans del `for` (bloc 1);
2. A continuació s'inicialitzen les variables que gestionen el `for` (bloc 2)
3. S'avalua la condició del `for`, la qual serà `true` o `false`
4. Si la condició és `true` s'executa el bloc de codi de dins del `for` (bloc 3) i, immediatament, es realitza l'actualització de les variables (bloc 4); un cop executat tot plegat, es torna al capdamunt del `for` per tornar a avaluar la condició (es torna al pas 3)
5. Si la condició és `false` el `for` s'acaba i s'executen les instruccions que hi ha a continuació (bloc 5)

![Figura 6.3: diagrama de flux de la sentència `for`](img/for_flowchart.png)

## Trencament del flux iteratiu
Pot ser que, segons les necessitats de l'algorisme que s'està implementant, interessi finalitzar una sentència iterativa (un bucle) abans de temps. Per fer-ho, es poden utilitzar dues sentències:
* Sentència `break`: trenca completament l'execució del bucle i en surt totalment (presentada en el [Captítol 4](chapter4.md))
* Sentència `continue`: finalitza la iteració (volta) actual i continua amb la següent

Tot i que molts llenguatges de programació disposen d'aquestes dues sentències, tot flux iteratiu es pot implementar correctament sense utilitzar-les (treballant de manera adequada amb les condicions) i, per tant, molts programadors les eviten perquè trenquen la seqüència natural del codi i el fan més difícil de resseguir.

Per exemple, el codi següent mostra un molt mal ús de la sentència `break`
```java
    int counter = 0;
    while(counter <= 10) {
        System.out.println("Número " + counter);
        if(counter == 2) {
            break;
        }
        counter++;
    }
```
Com que la condició del `while` està mal plantejada s'ha hagut d'utilitzar el `break` per finalitzar el bucle a la 2a volta. El codi correcte, doncs, seria el següent:
```java
    int counter = 0;
    while(counter <= 2) {
        System.out.println("Número " + counter);
        counter++;
    }
```

El codi que es troba a continuació, que només mostra els números imparells, també és un exemple de mal ús de la sentència `continue`
```java
    int num = 0;
    while(num < 10) {
        if(num % 2 == 0) {
            continue;
        }
        System.out.println("Número " + num);
        num++;
    }
```
ja que, en aquest cas, la condició de l'`if` havia de ser la contraria:
```java
    int num = 0;
    while(num < 10) {
        if(num % 2 != 0) {
            System.out.println("Número " + num);
        }
        num++;
    }
```

{% hint style="warning" %}
**Important:** cal anar amb molt de compte amb l'ús de les sentències `break` i `continue`
{% endhint %}

## Blocs iteratius niats (blucles niats)
Tal com s'ha comentat al [Capítol 4](chapter4.md), dins d'un bloc de codi s'hi pot posar qualsevol tipus d'instrucció. En el cas dels bucles, podem posar-hi sentències condicionals a dins (per exemple, un `if`) i també hi podem posar altres bucles (per exemple, un `for` dins d'un altre `for`). Si posem dos o més bucles, un dins de l'altre, tenim el que s'anomena *bucles niats* i poden ser de dos tipus:
* Independents: quan les variables que controlen les condicions són completament diferents
* Dependents: quan les variables que controlen les condicions dels bucles externs també afecten a les condicions dels bucles interns

### Exemple de dos bucles niats independents
```java
    final int EXTERNAL_ITERS = 10;
    final int INTERNAL_ITERS = 4;
    for(int i=0; i<EXTERNAL_ITERS; i++) {
        System.out.println("for extern amb i = " + i);
        for(int j=0; j<INTERNAL_ITERS; j++) {
            System.out.println("for intern amb j = " + j);
            System.out.println("Volta total número " + (i * EXTERNAL_ITERS + j));
        }
    }
```
Aquestes dues sentències `for` niades són completament independents perquè estan gestionades per variables diferents que no s'afecten entre elles. És a dir, el `for` extern està gestionat per la variable `i` i el `for` intern està gestionat per la variable `j`, sense que `i` i `j` tinguin cap relació entre elles.

Si ens hi fixem, el `for` extern farà 10 voltes i, per cadascuna d'aquestes voltes, el `for` intern en farà 4. Per tant, el nombre total de voltes serà $$10 \cdot 4 = 40$$.

### Exemple de dos bucles niats dependents
```java
    final int EXTERNAL_ITERS = 10;
    for(int i=0; i<EXTERNAL_ITERS; i++) {
        System.out.println("for extern amb i = " + i);
        for(int j=0; j<=i; j++) {
            System.out.println("for intern amb j = " + j);
            System.out.println("Volta total número " + (i * EXTERNAL_ITERS + j));
        }
    }
```
Les dues sentències `for` que mostra el codi superior són dependents perquè, tot i estar gestionades per dues variables diferents, la variable del `for` extern (la `i`) afecta  la variable del `for` intern (la `j`) perquè defineix el valor màxim al que pot arribar. Així doncs, quan la `i` serà 0 el `for` intern només podrà fer 1 volta (`j == 0`); quan la `i` serà 1 el `for` intern podrà fer 2 voltes (`j == 0` i `j == 1`); quan la `i` serà 2 el `for` intern podrà fer 3 voltes (`j == 0`, `j == 1` i `j == 2`) i així successivament. Podem dir que, per cada volta del `for` extern, el `for` intern en pot fer tantes com marqui la `i` en aquell moment i el total de voltes serà $$1 + 2 + 3 + \dots + 10 = 55$$