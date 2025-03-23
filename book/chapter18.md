# Excepcions
Les excepcions són un sistema de gestió d'errors que permeten tractar tant els problemes derivats d'incorreccions en el codi com provocats per la interacció amb l'usuari o el *hardware*.

Així doncs, quan el codi d'un programa provoca un error, la seva execució s'atura i llença una `Exception` (excepció) amb tota la informació necessària per detectar el problema i, en cas que es pugui, solucionar-lo sense necessitat d'aturar, de manera definitiva, el programa.

D'excepcions n'hi ha de dos tipus (vegeu la Figura 18.1):
* *Unchecked exceptions*: són aquelles excepcions que no es poden comprovar prèviament, en temps de compilació. És a dir, l'error que les ocasiona només es pot comprovar en temps d'execució, quan realment succeeix. Totes elles són subclasses de `RuntimeException` i sempre estan provocades per errors de programació, per tant, no es poden gestionar per evitar que el programa el tanqui sobtadament i només es poden solucionar arreglant el codi que les ocasiona.
Exemples: `ArrayIndexOutOfBoundException`, `NullPointerException`
* *Checked exceptions*: són aquelles excepcions que es poden comprovar prèviament, en temps de compilació. Dit d'altra manera, són excepcions que es poden preveure ja que són provocades per factors externs (sistema de fitxers, *hardware*, bases de dades, etc.) i, per tant, poden ser tractades per evitar que el programa es tanqui sobtadament.
Exemples: `IOException`, `SQLException`, `FileNotFoundException`

![Figura 18.1: jerarquia de la família `Exeption`](img/exceptions.png)

Així doncs, les excepcions que s'han d'aprendre a gestionar són les *checked exceptions*

## Gestió de les *Checked Exceptions*
La gestió d'una *checked exception* es pot fer de dues maneres:
1. Delegant
2. Capturant

### Delegació d'excepcions: instrucció `throws`
Quan un mètode (funció o procediment) pot provocar una excepció, es pot decidir no fer-ne el tractament directament dins d'aquest mètode, sinó delegar-ne la seva gestió a la funció o procediment que l'ha cridat. Per fer-ho es necessita utilitzar la instrucció `throws`.

Per exemple, la Figura 18.2 mostra com el programa `main` crida un procediment de lectura de fitxer, la qual pot provocar una excepció de tipus `FileNotFoundException` i una altra de tius `IOException`. Per fer que el seu tractament sigui delegat al `main`, el procediment `readFile()` indica que pot llençar (`throws`) aquests tipus d'excepcions.

{% code title="Figura 18.2: delegació del tractament de les excepcions `FileNorFoundException` i `IOException` dins del mètode `readFile()" overflow="wrap" lineNumbers="true" %}
```java
public static void main() {
    String filename = "...";
    readFile(filename);
}

public static void readFile(String filename) throws FileNotFoundException, IOException {
    //Codi de lectura de fitxer que pot llençar les excepcions
}
```
{% endcode %}

En el moment en què el procediment `readFile()` decideix delegar el tractament de les excepcions, és qüestió del nivell superior, en aquest cas el `main`, decidir si continua delegant o si en fa la gestió final. Si el nivell superior continua delegant, tal com mostra la Figura 18.3, les excepcions aniran ascendint pel sistema de crides fins que algú les tracti o arribin al *terminal* que ha executat el programa, fent que la seva execució finalitzi sobtadament per l'error.

{% code title="Figura 18.3: delegació del tractament de les excepcions `FileNorFoundException` i `IOException` fins a l'últim nivell, fent que el programa s'aturi sobtadament" overflow="wrap" lineNumbers="true" %}
```java
public static void main() throws FileNotFoundException, IOException {
    String filename = "...";
    readFile(filename);
}

public static void readFile(String filename) throws FileNotFoundException, IOException {
    //Codi de lectura de fitxer que pot llençar les excepcions
}
```
{% endcode %}


### Captura d'excepcions: bloc d'instruccions `try-catch-finally`
Per poder capturar una excepció i fer-ne el tractament s'ha d'utilitzar el bloc d'instruccions `try-catch-finally`, el qual té l'estructura bàsica següet:

{% code title="Figura 18.4: estructura bàsica del bloc d'instruccions `try-catch-finally`" overflow="wrap" lineNumbers="true" %}
```java
try {
    //Codi que pot provocar excepcions
} catch(ExceptionType exceptionVariableName) {
    //Tractament de l'excepció
} finally {
    //Codi que es desitja executar tant si s'ha llençat l'excepció com si no
}
```
{% endcode %}

Així doncs, quan es detecta que part del codi d'un mètode (funció o procediment) pot provocar una excepció, aquest codi, i tot el que en depèn, es tanca dins del bloc `try`. A continuació es posen tants blocs `catch` com excepcions s'hagin de capturar. Finalment, i només si es desitja, es prepara un bloc `finally` per implementar tot aquell codi que es vol executar tant si es llença alguna excepció com si no (aquest bloc no és obligatori).

Si alguna de les instruccions del bloc `try` provoca alguna de les excepcions capturades en els blocs `catch`, s'atura l'execució del codi del `try` i es passa a executar el codi del `catch` corresponent. Un cop finalitzat el `catch`, s'executa el bloc `finally` (en cas que existeixi) i, finalment, el codi que hi ha tot just a sota del `try-catch-finally`.

Tal com mostra la Figura 18.4, el bloc `catch` necessita declarar una variable del tipus de l'excepció que es vol capturar dins de la seva zona de parèntesis.

La Figura 18.5 mostra un exemple de la gestió d'una de les excepcions que poden succeir durant la lectura d'un fitxer utilitzant només el `try` i el `catch`.

{% code title="Figura 18.5: exemplificació del bloc d'instruccions `try-catch-finally`" overflow="wrap" lineNumbers="true" %}
```java
try {
    FileReader freader = new FileReader(filename);
    BufferedReader breader = new BufferedReader(breader);

    //Lectura del fitxer

    breader.close();
} catch(IOException ioe) {
    System.out.println("S'ha produït un error de lectura/escriptura del fitxer " + filename);
}
```
{% endcode %}

Si es vol gestionar més d'una excepció dins d'un bloc `try` es pot fer de dues maneres:
1. Fent un bloc `catch` per capturar una excepció de tipus `Exception`
2. Posar tants blocs `catch` com excepcions es vulguin capturar

En el primer cas, com que `Exception` és la superclasse que fa de mare de qualsevol altre tipus d'excepció (vegeu la Figura 18.1), el bloc `catch` capturarà qualsevol excepció que esdevingui dins del bloc `try` al que estigui associat. El principal problema és que això no permet fer una gestió individualitzada per cadascuna de les excepcions que es puguin arribar a llençar (totes rebran exactament el mateix tractament).

En el segon cas, cada bloc `catch` capturarà i gestionarà de manera específica una determinada excepció. Ara però, cal tenir en compte que els blocs `catch` s'han d'ordenar per tal que capturin les excepcions començant per les més específiques i acabant amb les més generals. Això és degut al fet que quan el bloc `try` genera una excepció, aquesta es comparà amb el tipus de cada bloc `catch`, començant pel primer. Quan es troba un `catch` que coincideix amb l'excepció llençada, sigui perquè és exactament el mateix tipus o perquè és una de les seves superclasses, s'executa aquest bloc `catch` i, un cop executat, es passa al bloc `finally` (si existeix) i es finalitza el `try-catch-finally`.

Per exemple, la Figura 18.6 mostra un exemple on primer es captura `Exception` i després `IOException`. Com que `IOException` és filla d'`Exception`, el tratament específic per aquest tipus d'exepció no s'executarà mai perquè sempre s'entrarà al bloc `catch` d'`Exception`. El mateix passa a la Figura 18.7, on primer es caputra `IOException` i després ` FileNotFoundException`, que és filla d'`IOException`. En canvi, la Figura 18.8 mostra una ordenació dels blocs `catch`correcte, ja que respecta l'ordre d'especificitat de les excepcions capturades.

{% code title="Figura 18.6: exemplificació d'una mala ordenació dels blocs `catch`" overflow="wrap" lineNumbers="true" %}
```java
try {
    FileReader freader = new FileReader(filename);
    BufferedReader breader = new BufferedReader(breader);

    //Lectura del fitxer

    breader.close();
} catch(Exception e) {
    System.out.println("S'ha produït un error");
} catch(IOException ioe) {
    System.out.println("S'ha produït un error de lectura/escriptura del fitxer " + filename);
}
```
{% endcode %}

{% code title="Figura 18.7: exemplificació d'una mala ordenació dels blocs `catch`" overflow="wrap" lineNumbers="true" %}
```java
try {
    FileReader freader = new FileReader(filename);
    BufferedReader breader = new BufferedReader(breader);

    //Lectura del fitxer

    breader.close();
} catch(IOException ioe) {
    System.out.println("S'ha produït un error de lectura/escriptura del fitxer " + filename);
} catch(FileNotFoundException fnfe) {
    System.out.println("El fitxer " + filename + " no s'ha pogut trobar. Cal comprovar si la ruta és correcta");
} 
```
{% endcode %}

{% code title="Figura 18.8: exemplificació d'una bona ordenació dels blocs `catch`" overflow="wrap" lineNumbers="true" %}
```java
try {
    FileReader freader = new FileReader(filename);
    BufferedReader breader = new BufferedReader(breader);

    //Lectura del fitxer

    breader.close();
} catch(FileNotFoundException fnfe) {
    System.out.println("El fitxer " + filename + " no s'ha pogut trobar. Cal comprovar si la ruta és correcta");
} catch(IOException ioe) {
    System.out.println("S'ha produït un error de lectura/escriptura del fitxer " + filename);
}  
```
{% endcode %}

### Combinació de delegació i captura d'excepcions
En algun moment pot interessar que el mètode que provoca excepcions no les tracti directament, sinó que les delegui al nivell superior per tal que sigui aquest (o algun altre de més amunt) qui en faci la captura. La Figura 18.9 mostra com el procediment `readFile()` delega el tractament de les seves excepcions al `main`, el qual les haurà de capturar si desitja que el programa no finalitzi sobtadament.

{% code title="Figura 18.9: combinació de la delegació i de la captura d'excepcions" overflow="wrap" lineNumbers="true" %}
```java
public static void main() {
    String filename = "...";
    try {
        readFile(filename);
    } catch(FileNotFoundException fnfe) {
        System.out.println("El fitxer " + filename + " no s'ha pogut trobar. Cal comprovar si la ruta és correcta");
    } catch(IOException ioe) {
        System.out.println("S'ha produït un error de lectura/escriptura del fitxer " + filename);
    }  
}

public static void readFile(String filename) throws FileNotFoundException, IOException {
    FileReader freader = new FileReader(filename);
    BufferedReader breader = new BufferedReader(breader);

    //Lectura del fitxer

    breader.close();
}
```
{% endcode %}

## Mètodes bàsics de qualsevol excepció
En aquest apartat s'expliquen dos dels mètodes de la jerarquia `Exception` (comproveu l'API per poder veure totes les funcionalitats que ofereixen aquesta classe i les seves filles).

* `String getMessage()`: aquest metode retorna un `String` especificant l'error que s'ha produït (en anglès)
* `void printStackTrace()`: aquest mètode mostra per pantalla totes les crides que s'han executat i que han acabat provocant el llençament de l'excepció (molt útil per poder fer el resseguiment i la correcció de l'error, sobretot en el cas de les `RuntimeException`)

## Creació de noves excepcions
Cal tenir en compte que, en qualsevol moment, es pot ampliar la jerarquia `Exception` amb nous tipus d'excepcions creats per tal que els errors i els seus missatges s'adaptin millor als requeriments del programa.

Per fer-ho, només fa falta subclassificar (`extends`) la classe `Exception` (o qualsevol de les seves filles) i sobreescriure o ampliar els mètodes de la jerarquia que es creguin necessaris.

Si pensem en un programa per a la gestió de l'estoc d'una botiga, la Figura 18.10 mostra l'exemple de la creació de la nova excepció pensada per a ser llençada quan les unitats d'algun dels productes cauen per sota d'una certa quantitat.

{% code title="Figura 18.10: exemple de la creació d'una nova excepció personalitzada" overflow="wrap" lineNumbers="true" %}
```java
public class RestockException extends Exception {
    @Override
    public String getMessage() {
        return "Not enough product units. Restock is needed ";
    }
}
```
{% endcode %}