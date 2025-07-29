# Prinzipin

| Prinzip | Erklärung |
|---------|-----------|
| SRP                | Singe Responsibility Prinzip        : <ul> Jede Komponente hat genau eine Aufgabe. </ul>|
| SLAP               | Single Layer of Abstraction Prinzip : <ul> Anweisungen innerhalb einer Methode sollten denselben Detailgrad haben. </ul>|
| DRY                | Don´t repeat yourself               : <ul> Informationen und Logik sollte im Code nur einmal implementiert sein. </ul>|
|Fachliche Zerlegung | Teile Code so auf, dass Komponenten nur für wenige (am besten eine) Personengruppe geändert werden muss.|
| IHP                | Information Hiding Prinzip          : <ul> Komponenten sollten ihre Implementierung verstecken und nur über Schnittstellen kommunizieren. </ul>|
| Tell, don´t ask    | Wenn eine Komponente B etwas von einer Komponente A wissen, sollte A einen Getter haben. |
| LCHC               | Low Coupling, High Cohesion         : <ul> <li> Hohe Kopplung verstößt oft gegen IHP.  <li> Niedrige Kohäsion verstöß oft gegen SRP. </ul> |
| Law of Demeter     | Objekte sollten nur mit Objekten in ihrer unmittelbaren Umgebung kommunizieren (s.u.).|
| ISP                | Interface Segregation Prinzip : <ul> Interfaces sollten so klein wie möglich und so groß wie nötig sein. </ul>|
| DIP                | Dependency Inversion Principle : <ul> <li> High-level Komponenten sollten nicht von low-level Komponenten abhängen. </li> <li> Interfaces sollten nicht von Implementierungen abhängen. </li> </ul>|
| OCP                | Open-Closed Prinzip : <ul> <li> Offen für Erweiterung </li> <li> Geschlossen für Modifikation </li> </ul>|
| LSP                | Liskov’sche Substitutionsprinzip : <ul> Instanzen einer Klasse können durch Instanzen einer Unterklasse ersetzt werden. </ul> |

## FIRST

das FIRST Prinzip ist ein Prinzip fürs Testing
<ul><li>Fast<li>Independent<li>Repeatable<li>Self-validating<li>Timely</ul>

## SOLID

Die SOLID-Prinzipien sind :
- **S**RP
- **O**CP
- **L**SP
- **I**SP
- **D**IP

## Law of Demeter

Law of Demeter für Methode m aus Klasse K.  
m darf nur auf folgende Methoden zugreifen.

    class K {
        Object C;
        void m(Object B){
            Object D = new Object;
            a();                    // Methoden von K selbst
            B.b();                  // Methoden von Objekten, die als Parameter an m übergeben werden
            C.c();                  // Methoden von Objekten, die in Instanzvariablen von K abgelegt sind
            D.d();                  // Methoden von Objekten, die m erzeugt
        }
        void a(){...};        
    }


# Code Smells

| Code Smell | verletztes Prinzip | Erklärung |
| -----------|--------------------|-----------|
| Long Methode       |SRP         | lange Methoden deuten darauf hin, dass die Methode mehrere Aufgeben hat|
| Mystery Names      |            | <ul> <li>benutze erklärende Namen <li> keine Lügen </ul>|
| Kommentare         |            | <ul> <li> erkläre warum etwas passiert <li> wenn erklärt werden muss was passiert, ist der code schlecht verständlich|
| Long Parameterlist |SRP         | hat eine Methode viele Parameter kann es sein, dass sie mehrere Aufgaben hat.|
| Duplicate Code     |DRY         |   |
| Refused Bequest    |ISP <br> LSP| Unterklassen welche Methoden der Oberklassen nicht implementieren.|
| Large Class        | SRP        | ähnlich wie long Methode |
| Primitive Obsession|            | Man sollte unspezifische Datentypen (wie int, Stringe, etc.) vermeiden und eigene specifische Datentypen nutzen. |
| Data Clumps        |            | Werden verschiedene Datentypen oft zusammen genutzt, sollte man sie zu einem neuen Typ zusammenfügen. |
| Divergent Change   |SRP <br>LCHC| Wenn eine Komponente aus verschiedenen Gründen geändert werden muss. |
| Shotgun Surgery    |LCHC        | Wenn mehrere Komponenten geändert werden müssen wenn wir ein Feature ändern. |
| Feature Envy       |LCHC<br>Tell, don´t ask| Wenn eine Komponente oft auf eine andere zugreift. |
| Message Chains     |Law of Demeter| Wenn gegen das Law of Demeter verstoßen wird. Z.B.: Warenkorb.getProdukt().getPreis()|

### Weitere nicht erwähnte Codesmells:

| Code Smell | verletztes Prinzip | Erklärung |
| -----------|--------------------|-----------|
| Dead Code          |            | Nicht mehr genutzter oder erreichbarer Code, der entfernt werden sollte. |
| God Object         | SRP        | Eine Klasse, die zu viele Verantwortlichkeiten übernimmt und dadurch sehr groß und unübersichtlich wird. |
| Speculative Generality |        | Code, der für zukünftige Anforderungen geschrieben wurde, die (noch) nicht benötigt werden. |
| Lazy Class         |            | Eine Klasse, die zu wenig Funktionalität hat und eigentlich überflüssig ist. |
| Temporary Field    |            | Felder, die nur unter bestimmten Bedingungen genutzt werden und sonst leer bleiben. |
| Middle Man         |            | Eine Klasse, die fast alle Aufrufe nur an andere Objekte weiterleitet und selbst kaum Logik enthält. |

# Refactoring-Techniken

| Technik                | Behebt Code Smell | Erklärung |
|------------------------|------------------|-----------|
| Extract Method         | Long Method<br>Duplicate Code | Teile einen langen Codeabschnitt in eine eigene Methode aus, um Übersichtlichkeit und Wiederverwendbarkeit zu erhöhen. |
| Rename                 | Mystery Names | Benenne Variablen, Methoden oder Klassen um, damit sie aussagekräftiger sind. |
| Move                   | Feature Envy<br>Large Class<br>Middle Man | Verschiebe Methoden oder Felder in eine passendere Klasse. |
| Inline                 | Lazy Class<br>Temporary Field | Ersetze eine Methode oder Variable durch ihren Inhalt, wenn sie nur einmal verwendet wird. |
| Extract Class          | Large Class<br>God Object<br>Divergent Change | Teile eine große Klasse in mehrere kleinere Klassen mit klaren Verantwortlichkeiten auf. |
| Replace Temp with Query| Temporary Field | Ersetze temporäre Variablen durch Methodenaufrufe, um Klarheit zu schaffen. |
| Encapsulate Field      | Data Clumps<br>Primitive Obsession | Mache Felder privat und stelle Getter/Setter bereit, um Kapselung zu verbessern. |
| Introduce Parameter Object | Data Clumps<br>Long Parameter List | Fasse mehrere zusammengehörige Parameter zu einem eigenen Objekt zusammen. |
| Remove Dead Code       | Dead Code | Entferne nicht mehr verwendeten oder erreichbaren Code. |

# Polymorphismen

### ad-hoc Polymorphismus

<ul>
    <li> 
        Methodenoverloading :
        <ul> mehrere Methoden mit dem gleichen Namen, aber unterschiedlichen Parametern. </ul>
    </li>
    <li>
        Operatoroverloading :
        <ul> Operatoren wie + , - , * etc funktionieren für verschiedene Objekte. </ul>
    </li>
</ul>

### parametrische Polymorphismus

<ul>
    <li>
        Typ-Parameter :
        <ul> In Java als Generics zu finden. </ul>
    </li>
</ul>

### Vererbungspolymorphismus

<ul>
    <li>
        Overwriting Methodes :
        <ul> 
            Eine Methode einer Klasse kann in verschiedenen Subklasen verschiedene Implementierungen haben.
            Wird @Overwrite genutzt so handelt es sich oft um
            einen Vererbungspolymorphismus.
        </ul>
    </li>
</ul>

## Kopplungsarten

| Kopplungsart         | Erklärung |
|----------------------|-----------|
| Datenkopplung        | Zwei Komponenten tauschen nur Daten (z.B. primitive Werte, Objekte) aus. |
| Kontrollkopplung     | Eine Komponente steuert das Verhalten einer anderen durch Kontrollinformationen (z.B. Flags). |
| Stempelkupplung      | Komponenten teilen sich eine Datenstruktur, nutzen aber nur einen Teil davon. |
| Externe Kopplung     | Komponenten sind über externe Systeme (z.B. Datenbanken, Dateien) verbunden. |
| Inhaltliche Kopplung | Eine Komponente greift direkt auf die Daten einer anderen zu (z.B. auf deren Felder) – stärkste Form der Kopplung. |
| Aufrufkopplung       | Eine Komponente ruft Methoden einer anderen direkt auf. |
| Vererbungskopplung   | Kopplung durch Vererbungsbeziehungen zwischen Klassen. |
| Testkopplung         | Testcode ist zu stark an die Implementierung des Produktivcodes gebunden, z.B. durch direkte Nutzung privater Felder, zu spezifische Assertions oder häufige Änderungen der Tests bei Refactorings. |

# Dependency Injection

Dependency Injection ist ein Entwurfsmuster, bei dem Abhängigkeiten (z.B. Objekte, die eine Klasse benötigt) von außen übergeben werden, anstatt sie selbst zu erzeugen. <br>
Dadurch können wir bein Testen FakeObjekte übergeben. 

Beispiel: Ein Service bekommt eine Datenbank-Verbindung als Parameter im Konstruktor übergeben, statt sie selbst zu erzeugen.
