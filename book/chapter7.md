# Cadenes de caràcters: la classe `String`
El llenguatge Java ofereix la classe `String` per poder crear, manipular i tractar cadenes de caràcters. Aquestes cadenes poden estar formades per un únic caràcter *Unicode*, per una paraula, per una frase o per un tros de text fins i tot més llarg.

Per poder analitzar tota la informació i les operacions que es poden amb els `String` s'ha de consultar l'[API de Java](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html).

## Declarar i inicialitzar variables i constants de tipus `String`
La declaració i inicialització de variables i constants de tipus `String` es pot fer de múltiples maneres, sigui a partir de literals o a partir d'altres variables i constants.
```java
    String name1;                               //Declaració de la variable name1 de tipus String;
    String name2 = new String("M.Àngels");      /*Declaració i inicialització de la variable name2, de tipus String,
                                                    de la manera clàssica, utilitzant el constructor (no s'acostuma a fer servir)*/
    String name3 = "M.Àngels";                  /*Declaració i inicialització de la variable name3 amb
                                                    assignació directa de valor mitjançant un literal*/
    String name4 = name3;                       /*Declaració i inicialització de la variable name4 amb
                                                    assignació directa de valor mitjançant una altra variable*/
    String name5 = name4 + " Cerveró Abelló";   /*Declaració i inicialització de la variable name5 amb
                                                    assignació directa de valor mitjançant la concatenació
                                                    d'una variable i un literal*/
    final String COURSE1 = new String("DAM 1"); /*Declaració i inicialització de la constant COURSE1 de la manera clàssica,
                                                    utilitzant el constructor (no s'acostuma a fer servir)*/
    final String COURSE2 = "DAM 1";             /*Declaració i inicialització de la constant COURSE2 amb
                                                    assignació de valor mitjançant un literal*/
    final String COURSE3 = COURSE2;             /*Declaració i inicialització de la constant COURSE3 amb
                                                    assignació de valor mitjançant una altra constant*/
    final String COURSE4 = name3;               /*Declaració i inicialització de la constant COURSE4 amb
                                                    assignació de valor mitjançant una variable*/
```

## Comparació d'`String`
Per comparar dues variables o constants d'`String` no es poden utilitzar els operadors lògics d'igualtat (`==`, `<=`, `>=`) ni de diferència (`!=`, `<`, `>`), sinó que s'han d'utilitzar els mètodes de comparació que ofereix la classe `String`.

### Mètode `equals()`
El mètode [`equals()`](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#equals(java.lang.Object)) permet comparar per igualtat dues cadenes de caràcters.
```java
    boolean equals(Object obj);
```
Si les dues cadenes són idèntiques (mateixos caràcters, tenint en compte majúscules i minúscules) retorna `true`; si no, retorna `false` (encara que la diferència sigui d'un únic caràcter). Per poder comparar les dues variables (o constants) de tipus `String` `str1` i `str2` s'ha de fer de la manera següent: `str1.equals(str2)`. Per exemple:
```java
    str1.equals(str2);
    str2.equals(str1);

    /*Les dues sentències són equivalents; no importa quina variable
        s'utilitza primer, str1 o str2, ja que el resultat és el mateix*/
```

El codi següent mostra com s'utilitza el mètode:
```java
    String name1 = "M.Àngels";
    String name2 = "M.ÀNGELS";
    String name3 = "M.Àngels";
    String course1 = "\tDAM 1";
    String course2 = "DAM 1\n";
    String course3 = "\tDAM 1";
    String str1 = "Bon dia!";
    String str2 = "Bon dia, com esteu?";
    boolean areEquals;

    areEquals = name1.equals(name2);        /*Retornarà false
                                                (problema de majúscules minúscules)*/
    areEquals = name1.equals(name3);        //Retornarà true
    areEquals = course1.equals(course2);    //Retornarà false
    areEquals = course1.equals(course3);    //Retornarà true
    areEquals = str1.equals(str2);          //Retornarà false
```

### Mètode `equalsIgnoreCase()`
El mètode [`equalsIgnoreCase()`](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#equalsIgnoreCase(java.lang.String)) també permet comparar per igualtat dues cadenes de caràcters.
```java
    boolean equalsIgnoreCase(String str);
```
S'utilitza igual que el mètode `equals()`, és a dir, per poder comparar les dues variables (o constants) de tipus `String` `str1` i `str2` s'ha de fer de la manera següent: `str1.equalsIgnoreCase(str2)`;
```java
    str1.equalsIgnoreCase(str2);
    str2.equalsIgnoreCase(str1);

    /*Les dues sentències són equivalents; no importa quina variable
        s'utilitza primer, str1 o str2, ja que el resultat és el mateix*/
```
Ara però, al contrari que el mètode `equals()`, l'`equalsIgnoreCase()` no té en compte les majúscules i minúscules. Per exemple:
El codi següent mostra com s'utilitza el mètode:
```java
    String name1 = "M.Àngels";
    String name2 = "M.ÀNGELS";
    String name3 = "M.Àngels";
    String course1 = "\tDAM 1";
    String course2 = "DAM 1\n";
    String course3 = "\tDAM 1";
    String course4 = "\tdam 1";
    String str1 = "Bon dia!";
    String str2 = "Bon dia, com esteu?";
    boolean areEquals;

    areEquals = name1.equals(name2);        /*Retornarà true
                                                (ignora majúscules i minúscules)*/
    areEquals = name1.equals(name3);        //Retornarà true
    areEquals = course1.equals(course2);    //Retornarà false
    areEquals = course1.equals(course3);    //Retornarà true
    areEquals = course1.equals(course4);    //Retornarà true
    areEquals = str1.equals(str2);          //Retornarà false
```

### Mètode `regionMatches()`
El mètode `regionMatches()` permet comparar per igualtat fragments de dues cadenes de caràcters (no fa falta comparar les cadenes de principi a final). Aquest mètode té dues *sobrecàrregues*, segons si es vol comparar els fragments tenint en compte les majúscules i minúscules o no:
* [`reginMatches()` sobrecàrrega 1](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#regionMatches(int,java.lang.String,int,int))
* [`reginMatches()` sobrecàrrega 2](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#regionMatches(boolean,int,java.lang.String,int,int))
```java
    boolean regionMatches(int toffset, String str, int ooffset, int length);                        //Case-sensitive
    boolean regionMatches(boolean ignoreCase, int toffset, String str, int ooffset, int length);
```
Per poder comparar fragments de dues variables (o constants) de tipus `String` `str1` i `str2` s'ha de fer de la manera següent: `str1.regionMatches(parameters)`.

Explicació dels paràmetres:
* `toffset`: posició de la cadena `str1` on comença el fragment que volem comparar
* `ooffset`: posició de la cadena `str2` on comença el fragment que volem comparar
* `length`: llargada del segment que volem comparar (número de caràcters que té el fragment)
* `ignoreCase`: indica si volem que el mètode tingui en compte majúscules i minúscules (`true`) o no (`false`)

El codi següent mostra com s'utilitzen el dos mètodes:
```java
    String name1 = "M.Àngels";
    String name2 = "M.ÀNGELS";
    String course1 = "\tDAM 1";
    String course2 = "DAM 1\n";
    String course3 = "\tdam 1";
    String str1 = "El meu gos és negre";
    String str2 = "Loki, el meu gos";
    boolean areEquals;

    areEquals = name1.equals(0, name2, 0, 3);               //Retornarà true
    areEquals = name1.equals(0, name2, 0, 5);               //Retornarà false
    areEquals = course1.equals(1, course2, 0, 5);           //Retornarà true
    areEquals = course1.equals(false, 0, course3, 0, 5);    //Retornarà true
    areEquals = course1.equals(true, 0, course3, 0, 5);     //Retornarà false
    areEquals = course1.equals(0, course3, 0, 5);           //Retornarà false
    areEquals = str1.equals(7, str2, 13, 3);                //Retornarà true
```

### Mètode `compareTo()`
El mètode [`compareTo()`](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#compareTo(java.lang.String)) compararà dues cadenes de caràcters (`String`) de manera alfabètica, és a dir, tenint en compte l'ordre que ocupen les lletres i caràcters dins de l'alfabet (o dins de la distribució *Unicode*).
```java
    int compareTo(String str);
```
Per comparar dues variables (o constants) de tipus `String` `str1` i `str2` s'ha de fer de la manera següent: `str1.compareTo(str2)`:
```java
    str1.compareTo(str2);
    str2.compareTo(str1);

    /*Les dues sentències són equivalents; no importa quina variable
        s'utilitza primer, str1 o str2, ja que el resultat és el mateix*/
```
i el mètode retornarà:
* 0 si `str1` i `str2` són exactament iguals (majúscules i minúscules incloses);
* un valor negatiu si `str1` és menor que `str2`, on `str1` és la variable que invoca el mètode de comparació i `str2` és la variable que es passa per paràmetre;
* un valor positiu si `str1` és major que `str2`.

Per saber si una cadena de caràcters és menor o major que una altra, el mètode `compareTo()` les analitza totes dues fins que troba el prier caràcter diferent. Un cop trobat, la cadena més petita serà la que tingui el caràcter que aparegui abans a l'alfabet. En cas que no hi hagi cap caràcter diferent, la cadena més petita és la que és més curta. Per exemple:
* *ord**e**nar* és més petita que *ord**i**nador* perquè la **e**, que és el primer caràcter diferent, va abans que la **i** dins l'alfabet.
* *ordena* és més petit que *ordenar* perquè és més curta (*ordena* té 6 caràcters, o lletres, i, en canvi, *ordenar* en té 7).

El codi següent mostra com s'utilitza el mètode (consulteu la Taula ASCII de la Figura 7.1):
```java
    String name1 = "M.Àngels";
    String name2 = "M.ÀNGELS";
    String course1 = "\tDAM 1";
    String course2 = "DAM 1\n";
    String course3 = "\tDAM 1";
    String str1 = "Bon dia";
    String str2 = "Bon dia Joan";
    int areEquals;

    areEquals = name1.compareTo(name2);        /*Retornarà un valor positiu
                                                (les minúscules van després de les majúscules a la taula ASCII )*/
    areEquals = course1.compareTo(course2);    /*Retornarà un valor negatiu
                                                (el símbol del tabulador va abans de les lletres a la taula ASCII)*/
    areEquals = course1.compareTo(course3);    //Retornarà 0
    areEquals = str1.compareTo(str2);          /*Retornarà un valor negatiu
                                                (str1 és més curta que str2)*/
```

![Figura 7.1: taula ASCII](img/ascii_table.png)

### Mètode `compareToIgnoreCase()`
El mètode [`compareToIgnoreCase()`](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#compareToIgnoreCase(java.lang.String)) funciona exactament igual que el mètode `compareTo()` però essent *non case-sensitive`, és a dir, per avaluar dos cadenes de caràcters no diferencia majúscules i minúscules.
```java
    int compareToIgnoreCase(String str);
```
S'utilitza igual que el mètode `compareTo()`, és a dir, per poder comparar les dues variables (o constants) de tipus `String` `str1` i `str2` s'ha de fer de la manera següent: `str1.compareToIgnoreCase(str2)`;
```java
    str1.compareToIgnoreCase(str2);
    str2.compareToIgnoreCase(str1);

    /*Les dues sentències són equivalents; no importa quina variable
        s'utilitza primer, str1 o str2, ja que el resultat és el mateix*/
```

El codi següent mostra com s'utilitza el mètode:
```java
    String name1 = "M.Àngels";
    String name2 = "M.ÀNGELS";
    String course1 = "\tDAM 1";
    String course2 = "DAM 1\n";
    String course3 = "\tDam 1";
    String str1 = "Bon dia";
    String str2 = "Bon dia Joan";
    int areEquals;

    areEquals = name1.compareTo(name2);        //Retornarà 0
    areEquals = course1.compareTo(course2);    /*Retornarà un valor negatiu
                                                (el símbol del tabulador va abans de les lletres a la taula ASCII)*/
    areEquals = course1.compareTo(course3);    //Retornarà 0
    areEquals = str1.compareTo(str2);          /*Retornarà un valor negatiu
                                                (str1 és més curta que str2)*/
```

## Obtenció de la longitud d'un `String`
Per saber la longitud (el nombre de caràcters) que té un `String` s'utilitza el mètode [`length()`](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#length()).
```java
    int length();
```
Per poder saber la longitud d'una variable (o constant) de tipus `String str` el mètode `length()`s'ha d'utilitzar de la manera següent:
```java
    str.length();
```

El codi següent mostra com s'utilitza el mètode:
```java
    String name = "M.Àngels";
    String str1 = " ";
    String str2 = "";
    String course = "\tDAM 1";
    int len;

    len = name.length();        //Retornarà 8
    len = str1.length();        //Retornarà 1
    len = str2.length();        //Retornarà 0
    len = course.length();      //Retornarà 6
```

## Obtenció de caràcters d'un `String`
Donada una variable (o constant) de tipus `String`, se'n pot consultar els caràcters individualment, segons la posició que ocupen, o obtenir-ne una subcadena, és a dir, un fragment, que comenci i acabi on es desitgi.

### Mètode `charAt()`
El mètode [`charAt()`](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#charAt(int)) permet obtenir el caràcter que hi ha en una posició concreta.
```java
    char charAt(int pos);
```
Si el valor del paràmetre `pos` és correcte, és a dir, és major o igual que 0 i menor que la longitud de la cadena que estem consultant, el mètode retorna el caràcter (`char`) que hi ha en aquella posició. En cas contrari llença l'excepció `IndexOutOfBoundsException` i el programa s'atura (provoca un error). Per poder obtenir el caràcter a la posició *X* d'una variable (o constant) de tipus `String str` s'ha de fer de la manera següent:
```java
    int pos = 0;
    str.equals(pos);
```

El codi següent mostra com s'utilitza el mètode:
```java
    String name = "M.Àngels";
    String course = "\tDAM 1";
    String str1 = "Bon dia!";
    char character;
    int pos = 0;

    character = name.charAt(2);         //Retornarà 'À'
    character = course.charAt(pos);     //Retornarà '\t'
    character = str.equals(3);          //Retornarà ' '
    character = str.equals(7);          //Retornarà '!'
    character = str.equals(8);          //Error!
```

### Mètode `codePointAt()`
El mètode [`codePointAt()`](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#codePointAt(int)) funciona exactament igual que el mètode `charAt()` però, en comptes de retornar el caràcter que hi ha en una posició concreta en format `char`, retorna el codi ASCII d'aquest caràcter, és a dir, un `int`.
```java
    int codePointAt(int pos);
```
Si el valor del paràmetre `pos` és correcte, és a dir, és major o igual que 0 i menor que la longitud de la cadena que estem consultant, el mètode retorna el codi ASCII del caràcter (`int`) que hi ha en aquella posició. En cas contrari llença l'excepció `IndexOutOfBoundsException` i el programa s'atura (provoca un error). Per poder obtenir el codi ASCII caràcter a la posició *X* d'una variable (o constant) de tipus `String str` s'ha de fer de la manera següent:
```java
    int pos = 0;
    str.codePointAt(pos);
```

El codi següent mostra com s'utilitza el mètode (consulteu la Taula ASCII de la Figura 7.1 i els caràcters de la Taula UNICODE parcial de la Figura 7.2):
```java
    String name = "M.Àngels";
    String course = "\tDAM 1";
    String str1 = "Bon dia!";
    char character;
    int pos = 0;

    character = name.charAt(2);         //Retornarà 192
    character = course.charAt(pos);     //Retornarà 9
    character = str.equals(3);          //Retornarà 32
    character = str.equals(7);          //Retornarà 33
    character = str.equals(8);          //Error!
```
![Figura 7.2: taula UNICODE parcial](img/iso_8859_1.png)

### Mètode `substring()`
El mètode `substring()` permet obtenir una subcadena (un fragment) de la cadena de caràcters que s'estigui avaluant. Aquest mètode té dues *sobrecàrregues*:
* [`substring()` sobrecàrrega 1](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#substring(int))
* [`substring()` sobrecàrrega 2](https://docs.oracle.com/en/java/javase/23/docs/api/java.base/java/lang/String.html#substring(int,int))
```java
    String substring(int iniPos);
    String substring(int iniPos, int endPos);
```
Per poder obtenir una subcadena d'una variable (o constant) de tipus `String str` s'ha de fer de la manera següent: `str.substring(parameters)`.

Explicació dels paràmetres:
* `iniPos`: posició de la cadena `str` on comença el fragment que volem obtenir
* `endPos`: posició de la cadena `str` on acaba el fragment que volem obtenir

En la primera sobrecàrrega del mètode (`String substring(int iniPos)`), com que no s'indica la posició final, el fragment que s'obtè va des de la posició inicial indicada fins al final de la cadena `str`. En canvi, en la segona sobrecàrrega (`String substring(int iniPos, int endPos)`) el fragment va des de la posició inicial fins a la posició final -1 (la posició final és excloent).

Cal tenir en compte que si qualsevol dels paràmetres és incorrecte, és a dir, les posicions indicades són negatives o superiors a la llargada de la cadena original o la posició inicial és més gran que la final, els mètodes llençaran l'excepció `IndexOutOfBoundsException`.

El codi següent mostra com s'utilitzen el dos mètodes:
```java
    String name = "M.Àngels";
    String str1 = "El meu gos és negre";
    String str2 = "Loki, el meu gos";
    String fragment;
    int iniPos = 0, endPos = 4;

    fragment = name.substring(2);                       //Retornarà "Àngels"
    fragment = name.substring(-2);                      //Error!
    fragment = str1.equals(iniPos, 10);                 //Retornarà "El meu gos"
    fragment = str2.substring(iniPos, endPos);          //Retornarà "Loki"
    fragment = str2.substring(endPos, iniPos);          //Error!
    fragment = str2.substring(0, str.length() + 10);    //Error!
```
