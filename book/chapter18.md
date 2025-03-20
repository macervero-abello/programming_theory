# Excepcions
Les excepcions són un sistema de gestió d'errors que permeten tractar tant els problemes derivats d'incorreccions en el codi com provocats per la interacció amb l'usuari o el *hardware*.

Així doncs, quan el codi d'un programa provoca un error, la seva execució s'atura i llença una `Exception` (excepció) amb tota la informació necessària per detectar el problema i, en cas que es pugui, solucionar-lo sense necessitat d'aturar, de manera definitiva, el programa.

D'excepcions n'hi ha de dos tipus:
* *Unchecked exceptions*: són aquelles excepcions que no es poden comprovar prèviament, en temps de compilació. És a dir, l'error que les ocasiona només es pot comprovar en temps d'execució, quan realment succeeix. Totes elles són subclasses de `RuntimeException` i sempre estan provocades per errors de programació, per tant, no es poden gestionar per evitar que el programa el tanqui sobtadament i només es poden solucionar arreglant el codi que les ocasiona.
Exemples: `ArrayIndexOutOfBoundException`, `NullPointerException`
* *Checked exceptions*: són aquelles excepcions que es poden comprovar prèviament, en temps de compilació. Dit d'altra manera, són excepcions que es poden preveure ja que són provocades per factors externs (sistema de fitxers, *hardware*, bases de dades, etc.) i, per tant, poden ser tractades per evitar que el programa es tanqui sobtadament.
Exemples: `IOException`, `SQLException`, `FileNotFoundException`

Així doncs, les excepcions que s'han d'aprendre a gestionar són les *Checked exceptions*

## Gestió de les *Checked Exceptions*
La gestió d'una *checked exception* es pot fer de dues maneres:
1. Delegant
2. Capturant-la

### Delegació d'excepcions: instrucció `throws`
Quan un mètode (funció o procediment) pot provocar una excepció, es pot decidir no fer-ne el tractament directament dins d'aquest mètode, sinó delegar-ne la seva gestió a la funció o procediment que l'ha cridat. Per fer-ho es necessita utilitzar la instrucció `throws`.

Per exemple, la Figura 18.1



 un programa `main` que crida una funció de lectura de fitxer, la qual pot provocar una excepció de tipus `IOException`. Per fer que 