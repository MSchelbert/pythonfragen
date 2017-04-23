% Zusammenfassung und Selbsttest-Möglichkeit _Programmieren mit Python_ 
% Python3
% M. Schelbert
% Stand: 23.04.2017

# Einstieg

## Fragen

* Wie kann man Fehler erkennen?
* Welchen Vorteil hat der interaktive Modus? Welche Nachteile?
* Welche Bedeutung hat eine Einrückung in Python?
* Was ist die Ausgabe von

~~~python
print(42)
print("42")
print("42" * 24)
print("42 * 24")
print("42 * 24)
~~~~

## Auflösung

* Syntaxfehler werden direkt ausgegeben (meist mit möglicher Erklärung für den Fehler)
* Vorteile: Direktes Testen von Code(bausteinen), einfaches Probieren; Nachteile: Eingabe längerer Programme umständlich, wenig (End-)Benutzer freundlich
* Einrückung kennzeichnet einen Anweisungblock (Schleife, Verzweigung, Funktion, etc.)

```python
>>> print(42)
42
>>> print("42")
42
>>> print("42" * 24)
424242424242424242424242424242424242424242424242
>>> print("42 * 24")
42 * 24
>>> print("42 * 24)
SyntaxError: EOL while scanning string literal
```




# Variablen und Zuweisungen

## Fragen

* Wie wird eine Variable in Python definiert?
* Wie wird einer Variable ein Wert zugewiesen?
* Was sind zulässige Namen für Variablen?
* Was ist die Ausgabe von

```python
"LGG" == 'LGG'
```

```python
schule = "LGG"
print(schule)
print("schule")
```

```python
print(13 + 37)
print("13" + "37")
print(13 + "37")
```

------------------

* Was macht der Operator ```+=``` mit einer Variablen?
	- z.B. 
```python
x = 5
x += 3
print(x)
```
	- gibt es noch ähnliche Operatoren?


## Auflösung

* Variablen müssen nicht explizit, zum Beispiel mit einem Schlüsselwort, deklariert werden, eine Definition erfolgt direkt mit der Zuweisung eines Werts
* Variable = Wert (Gleichheitszeichen)
* Variablen müssen mit einem Buchstaben beginnen und können beliebige Zahlen, Buchstaben (keine Umlaute!) und Unterstriche enthalten. Eine gute Konvention ist möglichst aussagekräftige Namen zu benutzen und nur Kleinbuchstaben und Unterstriche zu verwenden. Mehr unter [PEP 8](https://www.python.org/dev/peps/pep-0008/)

------------------


```python
>>> "LGG" == 'LGG'
True

>>> schule = "LGG"
>>> print(schule)
LGG
>>> print("schule")
schule

>>> print(13 + 37)
50
>>> print("13" + "37")
1337
>>> print(13 + "37")
Traceback (most recent call last):
  File "<pyshell#5>", line 1, in <module>
    print(13 + "37")
TypeError: unsupported operand type(s) for +: 'int' and 'str'

>>> x = 5
>>> x += 3
>>> print(x)
8
```
* Der Operator ```variable += ding``` ersetzt den etwas umständlichen Ausdruck ```variable = variable + ding```. Daneben gibt es noch ```-=```, ```*=```, ```/=``` und einige mehr.



# Mathematische Operationen

## Fragen

* Wie ist die Reihenfolge von Rechenoperationen in Python?
* Was ist der Unterschied zwischen ```3``` und ```3.0``` in Python?
* Wie kannst du zwischen den beiden Typen wechseln?
* Wie berechnest du den Rest einer ganzzahligen Division in Python?

------------------

* Wie lassen sich folgende Werte noch schreiben bzw wie lautet das Ergebnis?

```python
5**3
2**0.5
1e6
3.141592653589793
2./8
2/8.
5e-2
```

## Auflösung

* Die Auswertungsreihenfolge (der bislang gelernten Befehle) ist ```**```, ```* / % //```, ```+ -```, ```> >= < <=```, ```!= ==```, ```not or and```
* ```3``` wird als Integer interpretiert, ```3.0```als Float
* Typenumwandlung mit ```float()``` und ```int()```
* Mit dem Befehl ```%```

```python
125
(import math) math.sqrt(2)
1000000.0
(import math) math.pi
0.25
0.25
0.05
```




# Typen und Umwandlung

## Fragen

* Wie kannst du den Typ einer Variablen herausfinden?
* Was kann man mit dem Befehl 
```python
isinstance()
```
erreichen?
* Was kommt hier heraus?

```python
float(3/9)
int(0.9999999999)
int(-1.5)
float("3,141592")
float('2.7182818284')
int('2.7182818284')
int("1337")
float("")
type(float(int(str(int(float(str(int(13.37))))))))
```

## Auflösung
* ```type(variable)``` gibt den Typ der Variablen zurück
* ```isinstance(variable, Typ)``` gibt ```True``` zurück, falls die Variable vom Typ ```Typ``` ist, ansonsten ```False```.

```python
>>> float(3/9)
0.0
>>> int(0.9999999999)
0
>>> int(-1.5)
-1
>>> float("3,141592")
----> 1 float("3,141592")
ValueError: invalid literal for float(): 3,141592
>>> float('2.7182818284')
2.7182818284
>>> int('2.7182818284')
----> 1 int('2.7182818284')
ValueError: invalid literal for int() with base 10: '2.7182818284'
>>> int("1337")
1337
>>> float("")
----> 1 float("")
ValueError: could not convert string to float: 
>>> type(float(int(str(int(float(str(int(13.37))))))))
float
```


# Eingaben

## Fragen
* Was ist der Rückgabetyp von 
```python
raw_input()
```

* Wie kann man bei print einen Zeilenumbruch verhindern?
* Wie kann man in einem String einen extra Zeilenumbruch einfügen?
* Was ist der Typ von folgender Variable?
```python
muh = float(raw_input("Kuh?"))
```

## Auflösung

* Der Rückgabetyp ist immer ```str```, also ein String.
* Ein Komma an letzter Stelle, z.B. ```print "kein Umbruch",``` oder ```print variable,```
* Mit dem Zeichen ```\n```, z.B. ```"Hier ist\nEin Zeilenumbruch"```
* ```float```




# Verzweigungen

## Fragen
* Beschreibe, was genau die ```if```-Anweisung macht
* Wie kann man weitere Ausdrücke neben folgendem testen?

```python
if ausdruck:
	print "Blah!"
```

* Was ist der Vorteil der Verwendung von ```elif``` statt hintereinander geschriebenen ```if```-Verzweigungen?
* Wie kann ich einen Ausdruck negieren?
* Bestimme den Wahrheitswert von folgenden Ausdrücken:
```python
False or 1 != 0 and 'S' == "S"
not (5 < 0) and "S" > "A"
not (not(not(not(True))) or not False + 1)
```

------------------

## BONUS
Welche Ausdrücke werden hier getestet?

```python
if 1 == 0 and zahl1 == zahl2 and string1 == string2:
	print "nope!"

if 1 == None or 1 == 0 or isinstance(1, int) or zahl1 == zahl2 or string1 == string2:
	print "yep!"
```

## Auflösung

* Mit ```if``` kann man abhängig von einem Wahrheitswert einen bestimmten Codeblock ausführen
* Man kann den ```elif```-Befehl verwenden
* ```elif``` kann eventuell zu weniger Auswertungen der Wahrheitswerte führen.
* Mit dem Ausdruck ```not```
* Die Wahrheitswerte sind
```python
>>> False or 1 != 0 and 'S' == "S"
True
>>> not (5 < 0) and "S" > "A"
True
>>> not (not(not(not(True))) or not False + 1)
True
```

------------------

* Es wird nur der erste Ausdruck (```1==0```) ausgewertet. Da er bereits falsch ist, werden die restlichen Ausdrücke nicht weiter getestet.
* Die ersten drei Ausdrücke werden getestet. Die ersten beiden sind ```false```, deshalb wird jeweils zum nächsten Ausdruck übergegangen. Der Ausdruck ```isinstance(1, int)``` ist wahr, weshalb die restlichen Ausdrücke nicht mehr evaluiert werden müssen.




# Schleifen

## Fragen
* Welche Arten von Schleifen kennst du? Was sind Vor- und Nachteile?
* Welchen Typ hat die variable ```P=[1,2,3]```?
* Wie kannst du vorzeitig aus einer Schleife "aussteigen"?
* Was bewirkt der Befehl ```continue``` in einer Schleife?
* Was ist die Ausgabe von folgenden Ausdrücken

```python
range(5)
range(1,10,2)
range(10,1,-2)
range("A")
```

## Auflösung

* ```for```- und ```while```-Schleifen
* ```P``` ist vom Typ ```list```
* Mit dem Befehl ```break```
* ```continue``` lässt alle nachfolgenden Anweisungen im Schleifenblock weg und springt zurück zum Schleifenkopf

```python
>>> range(5)
[0, 1, 2, 3, 4]
>>> range(1,10,2)
[1, 3, 5, 7, 9]
>>> range(10,1,-2)
[10, 8, 6, 4, 2]
>>> range("A")
----> 1 range("A")
TypeError: range() integer end argument expected, got str.
```
