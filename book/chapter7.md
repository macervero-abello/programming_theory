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
Si les dues cadenes són idèntiques (mateixos caràcters, tenint en compte majúscules i minúscules) retorna `true`; si no, retorna `false` (encara que la diferència sigui d'un únic caràcter). Per poder comparar les dues variables (o constants) de tipus `String` `str1` i `str2` s'ha de fer de la manera següent: `nom_variable1.equals(nom_variable2)`. Per exemple:
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
S'utilitza igual que el mètode `equals()`, és a dir, per poder comparar les dues variables (o constants) de tipus `String` `str1` i `str2` s'ha de fer de la manera següent: `nom_variable1.equalsIgnoreCase(nom_variable2)`;
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
Per poder comparar fragments de dues variables (o constants) de tipus `String` `str1` i `str2` s'ha de fer de la manera següent: `nom_variable1.regionMatches(parameters)`.

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
El mètode `compareTo()` compararà dues cadenes de caràcters (`String`) de manera alfabètica, és a dir, tenint en compte l'ordre que ocupen les lletres i caràcters dins de l'alfabet (o dins de la distribució *Unicode*).
```java
    int compareTo(String str);
```
Per comparar dues variables (o constants) de tipus `String` `str1` i `str2` s'ha de fer de la manera següent: `nom_variable1.compareTo(nom_variable2)`:
```java
    str1.compareTo(str2);
    str2.compareTo(str1);

    /*Les dues sentències són equivalents; no importa quina variable
        s'utilitza primer, str1 o str2, ja que el resultat és el mateix*/
```
i el mètode retornarà:
* 0 si `str1` i `str2` són iguals

### Mètode `compareToIgnoreCase()`
