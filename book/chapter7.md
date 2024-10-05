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

    //Les dues sentències són equivalents; no importa quina variable s'utilitza primer, str1 o str2, ja que el resultat és el mateix
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

    areEquals = name1.equals(name2);        //Retornarà false (problema de majúscules minúscules)
    areEquals = name1.equals(name3);        //Retornarà true
    areEquals = course1.equals(course2);    //Retornarà false
    areEquals = course1.equals(course3);    //Retornarà true
    areEquals = str1.equals(str2);          //Retornarà false
```