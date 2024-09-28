# Control de flux condicional
En el [Capítol 1](chapter1.md) s'ha explicat que un programa (algorisme) s'executa de manera seqüencial, instrucció rera instrucció. No obstant això, hi ha certs tipus d'instruccions que permeten executar, o no, un tros de codi (o bloc de codi), depenent de si una determinada condició es compleix o no.

Aquest tipus d'instruccions es coneixen com a **control de flux condicional** i n'hi ha de tres tipus:
1. condicional simple;
2. condicional doble i
3. condicional múltiple.

## Condicional simple
La sentència `if` permet crear un condicional simple, de tal manera que defineix un bloc de codi que només s'executa si una determinada condició es compleix, és a dir, la condició s'avalua a `true`.

L'estructura de la sentència `if` és la següent:
```java
    if(condition) {
        //Bloc de codi que volem executar si condition és true
    }
```

La Figura 5.1 mostra el diagrama de flux corresponent a la sentència `if`, de tal manera que:
1. Primer s'executen les instruccions que hi ha abans de l'`if` (bloc 1)
2. A continuació s'avalua la condició de l'`if`, la qual serà `true` o `false`
3. Si la condició és `true` s'executa el bloc de codi de dins de l'`if` (bloc 2) i, un cop executat, es continua executant les instruccions que hi ha després de l'`if` (bloc 3)
4. Si la condició és `false` s'executen, directament, les instruccions que hi ha després de l'`if` (bloc 3), és a dir, el bloc intern de l'`if` (bloc 2) no s'executa mai

![Figura 5.1: diagrama de flux de la sentència `if`](img/if_flowchart.png)

## Condicional doble
La sentència `if-else` permet crear un bloc de codi que s'executa si una determinada condició es compleix (és `true`) i un altre bloc de codi que s'executa si aquesta mateixa condició no es compleix (és `false`).

L'estructura de la sentència `if-else` és la següent:
```java
    if(condition) {
        //Bloc de codi que volem executar si condition és true
    } else {
        //Bloc de codi que volem executar si la condition és false
    }
```

La Figura 5.2 mostra el diagrama de flux corresponent a la sentència `if-else`, de tal manera que:
1. Primer s'executen les instruccions que hi ha abans de l'`if` (bloc 1)
2. A continuació s'avalua la condició de l'`if`, la qual serà `true` o `false`
3. Si la condició és `true` s'executa el bloc de codi de dins de l'`if` (bloc 2) i, un cop executat, es continua executant les instruccions que hi ha després de l'`if-else` (bloc 4)
4. Si la condició és `false` s'executa el bloc de codi de dins de l'`else` (bloc 3) i, un cop executat, es continua executant les instruccions que hi ha després de l'`if-else` (bloc 4)

![Figura 5.2: diagrama de flux de la sentència `if-else`](img/ifelse_flowchart.png)

## Condicional múltiple
Per poder crear condicionals múltiples, és a dir, que puguin avaluar múltiples condicions i executar certs blocs de codi segons si aquestes són `true` o `false`, existeixen dues sentències: `if-else if-else` i `switch-case`.

### Sentència `if-else if-else`
L'estructura de la sentència `if-else if-else` és la següent:
```java
    if(condition1) {
        //Bloc de codi que volem executar si condition1 és true
    } else if(condition2) {
        //Bloc de codi que volem executar si
        //  1. la condition1 és false i
        //  2. la condition2 és true
    } else if(condition3) {
        //Bloc de codi que volem executar si
        //  1. la condition1 és false,
        //  2. la condition2 és flase i
        //  3. la condition3 és true
    } 
    .
    .
    .
    else {
        //Bloc de codi que volem executar si totes les conditions són false
    }
```

La Figura 5.3 mostra el diagrama de flux corresponent a la sentència `if-else if-else` amb dos `else if`, de tal manera que:
1. Primer s'executen les instruccions que hi ha abans de l'`if` (bloc 1)
2. A continuació s'avalua la `condition1` de l'`if`, la qual serà `true` o `false`
3. Si la condició és `true` s'executa el bloc de codi de dins de l'`if` (bloc 2) i, un cop executat, es continua executant les instruccions que hi ha després de l'`if-else if-else` (bloc 6)
4. Si la condició és `false` s'avalua la `condition2` del primer `if else`; si és `true` s'executa el bloc de codi de dins d'aquest `if else` (bloc 3) i, un cop executat, es continua executant les instruccions que hi ha després de l'`if-else if-else` (bloc 6)
5. Si `condition2` és `false`, s'avaula la `condition3` del segon `if else`; si és `true` s'executa el bloc de codi dins d'aquest segon `if else` (bloc 4) i, un cop executat, es continua executant les instruccions que hi ha després de l'`if-else if-else` (bloc 6)
6. Si `condition3` també és `false` s'executa el codi dins de l'`else` (bloc 5) i, un cop executat, es continua executant les instruccions que hi ha després de l'`if-else if-else` (bloc 6)

![Figura 5.3: diagrama de flux de la sentència `if--else if-else`](img/multipleif_flowchart.png)

**Detalls que cal tenir en compte**
Les múltiples sentències `if-else if-else` són depenents entre elles, això vol dir que, tan aviat una de les condicions és certa (`true`) i s'executa el codi corresponent, la resta de condicions ja no s'avaluen i el flux d'execució surt de la sentència per continuar executar el codi que hi ha a sota de l'`if-else if-else`.

Si fem el mateix codi, però en comptes d'utilitzar la sentència `ìf-else if-else` utilitzem múltiples `if` simples, aconseguirem el mateix resultat, però com que els `if` simples són independents els uns dels altres, totes les condicions s'hauran d'avaluar sí o sí i, per tant, el codi serà més ineficient.

Per exemple, en el codi següent
```java
1   int num=10;
2   if(num>0 && num<=10) {
3       System.out.println("Primera desena"); 
4   } else if(num>10 && num<=20) {
5       System.out.println("Segona desena");
6   } else if(num>20 && num<=30) {
7       System.out.println("Tercera desena"); 
8   } else {
9       System.out.println("Quarta desena o superior"); 
10  }
11  System.out.println("Finalització del programa");
}
```
com que la condició de l'`if` de la línia 2 és certa, s'executen les línies 3 i 11, de tal manera que les línies que van de la 4 a la 10 s'ignoren completament. En canvi, en el codi 
```java
1   int num=10;
2   if(num>0 && num<=10) {
3       System.out.println("Primera desena"); 
4   } 
5   if(num>10 && num<=20) {
6       System.out.println("Segona desena");
7   }
8   if(num>20 && num<=30) {
9       System.out.println("Tercera desena"); 
10  }
11  if(num>30) {}
12       System.out.println("Quarta desena o superior"); 
13  }
14  System.out.println("Finalització del programa");
}
```
tot i que la condició del l'`if` de la línia 2 sigui certa, la resta siguin falses i el resultat per pantalla sigui el mateix, l'ordinador ha d'avaluar totes i cadascuna de les condicions de manera independent, per tant, no pot ignorar el codi que va de la línia 5 a la 13.

### Sentència `switch-case`
La sentència `switch-case` permet crear un flux condicional múltiple on les condicions que s'avaluen sempre són d'igualtat, és a dir, mitjançant l'operador `==`.