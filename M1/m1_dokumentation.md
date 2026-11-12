# Dokumentation 

### Aufgabe M1 (erstell datum)

Klassen name und Attribute: 

- Kunde &#8594; Kundennummer, Name, E-Mail-Adresse
- Bestellung &#8594; Bestellnummer, Bestelldatum, Status
- Bestellposition &#8594; Menge, Einzelpreis
- Produkt &#8594; Produktnummer, Name, aktueller Preis, Lagerbestand 
- Lieferadrese &#8594; Strasse, Hausnummer, Postleitzahl, Ort, Land
- Zahlung &#8594; Betrag, Zahlungsdatum, Zahlungstatus
---
### Welche Beziehungen gibt es?

#### Kunde – Bestellung

Aus der Beschreibung:
- Ein Kunde kann beliebig viele Bestellungen aufgeben.
- Jede Bestellung gehört genau einem Kunden.
Daraus folgt:

Kunde 1 ─────────> 0..* Bestellung

Normale Assoziation

Begründung: Ein Kunde kann mehrere Bestellungen besitzen. Eine Bestellung gehört aber immer genau einem Kunden.

Keine Komposition, weil eine Bestellung nicht zwingend mit dem Kunden gelöscht werden muss.

--- 

#### Bestellposition – Produkt
Aus der Beschreibung:
- Jede Bestellposition verweist auf genau ein Produkt.
- Ein Produkt kann in mehreren Bestellungen vorkommen.
- Produkte existieren unabhängig von Bestellungen.
- Wird eine Bestellung gelöscht, darf das Produkt nicht gelöscht werden.
Bestellposition 0..* ───────── 1 Produkt

Normale Assoziation

Begründung: Hier darf keine Komposition verwendet werden. Ein Produkt kann unabhängig von einer Bestellung existieren und sogar in vielen Bestellungen vorkommen.

--- 

#### Bestellung – Lieferadresse
Aus der Beschreibung:
- Jede Bestellung besitzt genau eine Lieferadresse.
- Die Adresse wird als eigener Bestandteil der Bestellung gespeichert.
- Wird die Bestellung gelöscht, wird auch die gespeicherte Adresse gelöscht.
Bestellung 1 ◆──────── 1 Lieferadresse

(Komposition)

Begründung: Die Lieferadresse ist Bestandteil der Bestellung. Sie wird speziell für diese Bestellung gespeichert und hat in diesem Szenario keine unabhängige Existenz.

Wichtig: Auch wenn ein Kunde mehrere Bestellungen an dieselbe physische Adresse liefern lässt, werden die Adressdaten für jede Bestellung separat gespeichert.

--- 

#### Bestellung – Zahlung
Aus der Beschreibung:
- Eine Bestellung kann zunächst keine Zahlung besitzen.
- Später kann sie höchstens eine Zahlung besitzen.
- Eine Zahlung gehört immer genau zu einer Bestellung.
- Eine Zahlung soll nicht unabhängig von der Bestellung existieren.
Bestellung 1 ◆──────── 0..1 Zahlung

(Komposition)

Begründung: Die Zahlung ist vollständig an eine Bestellung gebunden und kann nicht unabhängig davon existieren. Deshalb ist eine Komposition sinnvoll.

--- 