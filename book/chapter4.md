# Bloc de codi
Un bloc de codi, **en Java** (i en la majoria de llenguatges de programació), són totes aquelles instruccions que es troben dins de la zona delimitada per les claus `{}`.

Tot programa té, com a mínim, un bloc de codi principal, el de la funció `main`. Per exemple, en Java
```java
1   public class MainProgram {
2       public static void main(String[] args) {
3           int nstudents = 20;
4           System.out.println("A la classe de DAM1 som: " + nstudents + " alumnes");
5       }
6   }
```
les línies 3 i 4 formen part del bloc de codi del `main`.

Dins d'un bloc de codi és pot utilitzar qualsevol tipus d'instrucció i, fins i tot, definir més blocs de codi, tal com veurem als [Captíols 5](chapter5.md) i [6](chanpter6.md), on es defineixen les sentències de control de flux condicional i iteratiu, respectivament.

## Sentència `break`
La sentència `break` permet finalitzar (o trencar) l'execució d'un bloc de codi. És a dir, totes aquelles instruccions d'un determinat bloc de codi  que es trobin sota d'un `break` s'ignoraran i no s'executaran.

Per exemple, en el codi següent
```java
1   public class MainProgram {
2       public static void main(String[] args) {
3           int nstudents = 20;
4           System.out.println("A la classe de DAM1 som: " + nstudents + " alumnes");
5           break;
6           nstudents += 4;
7           System.out.println("Ara, a la classe de DAM1 som: " + nstudents + " alumnes");
8       }
9   }
```
les línies 6 i 7 no s'executaran, ja que estan sota el `break` de la línia 5 i, per tant, quan el flux d'execució arribi a aquesta instrucció saltarà, directament, a la línia 8 (finalització del bloc).