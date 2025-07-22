# Prinzipin

| Prinzip | Erklärung |
|---------|-----------|
| SRP                | Singe Responsibility Prinzip        : <ul> Jede Komponente hat genau eine Aufgabe. </ul>|
| SLAP               | Single Layer of Abstraction Prinzip : <ul> Anweisungen innerhalb einer Methode sollten denselben Detailgrad haben. </ul>|
| DRY                | Don´t repeat yourself               : <ul> Informationen und Logik sollte im Code nur einmal implementiert sein. </ul>|
|Fachliche Zerlegung | Teile Code so auf, dass Komponenten nur für wenige (am besten eine) Personengruppe geändert werden muss.|
|||
| IHP                | Information Hiding Prinzip          : <ul> Komponenten sollten ihre Implementierung verstecken und nur über Schnittstellen kommunizieren. </ul>|
| LCHC               | Low Coupling, High Cohesion         : <ul> <li> Hohe Kopplung verstößt oft gegen IHP.  <li> Niedrige Kohäsion verstöß oft gegen SRP. </ul> |
| Law of Demeter     | Objekte sollten nur mit Objekten in ihrer unmittelbaren Umgebung kommunizieren (s.u.).|
|||
| ISP                | Interface Segregation Prinzip : <ul> Interfaces sollten so klein wie möglich und so groß wie nötig sein. </ul>|


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

| Code Smell | verletztes Prinzip | Bemerkung |
| -----------|--------------------|------------|
| Long Methode       |SRP         | lange Methoden deuten darauf hin, dass die Methode mehrere Aufgeben hat|
| Mystery Names      |            | <ul> <li>benutze erklärende Namen <li> keine Lügen </ul>
| Kommentare         |            | <ul> <li> erkläre warum etwas passiert <li> wenn erklärt werden muss was passiert, ist der code schlecht verständlich|
| Long Parameterlist |SRP         | hat eine Methode viele Parameter kann es sein, dass sie mehrere Aufgeben hat.|
| Duplicate Code     |DRY         |   |
|||


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

# Dependency In...

Siehe Woche 07 im Video relativ am Ende.