## Aufgaben zu Kapitel 5

- Weshalb besitzt die Klasse Math keinen Konstruktor?
	- Die Methoden der Klasse`Math`sind ***statisch*** deklariert und können "direkt" - ohne instanziiertes Objekt - aufgerufen werden.
- Was ist die Rückgabe folgender Ausdrücke:
	- `Math.pow(5, 3);`
		- `125.0`
	- `Math.sqrt(81);`
		- `9.0`
	- `Math.abs(15.1 - 17);`
		- `1.9`
	- `Math.ceil(4.5);`
		- `5.0`
	- `Math.floor(4.5);`
		- `4.0`
	- `Math.round(4.5);`
		- `5`

- Schreiben Sie eine Service Methode `distance`, welche zwei Objekte vom Typ `Point` entgegennimmt und die *Euklidische Distanz* zwischen den beiden Punkten berechnet und zurückgibt.

```java
public class Point
	{ private int x, y;
	
	public Point(int x, int y) {
		this.x = x;
		this.y = y;
	}
	
	public int getX() {
		return this.x;
	}
	public int getY() {
		return this.y;
	}
}
```

**Mögliche Lösung überprüfen**
```java
public static double distance(Point a, Point b) {

	double distanceX = b.getX() - a.getX();
	double distanceY = b.getY() - a.getY();

	return Math.sqrt(Math.pow(distanceX, 2) + Math.pow(distanceY, 2));
}
```


- Definieren Sie eine Variable `num`, welche den grösstmöglichen `int` speichert.
	- `int num = Integer.MAX_VALUE;`
- „Verpacken“ Sie den Wert `3.456` in einem Objekt.
	- `Double d = 3.456;`
- Gegeben sei `input = “false“;` Weisen Sie einer Variablen `on` vom Typ `boolean` den Wahrheitswert zu, der aktuell in input gespeichert ist? (Achtung: `input` könnte auch `“true“` referenzieren.)
	- `Boolean on = Boolean.parseBoolean(input);`
- Folgende Methode kompiliert nicht. Weshalb nicht? Korrigieren Sie — der Rückgabetyp darf dabei aber nicht verändert werden!

```java
public String returnResult(int op1, int op2) {
	return op1 + op2
}
```

1. Fehlendes `;`am Ende der zweiten Zeile
2. Datentypen sind nicht übereinstimmend

```java
return Integer.toString(op1, op2);
```

```java
return op1 + op2 + "";
```

- Welche Ausgaben erzeugen folgende Schleifen?

```java
int count = 1;
while (count != 10) {
	count += 2;
	System.out.println(count);
}
```

```text
3
5
7
9
11
13
...
```

```java
int i = 1, max = 3;
while (i < max) {
	System.out.println(i);
	i++;
}
```

```text
1
2
```

```java
int i = 5;
while (i >= 0) {
	i -= 2;
	System.out.println(i);
}
```

```text
3
1
-1
```

```java
int i = 1, max = 3;
while (i < max) {
	int j = i;
	while (j >= 0) {
		System.out.println(i + " " + j);
		j--;
	}
	i ++;
}
```

```text
1 1
1 0
2 2
2 1
2 0
```

- Welche Ausgabe erzeugt das folgende Code-Fragment?

```java
ArrayList<String> names = new ArrayList<String>();
names.add("Emilie");
names.add("Maxime");
names.add(1, "Noelle");
names.add(1, "Eliane");
names.remove(2);
names.set(1, "Maya");

Iterator<String> iter = names.iterator();
while (iter.hasNext())
	System.out.print(iter.next() + " ");
	
System.out.println(names.indexOf("Noelle"));
```

```text
Emilie, Maya, Maxime
-1
```

> [!Aufgabe]
> Schreiben Sie ein Programm, das das _Hi-Lo Ratespiel_ implementiert. Das Programm soll eine zufällige ganze Zahl zwischen `1` und `100` wählen und dann den Benutzer bitten, die Zahl zu erraten.
> 
> Nach jedem Rateversuch gibt das Programm aus, ob richtig geraten wurde oder nicht. Wenn falsch geraten wurde, soll das Programm einen Tipp geben, ob die gesuchte Zahl grösser oder kleiner als der letzte Rateversuch ist. Am Schluss geben Sie aus, wie oft geraten werden musste, bis der Benutzer die Zahl erraten hat.
> 
> Nachdem der Benutzer die Zahl korrekt erraten hat, wird er gefragt, ob er nochmals spielen will. Das Ganze wiederholt sich so lange, bis sich der Benutzer nach einigen Spielen entscheidet, das Programm zu beenden.


## Vorprogrammieren der Klassen

- `AdditionTask`
- `TaskList`
- `CalculationTrainer`

```mermaid
classDiagram
	direction TD
    class CalculationTrainer {
        +main(args : String[])
    }
    class TaskList {
        -tasks : ArrayList<AdditionTask>
        +TaskList()
        +getTasks() : ArrayList<AdditionTask>
    }
    class AdditionTask {
        -MAX : int = 100
        -op1 : int
        -op2 : int
        -result : int
        -rand : Random
        +AdditionTask()
        +checkAnswer(answer : int) : boolean
        +displayTask()
        +getResult() : int
    }

    CalculationTrainer ..> TaskList
    TaskList --o AdditionTask
```



## java Code Challenge

1. Als _Palindrom_ werden Wörter, Wortreihen oder Sätze bezeichnet, die rückwärts gelesen genau denselben Text ergeben (z.B. _Rentner_ oder _Regallager_). Schreiben Sie ein Java-Programm, das eine Zeichenkette akzeptiert und überprüft, ob diese ein Palindrom ist oder nicht.
2. Schreiben Sie ein Java-Programm, das einen MD5-Hash zurückgibt. MD5 (Message-Digest-Algorithmus 5) ist eine kryptographische Funktion zur Erstellung von 128-Bit-Hashes aus Zeichenketten (obwohl die Funktion als gebrochen gilt, ist sie dennoch als Programmierübung nützlich). Recherchieren Sie den Algorithmus und schreiben Sie ein Programm, das eine alphanumerische Zeichenkette akzeptiert und den MD5-Hash für diese Zeichenkette zurückgibt.




