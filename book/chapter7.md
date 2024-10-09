# Creació d'un menú amb les sentències `do-while` i `switch-case`
Molts programes implementats per executar-se en un terminal necessiten un menú per poder-ne gestionar les opcions i recollir les indicacions de l'usuari. Per exemple, podem voler implementar un programa *calculadora* que deixi escollir a l'usuari si vol fer una suma, una resta, una multiplicació, una divisió o si, per contra, vol tancar-lo. A més a més, volem que aquest menú es vagi mostrant una i altra vegada mentre l'usuari no indiqui que vol tancar l'aplicació. Per tant, necessitem control de flux que ens permeti repetir l'acció de mostrar el menú i control condicional que ens permeti gestionar l'opció escollida per l'usuari per a ser executada.

Molts programes que tenen aquest menú característic l'implementen utilitzant les sentències `do-while` i `switch-case` combinades tot i que, evidentment, també es pot utilitzar la sentència `while` o la sentència `if-else if-else`.

La Figura 7.1 mostra l'exemple d'un menú amb 4 opcions (la primera és la de sortir). El codi gestiona l'opció escollida i l'interacció amb l'usuari, així com també la gestió de l'error en cas que l'usuari introdueixi un valor incorrecte dins del cas `default` (cal tenir en compte que sempre s'ha de mantenir a l'usuari ben informat del que està passant, sobretot en cas d'error).

{% code title="Figura 7.1: implementació d'un menú" overflow="wrap" lineNumbers="true" %}
```java
import java.util.Scanner;

public class MenuMain {
    public static void main(String[] args) {
        Scanner keyboard = new Scanner(System.in);
        int option;

        do {
            System.out.println("~~~ MENÚ ~~~");
            System.out.println("\t0. Sortir");
            System.out.println("\t1. Opció 1");
            System.out.println("\t2. Opció 2");
            System.out.println("\t3. Opció 3");
            System.out.print("Si us plau, esculli una opció: ");
            option = keyboard.nextInt();

            switch(option) {
                case 0:
                    System.out.println("Tancant...");
                    break;
                case 1:
                    System.out.println("Ha escollit l'opció 1");
                    break;
                case 2:
                    System.out.println("Ha escollit l'opció 1");
                    break;
                case 3:
                    System.out.println("Ha escollit l'opció 1");
                    break;
                default:
                    System.out.println("Opció incorrecta");
            }
        } while(option != 0);
    }
}
```
{% endcode %}