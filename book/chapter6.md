# Control de flux iteratiu
En el [Capítol 5](chapter5.md) hem vist que el control de flux condicional permet l'execució d'un determinat bloc de codi si es compleix una condició. El control de flux iteratiu, en canvi, permet **repetir** un tros de codi (bloc de codi) mentre una determinada condició es compleixi, és a dir, sigui certa. Cada execució o repetició del bloc codi gestionat pel control de flux iteratiu s'anomena iteració o volta.

Hi ha tres sentències de **control de flux iteratiu** bàsiques, les quals, s'acostumen a mal anomenar *bucles*:
1. la sentència `while`;
2. la sentència `do-while` i
3. la sentència `for`.

L'ús d'aquestes estructures de control 
* evita crear codi duplicat (sempre que un programador té la intenció de fer *copy/paste* s'ha de preguntar si el codi es pot posar dins d'un *bucle*);
* simplifica la implementació dels algorismes i 
* facilita la detecció d'errors.

## Característiques que han de complir totes les estructrues de control de flux iteratiu
Tota sentència de control de flux iteratiu ha de complir 3 característques bàsiques:
1. Ha d'inicialitzar els valors de totes aquelles variables que intervenen en la condició de manera adequada
2. Ha de definir quina és la condició que permet entrar dins del bloc de codi del *bucle* i fer una nova repetició (iteració o volta)
3. A cada volta ha d'actualitzar els valors de les variables que intervenen en la condició per tal que, en un determinat moment, la condició sigui falsa (`false`) i, per tant, el codi pugui sortir de les iteracions; en cas contrari es crea un *bucle* infinit i l'algorisme queda bloquejat.