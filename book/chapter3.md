# Constants
Tal com s'ha explicat en el [Capítol 1](chapter1.md), una constant permet crear i definir dades dins del nostre algorisme, de tal manera que aquestes dades **no** podran variar en cap moment, és a dir, tal com el seu nom indica, seran valors **constants**.

Per poder crear (**declarar**) una constant necessitem
1. marcar-la com a `final` (paraula reservada del llenguatge Java que serveix per declarar les constants);
2. definir-ne el tipus de dades, és a dir, quines dades podrà emmagatzemar
3. definir un nom (identificador) que ens permeti referenciar-la i utilitzar-la i 
4. assignar-li el valor que tindrà.
```
    final tipus_dades NOM_CONSTANT = valor;
```
Un cop declarada, ja la podrem utilitzar.

## Tipus de dades
Les constants poden ser dels mateixos tipus que les variables, per tant, podeu analitzar el [Capítol 2](chapter2.md#tipus-de-dades) per saber quins tipus de dades existeixen en el llenguatge Java.

## Normes que han de complir els identificadors (noms)
Els noms de les constants han de complir les mateixes 7 normes bàsiques que els noms de les variables (vegeu el [Captíol 2](chapter2.md#normes-que-han-de-complir-els-identificadors-noms)), a excepció de la norma 6, ja que el nom de les constants s'ha d'escriure tot en majúscules. Així doncs, la nova norma 6 queda redactada de la manera següent
1. Sempre s'han d'escriure en majúscula; per separar les diverses paraules que la component es pot utilitzar el subguió. Per exemple:
```java
  final float PI = 3.1416f;
  final String HIGH_SCHOOL_NAME = "Institut Caparrella";    //Separació de les paraules amb subguions
  final String HIGHSCHOOLNAME = "Institut Caparrella";      //Sense separació entre les paraules
```

## Exemplificació de la declaració i ús de constants
El següent tros de codi mostra diversos exemples de creació i ús de constants
```java
  final float PI = 3.1416f;                                     //Declaració d'una constant per emmagatzemar el valor del nombre PI
  final String NAME = "M.Àngels", SURNAME = "Cerveró Abelló";   //Declaració de dos (o més) constants del mateix tipus en una sola instrucció
  float radius = 3.0f, perimetre;                               //Declaració de variables
  final float RADIUS = radius;                                  //Declaració d'una constant, tot assignant-li el valor contingut en una variable

  perimetre = 2 * PI * RADIUS;                                  //Càlculs utilitzant constants
  perimetre = 2 * PI * radius;                                  //Càlculs utilitzant constants i variables
```