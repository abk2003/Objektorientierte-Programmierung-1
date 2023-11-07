# Objektorientierte Programmierung 1

- ***Datentypen***
    - ***Primitive Datentypen***
        
        
        | Typ | Wertebereich |
        | --- | --- |
        | Boolean | true oder false |
        | char | 16-Bit-Unicode-Zeichen (0x0000 … 0xFFFF) —> “a”, “d”, “f” |
        | byte | –2² bis 2⁷ – 1 (–128 … 127) |
        | short | –2¹⁵ bis 2¹⁵ – 1 (–32.768 … 32.767) |
        | int | –2³¹ bis 2³¹ – 1 (–2.147.483.648 … 2.147.483.647) |
        | long | –2⁶³ bis 2⁶³ – 1(–9.223.372.036.854.775.808 … 9.223.372.036.854.775.807) |
        | float | 1,40239846E–45f … 3,40282347E+38f |
        | double | 4,94065645841246544E–324 … 1,79769131486231570E+308 |
        - **Wrapper-Klassen**
            
            Wrapper-Klassen sind spezielle Klassen in Java, die verwendet werden, um primitive Datentypen in Objekte zu verpacken. Dies ermöglicht es, primitive Datentypen in Situationen zu verwenden, in denen normalerweise nur Objekte akzeptiert werden. Wrapper-Klassen bieten auch nützliche Methoden und Eigenschaften zur Arbeit mit diesen Werten.
            
            ```java
            // Wrapper-Variabeln
            Integer age = 25;
            Double price = 19.99;
            Character grade = 'A';
            Boolean isJavaFun = true;
            Long population = 83000000L;
            Float temperature = 22.5f;
            Byte data = 127;
            Short distance = 500;
            ```
            
    - ***Referenztypen***
        - ***Enum-Typ***
            
            Enum-Datentypen werden mit dem Schlüsselwort **`enum`** erstellt. Jede Konstante innerhalb des Enums wird zu einem statischen finalen Objekt und kann demnach referenziert werden. In unserem Beispiel jetzt: **`Weekday.MONDAY` *oder* `Weekday.SATURDAY`*.*** Enums werden verwendet um eine begrenzte Menge von Werten darzustellen die nicht veränderbar sind, z.B. Wochentage, Monate, usw… Enums werden auch für **`Switch`**-Anweisungen verwendet. Siehe unteres Beispiel. Der Default Wert von Enums ist **`null`**.
            
            **Beispiel Weekdays:** 
            
            ```java
            public enum Weekday {
                MONTAG, DIENSTAG, MITTWOCH, DONNERSTAG, 
            		FREITAG, SAMSTAG, SONNTAG                  // Konstanten
            
                public boolean isWeekend() {
                    return this == SAMSTAG || this == SONNTAG;
                }
            
                public static void main(String[] args) {
                    Weekday samstag = Weekday.SAMSTAG;
                    System.out.println(samstag.isWeekend()); // True
                }
            }
            ```
            
            **Beispiel von Enum in Swtich-Anweisung:**
            
            ```java
            public class EnumSwitchExample {
                enum Wochentage {
                    MONTAG, DIENSTAG, MITTWOCH, DONNERSTAG, 
            				FREITAG, SAMSTAG, SONNTAG
                }
            
                public static void main(String[] args) {
                    Wochentage tag = Wochentage.DIENSTAG;
            
                    switch (tag) {
                        case MONTAG:
                            System.out.println("Es ist Montag.");
                            break;
                        case DIENSTAG:
                            System.out.println("Es ist Dienstag.");
                            break;
                        case MITTWOCH:
                            System.out.println("Es ist Mittwoch.");
                            break;
                        case DONNERSTAG:
                            System.out.println("Es ist Donnerstag.");
                            break;
                        case FREITAG:
                            System.out.println("Es ist Freitag.");
                            break;
                        case SAMSTAG:
                            System.out.println("Es ist Samstag.");
                            break;
                        case SONNTAG:
                            System.out.println("Es ist Sonntag.");
                            break;
                        default:
                            System.out.println("Ungültiger Wochentag.");
                            break;
                    }
                }
            }
            ```
            
        - ***Array-Typ***
            
            **3 Methoden um ein Array zu initialisieren:** 
            
            ```java
            double[] randomNum = new double[ 10 ]; // mit New
            int[] primes;                          // ohne New
            int[] primes = {1, 2, 3, 4, 5};        // Array mit Werten
            
            -----------------------------------------------------------------------------
            
            // Führt zu Fehlermeldung, weil Array schon definiert ist
            String[] strings = new String[5];
            strings = {"Hallo", "ABC", "KFC"};     // Würde Fehlermeldung abgeben
            
            // Richtige schreibweise
            String[] strings = new String[5];
            strings[0] = "Hallo";
            strings[1] = "ABC"; 
            ```
            
            **Vererbung von Arrays**:
            
            ```java
            String[] strings = new String[5];
            String[] secondStrings;
            String[] copyStrings;
            
            secondStrings = strings; // Verweisen auf gleiches Array
            ```
            
            **Array kopieren mit `clone()`- und `copyOf()`-Methoden:**
            
            ```java
            // Importieren von java.util.Arrays; um copyOf() zu nutzen
            import java.util.Arrays;
            
            // clone()-Methode
            copyStrings = strings.clone(); // Kopiert Array
            
            // copyOf(Das zu kopierende String, Länge des Arrays)-Methode 
            copyStrings = Arrays.copyOf(strings, 10); 
            ```
            
            **Weiter Methoden von Arrays**:
            
            ```java
            // Importieren von java.util.Arrays; um Methoden zu nutzen
            import java.util.Arrays;
            
            // Checkt ob strings und copyStrings gleich sind 
            System.out.println(Arrays.equals(strings, copyStrings));
            
            // Wandelt Array in ein String um
            System.out.println(Arrays.toString(strings));
            
            // Sortiert Array
            System.out.println(Arrays.sort(strings)); 
            ```
            
        - ***ArrayLists***
            
            Eine ArrayList ermöglicht es eine Anzahl von Elementen in einer geordneten Sequenz zu speichern. Im gegensatz zu Arrays die eine feste Grösse haben müssen, kann man beliebige Elemente bei ArrayLists hinzufügen oder entfernen. 
            
            ArrayLists werden wie folgt deklariert:
            
            1. Importiere zuerst die erforderliche Java-Klasse **`java.util.ArrayList`.**
            2. Definiere den Datentyp der ArrayList in den **`< >`** Klammern, um anzugeben, welchen Datentyp die ArrayList akzeptieren soll. Zum Beispiel, wenn du Strings speichern möchtest, verwende dann **`ArrayList<String>`**.
            3. Gebe einen Namen für deine ArrayList an, um deren Zweck zu verdeutlichen. Zum Beispiel, **`namensliste`** für eine Liste von Namen.
            4. Verwende **`new ArrayList<>();`**, um eine neue ArrayList zu erstellen. Du kannst den Datentyp (optional) in den **`< >`** Klammern angeben.
            
            ```java
            import java.util.ArrayList;
            
            // Erstellung einer ArrayList
            ArrayList<String> namensliste = new ArrayList<>();
            ```
            
            **Beispielcode ArrayList und ihre Methoden:**
            
            ```java
            import java.util.ArrayList;
            
            public class ArrayListExample {
                public static void main(String[] args) {
                    **// Erstellung einer ArrayList für Zeichenfolgen**
                    ArrayList<String> namensliste = new ArrayList<>();
            
                    **// Hinzufügen von Elementen**
                    namensliste.add("Max");
                    namensliste.add("Anna");
                    namensliste.add("Tom");
            
                    **// Zugriff auf das erste Element**
                    String ersterName = namensliste.get(0);
                    System.out.println("Erster Name: " + ersterName);
            
                    **// Iteration durch die ArrayList**
                    System.out.println("Alle Namen in der Liste:");
                    for (String name : namensliste) {
                        System.out.println(name);
                    }
            
                    **// Suche nach dem Index eines Elements**
                    int index = namensliste.indexOf("Max");
                    if (index >= 0) {
                        System.out.println("Max gefunden an Position: " + index);
                    } else {
                        System.out.println("Max nicht gefunden.");
                    }
            
                    **// Entfernen eines Elements nach Index**
                    namensliste.remove(1); // Entfernt "Anna"
            
                    **// Entfernen eines Elements nach Wert**
                    namensliste.remove("Tom"); // Entfernt "Tom"
            
                    **// Umwandlung der ArrayList in ein Array**
                    String[] namenArray = namensliste.toArray(new String[5]);
            
                    **// Ausgabe des sortierten Arrays**
                    for (String name : namensliste) {
                        System.out.println(name);
                    }
                }
            }Typecasting mit null Werten:
            
            ```
            
- ***Klassen***
    - ***Zugriffskontrolle (Sichtbarkeit)***
        - **`private`**: Eine private Variable oder Methode ist nur in der Klasse selbst sichtbar und kann nicht von ausserhalb der Klasse zugegriffen werden. Sie dient dazu, Informationen in einer Klasse zu verbergen und den direkten Zugriff von ausserhalb zu verhindern.
        - **`public`**: Eine öffentliche Variable oder Methode ist von überall aus sichtbar und zugänglich. Sie kann von anderen Klassen und Methoden aufgerufen und verwendet werden. Public-Elemente ermöglichen die Interaktion mit der Klasse von ausserhalb.
        - **`protected`**: Eine Variable oder Methode mit dem Zugriffsmodifikator "protected" ist in der Klasse selbst, in abgeleiteten (subklassen) Klassen und im gleichen Paket sichtbar. Dies ermöglicht die Nutzung und Vererbung in Unterklassen, während sie ausserhalb des Pakets unsichtbar bleibt.
        - **Paketprivat (`default`)**: Eine Variable oder Methode ohne expliziten Zugriffsmodifikator (also ohne "public", "protected" oder "private") ist "paketprivat" oder "default". Das bedeutet, dass sie nur im gleichen Paket sichtbar ist, aber nicht ausserhalb des Pakets.
        
        Hier noch zwei Tabellen dazu: 
        
        ![Untitled](Objektorientierte%20Programmierung%201%20db29bc8cecd240f78c41c2ec06bbbedf/Untitled.png)
        
        ![Untitled](Objektorientierte%20Programmierung%201%20db29bc8cecd240f78c41c2ec06bbbedf/Untitled%201.png)
        
    - ***Objekt- und Klassenvariabeln***
        
        ![Untitled](Objektorientierte%20Programmierung%201%20db29bc8cecd240f78c41c2ec06bbbedf/Untitled%202.png)
        
        ***Klassenvariabeln*** 
        
        Klassenvariablen sind Variabeln, die für die gesamte Klasse gemeinsam genutzt werden. Alle Objekte der Klasse teilen sich denselben Wert für eine Klassenvariable. Beispielsweise kann die Klassenvariable `**budget**` in der Klasse **`Candy`** von allen Objekte der Klasse gelesen und geändert werden.
        
        Der Unterschied zwischen Objekt- und Klassenvariablen liegt darin, dass Klassenvariablen mit dem Schlüsselwort **`static`** deklariert werden. Klassenvariablen sind Variablen, die unabhängig von einer Instanz/Objekt der Klasse genutzt werden können. Hier ist ein Beispiel:
        
        ```java
        class Candy {
        	static int budget = 20; // Keine var deklaration möglich
        
        	public static void main(String[] args) {
        		// budget kann alleine stehen. Ohne Erstellung von Objekt/Instanz
        		System.out.println(budget);    
        	}
        }
        ```
        
        ***Objektvariabeln***
        
        Objektvariablen sind Eigenschaften oder Attribute, die zu einem bestimmten Objekt oder einer Instanz der Klasse gehören. Jedes Objekt hat seine eigenen Werte für diese Variablen, die unabhängig von anderen Instanzen sind. Zum Beispiel kann ein **`lollipop`**-Objekt einen anderen ***Namen*** und ***Preis*** haben als ein ***`chocolate`***-Objekt.
        
        Es ist wichtig zu beachten, dass bei Objektvariablen die Datentypen angegeben werden müssen, und es wird kein **`var`** für die Deklaration verwendet. Objektvariablen gehören zu einer spezifischen Instanz/Objekt der Klasse und sind nicht mit der Klasse als Ganzes verbunden. Hier ein Beispiel von Objektvariablen:
        
        ```java
        class Candy {
        	String name;       // Keine var deklaration möglich. 
        	int price;
        	int quantity;
        	
        	public static void main(String[] args) {
        		Candy lollipop = new Candy();     // Objekt lollipop wird erstellt
        		lollipop.name = "Lollipop";       // lollipop.name wird ein Name zugewiesen
        	}
        
        }
        ```
        
    - ***Methoden***
        - ***Objekt- und Klassenmethoden***
            
            ![Untitled](Objektorientierte%20Programmierung%201%20db29bc8cecd240f78c41c2ec06bbbedf/Untitled%203.png)
            
            **Klassenmethoden**
            
            Eine Klassenmethode ist eine Methode, die zu einer Klasse gehört, aber nicht an ein bestimmtes Objekt dieser Klasse gebunden ist. Sie wird mithilfe des Klassennamens aufgerufen, nicht über ein konkretes Objekt. Solche Klassenmethoden werden immer mit dem Schlüsselwort **`static`** deklariert. Hier ein Beispiel dazu:
            
            ```java
            public class MyClass{
            // Erstellen von Klassenmethode
            	public static void classMethod() {
            		System.out.println("Ich bin eine Klassenmethode");;
            	}
            }
            
            // Klassenmethode aufrufen
            MyClass.classMethod();
            ```
            
            **Objektmethoden**
            
            Eine Objektmethode ist eine Methode, die an ein bestimmtes Objekt einer Klasse gebunden ist. Sie wird über ein konkretes Objekt der klasse aufgerufen und kann die Variablen dieses Objekts zugreifen. Hier ein Beispiel dazu:
            
            ```java
            public class MyClass {
            // Erstellen von Objektmethode
            	public void objectMethod() {
            		System.out.println("Ich bin eine Objektmethode");
            	}
            }
            
            // Zuerst Objekt der Klasse MyClass erstellen
            MyClass myObject = new MyClass(); 
            
            // Aufrufen der Methode objectmethode für "myObject" aufrufen
            myObject.objectMethod();
            ```
            
        - ***Getter- und Setter-Methoden***
            - **`Getter`**: Eine Getter-Methode ist eine Methode, die verwendet wird, um den Wert einer privaten Variable abzurufen. Sie hat normalerweise den Präfix "get" gefolgt von dem Namen der Variable, deren Wert abgerufen werden soll. Getter-Methoden sind öffentlich und geben den Wert der Variablen zurück, ohne sie direkt preiszugeben.
            - **`Setter`**: Eine Setter-Methode ist eine Methode, die verwendet wird, um den Wert einer privaten Variable zu ändern. Sie hat normalerweise den Präfix "set" gefolgt von dem Namen der Variable, deren Wert geändert werden soll. Setter-Methoden sind öffentlich und akzeptieren einen Wert als Parameter, um die Variable zu aktualisieren.
            
            Ein Beispiel zu ***Getter- und Setter-Methoden:***
            
            ```java
            class Candy {
                private String name; // Private Objektvariable
            
                // Getter-Methode für die Variable "name"
                public String getName() {
                    return this.name;
                }
            
                // Setter-Methode für die Variable "name"
                public void setName(String candyName) {
                    this.name = candyName;
                }
            
            		// boolean-Methode für die Variable "name"
            		/* Anstatt das "get" Präfix wird das "is" Präfix 
            			 für Boolean Methoden */
            		public boolean isName(String candyName) { 
            				return this.name == candyName;
            		}
            }
            ```
            
        - ***Overloading und Overriding***
            
            `**Overloading`:** Overloading beizeht sich auf eine Möglichkeit, in einer Klasse mehrere Methoden mit demselben Namen, aber unterschiedlichen Parametertypen oder unterschiedlicher Anzahl von Parametern zu definieren. Es ermöglicht verschiedene Versionen einer Methode bereitzustellen. Während des Aufrufs einer überladenen Methode wird die passende Methode basierend auf der Anzahl und den Typen der Argumente ausgewählt. 
            
            Beispielcode Overloading:
            
            ```java
            class Calculator {
            	
                **// Overloading Methoden
            		// Methode 1**
                **public int add(double a, int b) {
                    return a + b;
                }
            		// Methode 2 
                public double add(int a, double b) {
                    return a + b;
                }
            		// Methode 3
                public int add(double a, double b) {
                    return a + b;
                }**
            		public static void main(String[] args) {
            			Calculator rechner = new Calculator();
            			**rechner.add(1, 2); // Fehlermeldung!! Da Methoden 1,2 gleich spezifisch sind
            			rechner.add(2.5, 3); // Methode 1
            			rechner.add(2.5, 3.5); // Methode 3**
            		}
            }
            ```
            
            Wichtig hierbei zu beachten gilt, dass die Parameter der Methoden nicht gleich spezifisch sein dürfen. Beispiel bei rechner.add(1, 2);. Methode 1 und 2 sind am nähsten zu (int 1, int 2) und der Compiler führt eine Fehlermeldung aus, weil es sich nicht entscheiden kann welche Methode es jetzt auswählen soll. Auch zu beachten gillt, die Anzahl der Parameter. Wenn wir jetzt hier 3 Parameter mit int hätten, würde es auch nicht funktionieren, da die Parameter Anzahl äquivalent sein muss. 
            
            **`Overriding`:** Overriding ist das Konzept, bei dem eine Unterklasse eine Methode aus ihrer Oberklasse überschreibt, um spezifischere Implementierung bereitzustellen. Die überschriebene Methode muss denselben Namen, Rückgabetyp und Parameter wie die Methode in der Oberklasse haben. Dies ermöglicht eine Anpassung des Verhaltens in der Unterklasse, ohne die Methode in der Oberklasse zu ändern.
            
            ```java
            class Animal {
                public void makeSound() {
                    System.out.println("Ein Tier macht einen Klang.");
                }
            }
            
            class Dog extends Animal {
                **@Override
                public void makeSound() {
                    System.out.println("Der Hund bellt.");
                }**
            }
            ```
            
            Unterschiede zwischen Overloading und Overriding:
            
            **Overloading:**
            
            - **`Verschiedene Signaturen`:** Bei Overloading haben die Methoden denselben Namen, aber unterschiedliche Parameterlisten (z. B. unterschiedliche Anzahl der Parameter, Reihenfolge der Parameter oder unterschiedliche Datentypen der Parameter).
            - **`Dynamische Bindung`:** Die Auswahl der überladenen Methode erfolgt zur Laufzeit (dynamische Bindung), wenn das konkrete Objekt bekannt ist. Dies bedeutet, dass die Methode je nach dem tatsächlichen Typ des Objekts aufgerufen wird.
            - **`Dynamischer Typ des Objekts entscheidet`:** Bei Overloading hängt die Auswahl der Methode vom dynamischen Typ des Objekts ab. Wenn eine Methode aufrufen wird, wird die Methode ausgewählt, die zum Typ des tatsächlichen Objekts gehört.
            
            **Overriding:**
            
            - **`Identische Signaturen`:** Bei Overriding haben die Methoden denselben Namen, denselben Rückgabetyp und dieselbe Parameterliste wie die Methode in der Oberklasse.
            - **`Statische Auflösung`:** Die Auswahl der überschriebenen Methode erfolgt zur Kompilierungszeit (statische Bindung) basierend auf dem Typ der Referenzvariable. Das bedeutet, dass die Auswahl der Methode zur Kompilierungszeit festgelegt wird und nicht zur Laufzeit geändert wird.
            - **`Statische Typen der Argumente entscheiden`:** Bei Overriding wird die Methode aufgrund des statischen Typs der Referenzvariable ausgewählt. Das bedeutet, dass die Auswahl der Methode anhand des erwarteten Typs in der Referenzvariablen erfolgt.
        - ***Rekursion***
            
            **`Rekursion`** ist ein Programmierkonzept, bei dem eine Methode sich selbst aufruft, um eine Aufgabe in kleinere Teilprobleme zu zerlegen. Dies ermöglicht es, komplexe Probleme in einfachere, wiederholende Muster aufzuteilen und zu lösen. 
            
            In jeder rekursiven Methode gibt es einen sogenannten "Basisfall". Dies ist der Punkt, an dem die Methode aufhört, sich selbst aufzurufen und stattdessen direkt eine Antwort zurückgibt. Der Basisfall verhindert, dass die Rekursion unendlich weitergeht.
            
            Hier ein Beispiel mit der Fakultät:
            
            ```java
            public class factorial{
                public static int factorial(int number) {
                    if (number == 1) { // Basisfall
                        return 1;
                    } else {
                        return number * factorial(number - 1); // factorial wird aufgerufen
                    }
                }
            }
            ```
            
- ***Packages***
    
    Ein Package in Java wird verwendet, um zusammengehörige Klassen zu gruppieren. Man kann es sich wie einen Ordner in einem Dateiverzeichnis vorstellen. Packages werden genutzt, um Namenskonflikte zu vermeiden und einen besser wartbaren Code zu schreiben. Packages für Domain-Namen werden wie folgt gebildet: Aus `**oop.ost.ch`** wird der Paketname `**ch.ost.oop1`** erstellt**.** Also in umgekehrter Reihenfolge geschrieben. Hier ein Beispiel für `**school.ch**`: 
    
    ```java
    **Package ch.school;
    
    public class Teacher {}**
    ```
    
    ```java
    // Verzeichnis würde wie folgt aussehen
    **ch
    │
    └── school
    │   │
    │   ├── Teacher.java
    │
    ├── Main.java**
    ```
    
    Der `**school`** Ordner kann ebenfalls weitere Ordner enthalten die ebenfalls Klassen beinhalten. Siehe Verzeichnis:
    
    ```java
    **ch
    │
    └── school
    │   │
    │   ├── admin
    │   │   ├── Admin.java
    │   │   └── Staff.java
    │   │
    │   ├── students
    │   │   ├── Student.java
    │   │   └── Course.java
    │   │
    │   └── teachers
    │       ├── Teacher.java
    │       └── Subject.java
    │
    └── Main.java**
    ```
    
    Jetzt haben wir Subpackets in **`school`**. Diese sind **`admin`**, **`students`** und **`teachers`**. Wenn man jetzt in diesem Fall ein package importieren möchte, hat man zwei Möglichkeiten. 
    
    **Single-Type Imports**
    
    Ein `**Single-Type**` importiert eine bestimmte Klasse aus einem Package und ermöglicht es, diese Klasse ohne den vollen Namen zu verwenden. Kleines Beispiel:
    
    ```java
    // Importiert das Admin Package
    **import ch.school.admin.Admin;**
    
    package ch.school.students;
    
    class Student {
    	public static void main(String[] args) {
    		// Erstellt Admin-Variable
    		**Admin newAdmin = new Admin();**
    	}
    }
    ```
    
    **On-Demand Imports**
    
    **`On-Demand`** importiert alle Klassen aus einem bestimmten Package und erlaubt es, auf alle Elemente in diesem Package zuzugreifen, ohne den vollen Namen zu verwenden. Beispiel:
    
    ```java
    // Importiert alle Packages von admin
    **import ch.school.admin.*;**
    
    package ch.school.students;
    
    class Student {
    	public static void main(String[] args) {
    		// Erstellt Admin- & Staff-Variable
    		**Admin newAdmin = new Admin();
    		Staff newStaff = new Staff();**
    	}
    }
    ```
    
    **WICHTIG ZU BEACHTEN**
    
    - Gleichwertige Pakete mit dem selben Namen, ergeben eine Fehlermeldung
    - Ein Single-Type Paket steht an höchstem Rang
    - Eine Klasse aus dem selben Paket hat einen höheren Rang als eine On-Demand Klasse, aber niedriegeren als ein Single-Type Paket
    
    ```java
    // Szenario 1 Single-Type - Single-Type
    import paket1.A;
    import paket2.A;
    A newA = new A();
    // Resultat --> Fehlermeldung, weil beide Gelichwertige Pakete sind
    
    ------------------------------------------------------------------------------------
    
    // Szenario 2 Single-Type - eigene Klasse
    import paket1.A;
    class A{}
    A newA = new A();
    // Resultat --> Objekt von Single-Type Paket wird erstellt
    
    ------------------------------------------------------------------------------------
    
    // Szenario 3 On-Demand - On-Demand
    import paket1.*; // Beinhaltet Klasse A, B
    import paket2.*; // Beinhaltet Klasse A, C
    A newA = new A();
    // Resultat --> Fehlermeldung, weil beide Gelichwertige Pakete sind
    
    ------------------------------------------------------------------------------------
    
    // Szenario 4 On-Demand - eigene Klasse
    import paket1.*; // Beinhaltet Klasse A, B
    class A{}
    A newA = new A();
    // Resultat --> Objekt von eigener Klasse wird erstellt
    ```
    
- ***Vererbung von Klassen***
    - ***Polymorphismus***
        
        Beim `**Typ-Polymorphismus**` handelt es sich um ein Objekt das nicht nur den Typ seiner Klasse, sondern auch den Typen seiner Superklasse annehmen kann. Z.b. hat das **`Car`**-Objekt den Typ `**Car**`, **`Vehicle`** und **`Object`**.  Wo `**Vehicle**` verlangt wird, kann auch **`Car`** benutzt werden. 
        
        Statischer und Dynamischer Typ
        
        ![Untitled](Objektorientierte%20Programmierung%201%20db29bc8cecd240f78c41c2ec06bbbedf/Untitled%204.png)
        
        Der **`statische Typ`** ist der Datentyp, der zur Kompilierzeit bekannt ist und bei der Deklaration von Variablen oder Parametern festgelegt wird. Der Compiler verwendet den statischen Typ, um auf Eigenschaften und Methoden zuzugreifen und Fehler zur Compilezeit zu überprüfen.
        
        Der **`dynamische Typ`** ist der tatsächliche Datentyp eines Objekts zur Laufzeit. Er wird zur Laufzeit ermittelt und kann sich je nach der konkreten Instanz des Objekts ändern. Der dynamische Typ wird zur Laufzeit verwendet, um auf die spezifischen Implementierungen von Methoden zuzugreifen.
        
        Code Beispiel: 
        
        ```java
        // Statischer Typ ist immer vor dem Variablennamen
        **Vehicle** myVehicle;
        
        // Dynamischer Typ nach dem gleich das "new Auto()"
        Vehicle myVehicle = **new Car();**
        ```
        
        Wenn der Dynamische Typ (`**Car**`) eine Subklasse vom Statischen Typen (`**Vehicle**`) ist und die Car Klasse die Methode der Vehicle Klasse @Overridet dann wird die @Overridete Car-Klasse aufgerufen. 
        
        Code Beispiel für ein besseres Verständnis:
        
        ```java
        class Vehicle {
            void move() {
                System.out.println("Das Fahrzeug bewegt sich.");
            }
        }
        
        class Car extends Vehicle {
            @Override
            void move() {
                System.out.println("Das Auto bewegt sich.");
            }
        
            public static void main(String[] args) {
              **Vehicle vehicle1 = new Car();
              Car car1 = new Car();
              Vehicle vehicle2 = new Vehicle();
        
              vehicle1.move(); // Ruft "Das Auto bewegt sich." aus
              car1.move();     // Ruft "Das Auto bewegt sich." aus
              vehicle2.move(); // Roft "Das Fahrzeug bewegt sich." aus**
          }
        }
        
        ```
        
        Wenn jetzt aber eine neue Methode in der Car-Klasse erstellt wurde, kann vehicle1 diese Methode nicht aufrufen, weil die Referenzvariable vehicle1 nur bist zur Oberklasse Vehicle sieht und nicht auf die Methoden und Eigenschaften in der Unterklasse Car zugreifen kann. 
        
        ```java
        class Vehicle {
           
        }
        
        class Car extends Vehicle {
            void move() {
                System.out.println("Das Auto bewegt sich.");
            }
        
            public static void main(String[] args) {
              **Vehicle vehicle1 = new Car();
              Car car1 = new Car();
              Vehicle vehicle2 = new Vehicle();
        
              vehicle1.move(); // Gibt eine Fehlermeldung aus, da es move() nicht kennt
              car1.move();     // Ruft "Das Auto bewegt sich." aus**
          }
        }
        ```
        
    - ***Final***
        
        Final-Variablen
        
        - Eine **`final`**Variable in Java ist eine Konstante, deren Wert nach der Initialisierung nicht mehr geändert werden kann.
        - Sie muss bei der Deklaration oder im Konstruktor initialisiert werden und kann danach nicht mehr geändert werden.
        - Die Konstante muss dann immer gross geschrieben sein. Wie Z.b. **`PI`** oder **`DATE`**
        
        ```java
        final double PI = 3.14;
        ```
        
        Final-Methoden
        
        - Eine **`final`**Methode ist eine Methode in einer Klasse, die nicht in Unterklassen überschrieben werden kann.
        - Sie wird in der Oberklasse als **`final`** deklariert, um sicherzustellen, dass ihre Implementierung nicht geändert wird.
        - Dies ist nützlich, wenn man verhindern möchte, dass Unterklassen das Verhalten einer bestimmten Methode ändern.
        
        ```java
        class BaseClass {
            **final void finalMethod() {
                System.out.println("Dies ist eine `final`-Methode in der Basisklasse.");
            }**
        }
        
        class DerivedClass extends BaseClass {
            **// Versuch, die `final`-Methode zu überschreiben, führt zu einem Fehler
            // void finalMethod() {
            //     System.out.println("Dies ist eine überschriebene `final`-Methode.");
            // }**
        
        		public static void main(String[] args) {
        	        BaseClass base = new BaseClass();
        	        base.finalMethod();  // Aufruf der `final`-Methode aus der Oberklasse
        	    }
        }
        
            
        ```
        
        Final-Klassen
        
        - Eine **`final`**Klasse ist eine Klasse, die nicht abgeleitet werden kann. Das bedeutet, dass keine anderen Klassen von ihr erben können.
        - Dies wird verwendet, wenn man sicherstellen möchte, dass keine Unterklassen erstellt werden, um das Verhalten der Oberklasse zu ändern.
        
        ```java
        **final class FinalClass {
            void displayMessage() {
                System.out.println("Dies ist eine Methode in der `final`-Klasse.");
            }
        }**
        
        **// Versuch, von der `final`-Klasse abzuleiten, führt zu einem Fehler
        // class SubClass extends FinalClass {
        //     void displayMessage() {
        //         System.out.println("Dies ist eine überschriebene Methode in der abgeleiteten Klasse.");
        //     }
        // }**
        ```
        
    - ***Type Casts***
        
        
        | Upcasting:
        Upcasting tritt auf, wenn einn Objekt einer Unterklasse in eine Referenzvariable der Oberklasse umgewandelt wird. Upcasting ist sicher und erfordert normalerweise keine explizite Typumwandlung, da die Unterklasse alle Eigenschaften und Methoden der Oberklasse erbt. |
        | --- |
        | Downcasting:
        Downcasting tritt auf, wenn ein Objekt der Oberklasse in eine Referenzvariable der Unterklasse umgewandelt wird. Downcasting erfordert eine explizite Typumwandlung. |
        
        ![Untitled](Objektorientierte%20Programmierung%201%20db29bc8cecd240f78c41c2ec06bbbedf/Untitled%205.png)
        
        ```java
        class Vehicle {
            void move() {
                System.out.println("Das Fahrzeug bewegt sich.");
            }
        }
        
        class Car extends Vehicle {
            void accelerate() {
                System.out.println("Das Auto beschleunigt.");
            }
        		public static void main(String[] args) {
                **// Upcasting
        				// Ein Objekt der Car-Klasse wird in eine Vehicle-Referenz umgewandelt
                Vehicle vehicle1 = new Car();**
        
                **// Downcasting
                if (vehicle1 instanceof Car) {
        						// Umwandlung der Vehicle-Referenz in eine Car-Referenz
                    Car car = (Car) vehicle1; 
                    car.accelerate(); // Wird "Das Auto beschleunigt" ausgegeben
                }**
            }
        }
        ```
        
    - ***Hiding***
        
        Bei **`Hiding`** handelt es sich um die Verdeckung oder Ausblendung von Oberklassenvariablen in einer Unterklasse, was bedeutet, dass sowohl die Oberklasse als auch die Unterklasse denselben Variablennamen für eine Variable verwenden. Hier ein Beispiel dazu:
        
        ```java
        class Base {
            int value = 10;
        }
        
        class Derived extends Base {
            int value = 20; // Hiding: Die Variable "value" in Derived verdeckt die Variable in Base.
        
        		public static void main(String[] args) {
        	        Derived derived = new Derived();
        	        System.out.println(derived.value); // Gibt 20 aus (Zugriff auf die verdeckte Variable in Derived).
        	        
        	        Base base = derived;
        	        System.out.println(base.value); // Gibt 10 aus (Zugriff auf die Variable in Base).
        	    }
        }
        ```
        
        Mit dem Variablennamen oder **`this.Variablenname`** kann auf die Variable der eigenen Klasse zugegriffen werden. Mit **`super.Variablenname`** oder auch **`((Oberklasse)this).Variablenname`** kann auf die Variable der Oberklasse zugegriffen werden. Hier ist ein Beispielcode, der die Verwendung von **`this`** und **`super`** zur Variablenzugriff veranschaulicht:
        
        ```java
        class Tier {
            String name = "Unbekannt";
        }
        
        class Hund extends Tier {
            String name = "Bello";
        
            void zugriffAufNamen() {
                String eigenerName = this.name;                        // Zugriff auf den Namen des eigenen Hundes
                String tierName = super.name;                          // Methode für Zugriff auf den Namen des allgemeinen Tierobjekts
        				String tierName2 = ((Tier)this).name                   // 2te Methode für Zugriff auf den Namen des allgemeinen Tierobjekts
                System.out.println("Eigener Name: " + eigenerName);
                System.out.println("Tier Name: " + tierName);
        				System.out.println("Tier Name2: " + tierName2);
            }
        }
        
        public class Main {
            public static void main(String[] args) {
                Hund meinHund = new Hund();
                meinHund.zugriffAufNamen();
            }
        }
        ```
        
    - ***Abstrakte Klassen***
        
        **`Abstrakte Klassen`** in Java dienen als Oberklassen, können jedoch selbst nicht zur Instanziierung von Objekten verwendet werden. Sie werden oft verwendet, um gemeinsame Eigenschaften und Fähigkeiten für eine Gruppe von spezifischeren Unterklassen zu definieren. Abstrakte Klassen und Methoden werden mit dem Schlüsselwort **`abstract`** deklariert. Abstrakte Klassen können normale Methoden besitzen und diese Methoden werden normal vererbt an die Unterklassen. Siehe Methode **`hall()`**; im Beispiel unten.
        
        Abstrakte Methoden sind Methoden die einer Abstrakten Klasse angehören.  Unterklassen der Abstrakten Klasse müssen die abstrakten Methoden überschreiben und eine Implementierung bereitstellen. Wenn das nicht gemacht wird, kommt es zu einem Compilerfehler. 
        
        Beispiel einer Abstrakten Klasse:
        
        ```java
        // Abstrakte Klasse Vehicle
        **public abstract class Vehicle** {
        
            **public abstract void start();
        
            public abstract void stop();**
        
        		public void hello() {
        			System.out.println("Hello World!");
        	}
        }
        
        // Unterklasse Car
        public class Car extends Vehicle {
            // Weitere Eigenschaften und Methoden spezifisch für Autos
            private String brand;
            private String model;
        
            public Car(String brand, String model) {
                this.brand = brand;
                this.model = model;
            }
        
            public void displayInfo() {
                System.out.println("Brand: " + brand);
                System.out.println("Model: " + model);
            }
        
        		**// Überschreiben der Abstrakten Methoden**
        		**@Override
            public void start() {
                System.out.println("Das Auto wird gestartet.");
            }
        		@Override
            public void stop() {
                System.out.println("Das Auto wird gestoppt.");
            }**
        		
        	public static void main(String[] args) {
        		**Vehicle myVehicle = new Vehicle(); // FUNKTIONIERT NIIICHT!!!!
        		Car myCar = new Car("BMW", "BMW iX");
        
        		// hello-Methode wird an die Unterklasse normal weitervererbt
        		myCar.hello();**
        		
        	}
        }
        ```