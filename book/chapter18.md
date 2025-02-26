# Lectura i escriptura de fitxers de text
En el moment d'implementar un programa és molt important tenir en compte la **persistència de dades**, és a dir, la capacitat de poder-les emmagatzemar i recuperar en qualsevol moment. Per assolir aquest objectiu hi ha dues eines bàsiques: els fitxers i les bases de dades persistents.

Aquest capítol tracta la persistència de dades en fitxers a través de la seva lectura i escriptura.

## Fitxers de text
Entendrem com a *fitxer de text* qualsevol document que s'hagi escrit mitjançant un editor de text bàsic i que contingui text en pla, és a dir, sense cap mena de format enriquit (negreta, cursiva, imatges, enllaços, etc.). Les extensions de fitxers més habituals en aquests casos són `txt` i `csv`.

Addicionalment, fitxers amb formats de tipus `html`, `xml`, `json`, etc., també es poden tractar com a fitxers de text tenint en compte que, qualsevol tipus de format desapareixerà si no se'n fa l'adaptació correcta de manera manual.

## Lectura bàsica d'un fitxer de text
Java ens ofereix 3 classes bàsiques per llegir un fitxer de text:
1. `FileReader`: lector bàsic;
2. `BufferedReader`: lector eficient i
3. `Scanner`: lector per tractar diferents tipus de dades

## `FileReader`
La classe `FileReader`, que es troba dins del *package* `java.io`, permet obrir un fitxer en mode lectura a partir de la seva ruta, que pot ser absoluta o relativa.
```java
//Utilitzant una ruta relativa (en un sistema Linux)
FileReader freader = new FileReader("files/myfile.txt");


//Utilitzant una ruta relativa (en un sistema Windows)
FileReader freader = new FileReader("files\\myfile.txt");

//Utilitzant una ruta relativa (multiplataforma)
FileReader freader = new FileReader("files" + File.separator + "myfile.txt");
```
Aquesta obertura pot provocar una `FileNotFoundException` si el fitxer no existeix o si la ruta especificada no és correcta i, per tant, no s'ha pogut trobar el document. Aquesta excepció, que també es troba dins del *package* `java.io`, no és *bloquejant* i es pot tractar per evitar que el programa falli i aturi la seva execució. Aquest tractament, però, s'estudiarà més endavant.

La classe `FileReader` ofereix el mètode `int read()`, el qual llegeix caràcter a caràcter, retornant-ne el seu codi *Unicode* (en cas que no hi hagi més caràcters per llegir retorna -1). Aquesta lectura, però, és **molt ineficient**, ja que per cada caràcter individual a llegir ha de fer un accès a memòria secundària (disc dur), procès que és molt lent.

Un cop acabat de llegir el fitxer, cal tancar el `FileReader` mitjançant el mètode `void close()` per tancar i alliberar el fitxer i retornar els recursos al sistema.

La Figura 17.1 mostra l'exemple d'un fitxer de text i la Figura 17.2 mostra el codi necessari per poder-ne fer la lectura mitjançant la classe `FileReader`.

![Figura 17.1: exemple de fitxer de text](img/text_file_example.png)

{% code title="Figura 17.2: implementació de lectura de fitxer amb `FileReader`" overflow="wrap" lineNumbers="true" %}
```java
public String readFile(String filename) throws FileNotFoundException {
    FileReader freader = new FileReader(filename);
    String filecontent = "";
    int ccode = freader.read();
    while(ccode != -1) {
        filecontent += String.valueOf((char) ccode);
        ccode = freader.read();
    }
    freader.close();

    return filecontent;
}
```
{% endcode %}

## `BufferedReader`
La classe `BufferedReader`, dins del *package* `java.io`, fa una lectura més eficient dels fitxers de text ja que, internament, gestiona un *búffer* que permet llegir múltiples caràcters a la vegada i, per tant, disminueix el nombre d'accessos a memòria secundària.

Així doncs, aquesta classe no només té el mètode `int read()` que llegeix cada caracter de manera individual, sinó que també té el mètode `String readLine()`, el qual llegeix i retorna línies senceres i quan acaba el fitxer, retorna `null`.

Per poder llegir un fitxer mitjançant un `BufferedReader` cal crear, prèviament, un `FileReader`, ja que aquesta és la classe encarregada d'obrir el fitxer en mode lectura. A més a més, un cop acabada la lectua, també caldrà tancar el `BufferedReader` mitjançant el mètode `void close()`, el qual, al seu torn, també tancarà el `FileReader` intern.

La Figura 17.3 mostra l'exemple d'un fitxer de text amb múltiples línies i la Figura 17.4 mostra el codi necessari per poder-ne fer la lectura mitjançant la classe `BufferedReader`.

![Figura 17.3: exemple de fitxer de text amb múltiples línies](img/multi_line_file_example.png)

{% code title="Figura 17.4: implementació de lectura de fitxer amb `BufferedReader`" overflow="wrap" lineNumbers="true" %}
```java
public String readFile(String filename) throws FileNotFoundException {
    FileReader freader = new FileReader(filename);
    BufferedReader breader = new BufferedReader(freader);
    String filecontent = "";
    String line = breader.readLine();
    while(line != null) {
        filecontent += line;
        line = breader.readLine();
    }
    breader.close();

    return filecontent;
}
```
{% endcode %}

{% hint style="danger" %}
**Important:** la lectura de fitxer sempre haurà de ser el més eficient possible, per tant, sempre haurà d'involucrar el `BufferedReader`.
{% endhint %}

## `Scanner`
La classe `Scanner`, dins del *package* `java.io`, i que també s'utilitza per fer l'entrada de dades des de teclat, ofereix tots els mètodes necessaris per tal de poder tractar les dades de forma correcta segons el seu tipus. Per tant, permet llegir
* *paraules*: `String next()`;
* línies: `String nextLiine()`;
* nombres: `int nextInt()`,  `float nextFloat()`, `double nextDouble()`, etc.;
* booleans: `boolean nextBoolean()`
* etcètera

Per crear un lector de tipus `Scanner` necessitarem un `FileReader` (la lectura serà ineficient) o un `BufferedReader` (la lectura serà eficient). Ara però, com ja s'ha esmentat en l'apartat anterior, la lectura d'un fitxer sempre ha de ser eficient, per tant, sempre es crearà l'`Scanner` per sobre d'un `BufferedReader`. A més a més, com passa amb els altres tipus de `Readers`, un cop finalitzada la lectura del fitxer, caldrà tancar l'`Scanner` i alliberar els recursos.

Cal tenir en compte que, així com l'ús del `BufferedReader` es pot considerar obligatori, l'ús de l'`Scanner` no ho és i, per tant, es deixa a criteri del desenvolupador el seu ús, segons si es necessiten els mètodes de format de dades o no.

La Figura 17.5 mostra l'exemple d'un fitxer de text amb múltiples tipus de dades i la Figura 17.6 mostra el codi necessari per poder-ne fer la lectura mitjançant la classe `Scanner`.

![Figura 17.5: exemple de fitxer de text amb múltiples línies](img/multi_data_file_example.png)

{% code title="Figura 17.6: implementació de lectura de fitxer amb `Scanner`" overflow="wrap" lineNumbers="true" %}
```java
public void readFile(String filename) throws FileNotFoundException {
    FileReader freader = new FileReader(filename);
    BufferedReader breader = new BufferedReader(freader);
    Scanner sreader = new Scanner(breader);
    int num;
    float decim;
    String line;

    while(sreader.hasNextInt()) {
        num = sreader.nextInt();
    }

    while(sreader.hasNextFloat()) {
        decim = sreader.nextFloat();
    }
    
    line = sreader.nextLine();

    sreader.close();
}
```
{% endcode %}

{% hint style="danger" %}
**Important:** les Figures 17.2, 17.4 i 17.6 mostren una lectura molt senzilla de les dades dels fitxers, pensada, únicament, per mostrar la informació per pantalla o, simplement, llegir-la. Si cal un tractament més elaborat i una anàlisi de les dades que conté el fitxer cal utilitzar els mètodes de tractament d'`String` (vegeu el [Capítol 8](chapter8.md)) i diverses operacions matemàtiques.

Per exemple, la Figura 17.7 refà l'exemple 17.4 per fer un còmput del nombre de paraules i de caràcters que conté el fitxer de la Figura 17.3.
{% endhint %}

{% code title="Figura 17.7: implementació de lectura de fitxer amb `BufferedReader`" overflow="wrap" lineNumbers="true" %}
```java
public int[] readFile(String filename) throws FileNotFoundException {
    FileReader freader = new FileReader(filename);
    BufferedReader breader = new BufferedReader(freader);
    int nwords = 0, nchars = 0;
    String line = breader.readLine();
    while(line != null) {
        nwords += line.split(" ").length;
        nchars += line.length();

        line = breader.readLine();
    }
    breader.close();

    return new int[]{nwords, nchars};
}
```
{% endcode %}

## Escriptura bàsica d'un fitxer de text
L'escriptura d'un fitxer de text segueix una estructura molt similar al procés de lectura que s'ha explicat a l'apartat anterior, de tal manera que Java també ofereix 3 classes bàsiques per assolir l'objectiu:
1. `FileWriter`: escriptor bàsic;
2. `BufferedWriter`: escriptor eficient i
3. `PrintWriter`: escriptor per tractar diferents tipus de dades

## `FileWriter`
La classe `FileWriter`, que es troba dins del *package* `java.io`, permet obrir un fitxer en mode escriptura a partir de la seva ruta, que pot ser absoluta o relativa; en cas que el fitxer no existeixi, el crea nou. Addicionalment també permet obrir el fitxer en mode *sobreescriptura* o en mode *append*. El mode *sobreescriptura* esborra completament el fitxer (en cas que ja existeixi) i en torna a crear el contingut. El mode *append*, en canvi, respecta el contingut preexistent al fitxer i afegeix les noves dades al final de tot.

```java
//Utilitzant una ruta relativa (en un sistema Linux)
//Mode sobreescriptura
FileWriter fwriter = new FileWriter("files/myfile.txt");


//Utilitzant una ruta relativa (en un sistema Windows)
//Mode sobreescriptura
FileWriter fwriter = new FileWriter("files\\myfile.txt", false);

//Utilitzant una ruta relativa (multiplataforma)
//Mode append
FileWriter fwriter = new FileWriter("files" + File.separator + "myfile.txt", true);
```
Aquesta obertura pot provocar una `IOException` si hi ha qualsevol error d'entrada/sortida durant l'intent d'obrir o crear el document en mode escriptura. Tal com passa amb l'excepció `FileNotFoundException`, la `IOException` també es troba dins del *package* `java.io` i no és *bloquejant*, per tant es pot tractar per evitar que el programa falli i aturi la seva execució.

La classe `FileWriter` ofereix diversos mètodes d'escriptura
* `void write(int c)`
* `void write(String str)`
* `Writer append(char c)`
* `Writer append(CharSequence seq)`: un `CharSequence` és pot considerar equivalent a un `String`

Malauradament, tot i que hi hagi mètodes per escriure `String`, el `FileWriter` és equivalent al `FileReader` pel que fa a eficiència i, per tant, escriu a fitxer caràcter a caràcter, fent que el procès sigui molt costós per l'elevat nombre d'accessos a memòria secundària (disc dur) que ha de realitzar.

Un cop acabat d'escriure el fitxer, cal tancar el `FileWriter` mitjançant el mètode `void close()`, el qual guarda les dades a fitxer, el tanca, l'allibera i retornar els recursos al sistema.

{% hint style="danger" %}
**Important:** si un fitxer obert en mode escriptura no es tanca, les dades no quedaran guardades i, per tant, es perdràn!
{% endhint %}

La Figura 17.8 mostra el codi necessari per poder-ne fer l'escriptura d'un fitxer `FileWriter` (mode *sobreescriptura*) i la Figura 17.9 en mostra el resultat.

{% code title="Figura 17.8: implementació de l'escriputra de fitxer amb `FileWriter` (mode *sobreescriptura*)" overflow="wrap" lineNumbers="true" %}
```java
public void writeFile(String filename) throws IOException {
    FileWriter fwriter = new FileWriter(filename);
    String filecontent = "Hola, benvinguts!";
    for(int pos=0; pos<filecontent.length; pos++) {
        fwriter.write(filecontent.codePointAt(pos));
    }
    fwriter.close();
}
```
{% endcode %}

![Figura 17.9: resultat de l'escriptura d'un fitxer de text a partir del codi de la Figura 17.8](img/text_file_example_writing.png)

## `BufferedWriter`
La classe `BufferedWriter`, dins del *package* `java.io`, fa una escriptura de dades a fitxer més eficient ja que tal com passa amb el `BufferedReader`, internament, gestiona un *búffer* que permet escriure múltiples caràcters a la vegada i, per tant, disminueix el nombre d'accessos a memòria secundària.

Aquesta classe té els mateixos mètodes que la `FileWriter`, ara però, gràcies a l'ús del *búffer* intern, els mètodes
* `void write(String str)`
* `Writer append(CharSequence seq)`

poden escriure a fitxer tots els caràcters de cop a fitxer (o, si menys no, un grapat de caràcters a la vegada, segons la mida del *búffer*).

Addicionalment, aquesta classe també ofereix els mètodes 
* `void newLine()`, que afegeix un salt de línia al fitxer i
* `void flush()`, que buida el *búffer* i escriu els caràcters pendents al fitxer; ara però, l'ús del mètode `flush()` no evita el tancament del `BufferedWriter` mitjançant el mètode `close()`.

Per poder llegir un fitxer mitjançant un `BufferedWriter` cal crear, prèviament, un `FileWriter`, ja que aquesta és la classe encarregada d'obrir el fitxer en mode escriptura. A més a més, un cop acabada la lectua, com ja s'ha dit, també caldrà tancar el `BufferedWriter` mitjançant el mètode `void close()`, el qual, al seu torn, també tancarà el `FileWriter` intern.

La Figura 17.10 mostra l'exemple d'un fitxer de text preexistent, la Figura 17.11 mostra el codi necessari per escriure-hi dades en mode *append* mitjançant la classe `BufferedWriter` i la Figura 17.12 mostra el resultat final.

![Figura 17.10: fitxer que es modificarà amb el codi de la Figura 17.11 en el seu estat inicial](img/text_file_example_writing.png)

{% code title="Figura 17.11: implementació de l'escriputra de fitxer amb `BufferedWriter` (mode *append*)" overflow="wrap" lineNumbers="true" %}
```java
public void writeFile(String filename) throws IOException {
    FileWriter fwriter = new FileWriter(filename, true);
    BufferedWriter bwriter = new BufferedWriter(fwriter);
    String filecontent = "Estem fent classe de programació a DAM1";

    bwriter.newLine();
    bwriter.write(filecontent);
    
    bwriter.close();
}
```
{% endcode %}

![Figura 17.12: resultat final d'escriptura sobre el fitxer de la Figura 17.10 en mode *append*](img/text_file_example_writing_append.png)


{% hint style="danger" %}
**Important:** l'escriptura de fitxer sempre haurà de ser el més eficient possible, per tant, sempre haurà d'involucrar el `BufferedWriter`.
{% endhint %}

## `PrintWriter`
La classe `PrintWriter`, dins del *package* `java.io`, ofereix els mateixos mètodes que les classes `FileWriter` i `BufferedWriter` i, a més a més, tots els mètodes de tipus `print()` que faciliten el tractament dels diversos tipus de dades i permeten fer una escriptura a fitxer de manera molt similar a com es fa l'escriptura de resultats per pantalla:
* `void print(String str)`;
* `void print(int num)`;
* `void print(float num)`;
* etcètera
* `void println()`
* `void println(String str)`
* `void println(int num)`
* `void println(float num)`
* etcètera

Per crear un lector de tipus `PrintWriter` necessitarem un `FileWriter` (l'escriptura serà ineficient) o un `BufferedWriter` (l'escriptura serà eficient). Ara però, com ja s'ha esmentat en l'apartat anterior, l'escriptura d'un fitxer sempre ha de ser eficient, per tant, sempre es crearà el `PrintWriter` per sobre d'un `BufferedWriter`. A més a més, com passa amb els altres tipus de `Writers`, un cop finalitzada l'escriptura del fitxer, caldrà tancar el `PrintWriter` i alliberar els recursos.

Cal tenir en compte que, així com l'ús del `BufferedWriter` es pot considerar obligatori, l'ús del `PrintWriter` no ho és i, per tant, es deixa a criteri del desenvolupador el seu ús, segons si es necessiten els mètodes de format de dades o no.

La Figura 17.13 mostra l'exemple d'un fitxer de text preexistent, la Figura 17.14 mostra el codi necessari per escriure-hi dades en mode *sobreescriptura* mitjançant la classe `PrintWriter` i la Figura 17.15 mostra el resultat final.

![Figura 17.13: fitxer que es modificarà amb el codi de la Figura 17.14 en el seu estat inicial](img/text_file_example_writing_append.png)

{% code title="Figura 17.14: implementació de l'escriputra de fitxer amb `PrintWriter` (mode *sobreescriptura*)" overflow="wrap" lineNumbers="true" %}
```java
public String writeFile(String filename) throws IOException {
    FileWriter fwriter = new FileWriter(filename, false);
    BufferedWriter bwriter = new BufferedWriter(fwriter);
    PrintWriter pwriter = new PrintWriter(bwriter);
    String filecontent = "Escric noves dades a fitxer";

    pwriter.print(filecontent);
    
    pwriter.close();
}
```
{% endcode %}

![Figura 17.15: resultat final d'escriptura sobre el fitxer de la Figura 17.13 en mode *sobreescriptura*](img/text_file_example_writing_overwrite.png)