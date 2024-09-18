# Conceptes bàsics

## Què és un algorisme?
Programar significa resoldre problemes creant, o implementant, algorismes. Un **algorisme** és un conjunt ordenat i finit d'operacions o instruccions que s'executen de manera seqüencial (en ordre, una darrera de l'altra) i que permeten trobar la solució d'un problema.

## Característiques d'un algorisme
Tot algorisme té 8 característiques desitjables i, tot i que en alguns casos alguna d'elles es difícil d'aconseguir complir, tot programador ha d'intentar buscar aquella solució que n'assoleixi el màxim possible.

* **Efectiu**: tot algorisme ha de donar resposta al problema que intenta solucionar.
* **Clar i documentat**: el codi ha de ser clar i documentat per facilitar-ne el manteniment i les possibles ampliacions i adaptacions.
* **Eficient**: l'execució ha de ser ràpida, aprofitant al màxim els recursos del dispositius on s'executa.
* **Robust**: ha de donar solució, siguin quins siguins els paràmetres d'entrada; a més a més, donats uns mateixos paràmetres sempre ha de retornar la mateixa solució.
* **Fiable**: els resultats han de ser precisos.
* **Transportable**: s'ha de poder executar en diferents dispositius, sense importar la diferència de hardware ni de sistema operatiu.
* **Interacció**: ha de realitzar una bona interacció amb l'usuari, amb missatges clars i una bona interfície d'usuari, sigui gràfica o mitjançant un terminal.

## Estructura d'un algorisme
Un algorisme està format per tres elements:
* Dades
* Expressions
* Instruccions

### Dades
Les dades són el conjunt d'informació que cal tractar i poden ser:
* Simples
  * Numèriques: per fer operacions aritmètiques
    * Enters
    * Reals
  * No numèriques
    * Caràcters: alfanumèrics, especials i cadenes de caràcters
    * Booleanes (lògiques)
* Estructures de dades
  * Internes
    * Estàtiques
      * *Arrays*
      * Matrius
    * Dinàmiques
      * Llistes, cues i piles
      * Conjunts
      * Diccionaris
      * Àrbres
  * Externes
    * Fitxers
    * Bases de dades

### Expressions
Les expressions són les operacions que es realitzen sobre les dades i estan formades per:
* Operands: són les dades que es volen operar
  * Literals: dades en cru
  ```java
    3;
    'a';
  ```
  * Constants: valor inalterable, és a dir, l'algorisme no les pot modificar de cap manera. Es defineixen indicant el tipus de dada que es vol, el nom que s'utilitzarà per accedir-hi i el valor. Poden ser numèriques, alfabètiques, alfanumèriques o estructures més complexes.
  ```java
    final int NUM_TEACHERS = 28;
  ```
  * Variables: el seu valor es pot alterar durant l'execició del programa. Es defineixen indicant el tipus de dada que es vol, el nom que s'utilitzarà per accedir-hi i el seu valor inicial. Poden ser numèriques, alfabètiques, alfanumèriques o estructures més complexes.
  ```java
    char vowel = 'a';
  ```
* Operadors: són les operacions que s'executen sobre les dades
  * Assignació: permet assignar un valor a una dada en concret (=)
  ```java
    int num;
    num = 2;
  ```
  * Aritmètics: representen les operacions bàsiques de suma (+), resta (-), multiplicació (*), divisió (/), mòdul (% o mod) i exponenciació (^)
  ```java
    int num1 = 3
    int num2 = 4;
    int num;

    num = num1 * num2;
  ```
  * Alfanumèrics: operació bàsica de concatenació (+)
  ```java
    String name = "M.Àngels";
    String surname = "Cerveró Abelló";
    String completeName;

    completeName = name + surname;
  ```
  * Relacionals o condicionals: permeten elaborar operacions de condició per consultar l'estat de les dades. Les condicions que es poden consultar són la d'igualtat (==), diferència (!=), menor que (<), major que (>), menor o igual que (<=) i major o igual que (>=)
  ```java
    int num1 = 3;
    int num2 = 4;
    boolean result;

    result = num1 == num2;
    result = num1 <= num2;
  ```
  * Parèntesis: estableixen prioritat, és a dir, quines operacions es fan abans que unes altres
  ```java
    int num1 = 3;
    int num2 = 4;
    boolean result;

    result = (num1 == num2);
    result = (num1 <= num2);
  ```
  * Lògics: són les operacions NOT (!), AND bit a bit (&), OR bit a bit (|), AND condicional (&&) i OR condicional (||).
  ```java
    int num1 = 3;
    int num2 = 4;
    int num3;
    boolean resultat;

    num2 = num1 & num2;
    resultat = num1 == num2 || num1 < num2;
  ```

### Instruccions
Les instruccions estan formades per un conjunt de dades i d'operacions (expressions) i defineixen el comportament de l'algorisme, és a dir, els còmputs que ha de fer per arribar a una solució.
* Instruccions simples:
  * Comentaris: permeten afegir explicacions al codi sense alterar-ne la seva execució ja que, en el moment de crear l'executable, aquests comentaris desapareixen. Poden ser d'una sola línia o multilínia
  ```java
    // Aquest és un comentari d'una sola línia
    /* 
      Aquest comentari
      conté dos línies
    */
    /**
     * Aquest comentari
     * també és multilínia
     */
  ```
  * Declaratives: permeten definir constants i variables
  ```java
    /**
     * Declaració d'una constan
     * (recordeu que en el mateix moment en què es declara una constant també se li ha d'assignar el valor que tindrà)
     */
    final int COURS_DURATION = 2000;

    //Declaració d'una variable
    int numStudents;
  ```
  * Primitives: són les instruccions més bàsiques que ens permeten interactuar amb l'usuari i assignar valors a les nostres dades (variables i constants):
    * Instruccions d'entrada i de sortida (E/S): són les que ens permeten introduir i extreure dades del sistema. Les instruccions E/S més bàsiques gestionen el teclat (entrada de dades) i la pantalla (sortida de dades) i les més complexes treballen amb fitxers, bases de dades i sistemes més elaborats.
    ```java
    //Instrucció per llegir un valor enter des de teclat
    Scanner keyboard = new Scanner(System.in);
    int value;
    value = keyboard.nextInt();

    //Instrucció per mostrar per pantalla un valor enter
    System.out.println(value);
    ```
    * Assignació: permet donar valor a una variable o a una constant i utiltiza l'operador *igual* (=)
    ```java
    //Declaració d'una variable
    int value;
    //Assignació del valor de la variable
    value = 3;

    //Declaració i assignació d'una variable en una sola línia
    int num = 4;
    ```
  * Control de fluxe: com ja sabem, el codi d'un algorisme s'executa de manera seqüencial, línia de codi rera línia de codi. Les instruccions de control de fluxe ens permeten variar aquesta execució per tal de poder executar, o no, un tros de codi segons si una condició es compleix o no; poder repetir un tros de codi múltiples vegades, etc.
    * Control de fluxe condicional (alternatiu): permet decidir si un tros de codi determinat s'executa o no depenent de si una condició es compleix. El control de fluxe condicional pot ser
      * simple (`if`),
      * doble (`if-else`) o
      * múltiple (`if-else if-else` i `switch-case`)
    * Control de fluxe iteratiu (repetitiu): permet repetir un tros de codi mentre una determinada condició es compleix. Existeixen diverses instruccions iteratives: `while`, `do-while`, `for` i `for-each`.
* Instruccions compostes: són un conjunt d'instruccions simples agrupades en **funcions**