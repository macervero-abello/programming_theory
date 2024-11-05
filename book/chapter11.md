# Control de flux modular
A mesura que els programes creixen, tant en nombre d'instruccions com en complexitat, és molt possible que s'hagin d'implementar les mateixes funcionalitats (característiques) en diversos punts i es fa necessari modularitzar i organitzar el codi per fer-lo més llegible, fàcilment ampliable, de més fàcil manteniment i, sobretot, per evitar el *copy/paste* i tots els problemes que se'n deriven.

Per facilitar aquesta organitzaió i modularitat del codi apareix el control de fluxe modular o, dit d'altra manera, **les funcions i els procediments**. D'aquesta manera es passa del paradigma de *programació estructurada*, que és el que s'ha treballat fins ara, al paradigma de *programació modular*, basat en el disseny modular.

## Programació modular
La programació modular és un paradigma de programació que consisteix en analitzar un programa i totes les seves funcionalitats per tal de poder-lo dividir en mòduls (subprogrames, algorismes) més petits i senzills que el facin més llegible i sostenible. En aquest context, s'entén que un programa és sostenible si es pot mantenir i ampliar fàcilment i si els errors que pugui tenir són relativament fàcils de trobar i corregir gràcies a la seva modularització.

Els mòduls o subprogrames en què queda dividit el programa principal són, justament, les funcions i els procediments que s'han anomenat al principi d'aquest capítol.

L'anàlisi del programa principal i la seva divisió en mòduls també es pot anomenar *disseny modular* o *anàlisi descendent (top-down)*.

## Programa principal: la funció o procediment `main`
Tal com ja sabem, tot programa ha de definir el seu procés prinipal, que és el seu punt d'entrada. Aquest procés ha de ser únic i, en molts llenguatges de programació, es defineix com una funció o procediment especial que s'anomena `main`.

## Funcions i procediments
Les funcions i els procediments són **blocs de codi** que permeten implementar un algorisme (una tasca) molt específica i que tenen unes característiques especials:
* Són **independents**, és a dir, no estan situats dins del programa principal, sinó que s'implementen fora
* Poden ser **invocats** (cridats) des del programa principal o des de qualsevol altra funció o procediment per tal de ser executats
* Tenen un **nom identificatiu** per poder-ne fer la invocació
* S'encarreguen d'implementar algorismes, és a dir, de **fer càlculs i retornar resultats**, per tant, en cap moment gestionaran la interacció amb l'usuari; aquesta interacció sempre s'implementarà dins del programa principal
* Poden rebre dades d'entrada, anomenades **paràmetres**, que són les que necessitaran per poder dur a terme els càlculs que han d'implementar
* Poden **retornar valors**