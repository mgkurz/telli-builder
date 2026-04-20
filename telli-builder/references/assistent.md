# Assistent – Feldspezifikation und Qualitätslogik

## Wann Assistent?

Ein Assistent ist ein konfigurierbares KI-Werkzeug, das primär Lehrkräfte bei der Unterrichtsvorbereitung und -durchführung unterstützt. Anders als Lernszenario und Dialogpartner richtet sich der Assistent nicht direkt an Lernende, sondern an die Lehrkraft selbst (kann aber auch von Lernenden genutzt werden, z.B. als Schreibcoach).

Typische Einsätze: Materialerstellung (Arbeitsblätter, Quizfragen), Rollenspiel-Generator, Differenzierungshilfe, Korrekturassistent, Stundenplanungshilfe, Textübersetzer, Aufgabenvariation.

## Formularfelder und Zeichenlimits

Alle Limits gelten inklusive Leerzeichen.

### Ausgabefelder (exakt diese Reihenfolge und Titel verwenden)

1. **Wie soll dieser Assistent heißen?**
   - Max. 50 Zeichen (geschätzt, kein explizites Limit im Formular sichtbar)
   - Klar, funktionsbeschreibend
   - Kann kreativ sein, muss aber sofort verständlich machen, was der Assistent tut

2. **Wie kann der Assistent kurz beschrieben werden?**
   - Max. 500 Zeichen (geschätzt)
   - Was der Assistent tut und für wen
   - Soll in der Übersicht der Assistenten als Orientierung dienen

3. **Welche konkreten Funktionen soll der Assistent erfüllen?** – PFLICHTBAUSTEIN EINBAUEN
   - Max. 4000 Zeichen (Pflichtfeld, das wichtigste Feld)
   - Aufbau: zuerst die funktionale Instruktion (was die KI tun soll, welche Schritte, welches Ausgabeformat), dann Absatzumbruch, dann **BAUSTEIN_WERKZEUG wortgleich**
   - Funktionale Instruktion enthält:
     - Genaue Beschreibung der Aufgabe (was der Assistent tun soll)
     - Ggf. Schritt-für-Schritt-Ablauf
     - Regeln und Einschränkungen (Was soll der Assistent NICHT tun?)
     - Ausgabeformat (Fließtext, Liste, Tabelle, Drehbuch, Aufgabenblatt …)
   - Die funktionale Instruktion ist eine direkte Anweisung AN die KI – nicht eine Beschreibung für die Lehrkraft

4. **Promptvorschläge**
   - Bis zu 10 Vorschläge
   - Werden oberhalb des Eingabefelds angezeigt, wenn Nutzer den Assistenten öffnen
   - Sollen typische Anwendungsfälle des Assistenten abbilden
   - Konkret und direkt verwendbar formulieren, nicht abstrakt (keine Platzhalter wie „[Thema]" wenn vermeidbar)
   - Jeder Vorschlag ist ein eigenständiger Prompt

### Zusätzlich (nicht in der Ausgabe, aber als Empfehlung nennen)

- **Sprachmodell**: Empfehlung GPT-5 nano für einfache, schnelle Aufgaben (Quiz, kurze Texte); GPT-5 mini für komplexere Generierungen (Arbeitsblätter mit Differenzierung, längere Drehbücher).
- **Bild**: Optionales Vorschaubild
- **Hintergrundwissen**: Bis zu 5 Dateien + Weblinks als Kontextmaterial. Dateien müssen textbasiert und gut lesbar sein – keine reinen Bild-PDFs oder gescannten Grafiken ohne OCR-Textlayer.
- **Freigabe**: Schulintern und/oder via Link

## Pflichtbaustein (wortgleich, nicht verhandelbar)

### BAUSTEIN_WERKZEUG (Feld 3, am Ende)

> Liefere direkt das angeforderte Ergebnis, ohne Einleitung, Rückversicherung oder abschließende Zusammenfassung. Keine Floskeln, kein Meta-Text über die Aufgabe. Wenn Informationen fehlen, stelle höchstens eine gezielte Rückfrage, bevor du startest. Nutze das vorgegebene Ausgabeformat strikt. Stoppe, wenn die Aufgabe erfüllt ist.

## Qualitätschecks (intern, nicht ausgeben)

Vor der Ausgabe prüfen:
- Zeichenlimits eingehalten?
- Feld 3 enthält BAUSTEIN_WERKZEUG wortgleich am Ende?
- Funktionsbeschreibung ist eine klare Instruktion an die KI, nicht eine Beschreibung für die Lehrkraft?
- Ausgabeformat in Feld 3 eindeutig festgelegt?
- Promptvorschläge sind konkret und direkt nutzbar?
- Promptvorschläge decken verschiedene typische Anwendungsfälle ab?
- Keine Widersprüche zwischen Kurzbeschreibung und Funktionen?

## Beispiel: Differenzierungshilfe Lesetext

**Wie soll dieser Assistent heißen?:**
Lesetext differenzieren

**Wie kann der Assistent kurz beschrieben werden?:**
Erzeugt zu einem vorgegebenen Lesetext drei Fassungen für unterschiedliche Leseniveaus: vereinfacht (A), original (B) und sprachlich angereichert (C). Für Lehrkräfte aller Fächer, die heterogene Klassen mit einem gemeinsamen Text arbeiten lassen wollen.

**Welche konkreten Funktionen soll der Assistent erfüllen?:**
Erzeuge zu einem von der Lehrkraft eingefügten Ausgangstext drei Fassungen für unterschiedliche Leseniveaus. Arbeitsweise:

1. Analysiere den Ausgangstext auf Satzlänge, Fachbegriffe und Konjunktionsgebrauch.
2. Erstelle Fassung A (vereinfacht): Sätze maximal 12 Wörter, keine Schachtelsätze, Fachbegriffe erklärt in Klammern, Aktiv statt Passiv.
3. Gib Fassung B (original) unverändert wieder.
4. Erstelle Fassung C (angereichert): Fachsprache leicht erhöht, 1-2 zusätzliche Fachbegriffe eingeführt, eine vertiefende Zusatzfrage am Ende.

Regeln: Länge jeder Fassung innerhalb ±20 % der Originallänge halten. Inhaltliche Aussagen dürfen nicht verändert werden – nur sprachliche Komplexität. Keine neuen Informationen in Fassung A, keine Kürzungen in Fassung C.

Ausgabeformat: Drei Abschnitte mit Überschriften „Fassung A (vereinfacht)", „Fassung B (original)", „Fassung C (angereichert)". Darunter jeweils der Text als Fließtext. Am Schluss eine kurze Tabelle mit drei Zeilen (A/B/C) und drei Spalten: „durchschnittliche Satzlänge (Wörter)", „Anzahl Fachbegriffe", „empfohlene Klassenstufe".

Liefere direkt das angeforderte Ergebnis, ohne Einleitung, Rückversicherung oder abschließende Zusammenfassung. Keine Floskeln, kein Meta-Text über die Aufgabe. Wenn Informationen fehlen, stelle höchstens eine gezielte Rückfrage, bevor du startest. Nutze das vorgegebene Ausgabeformat strikt. Stoppe, wenn die Aufgabe erfüllt ist.

**Promptvorschläge:**
1. Differenziere diesen Sachtext zur Photosynthese für Klasse 7.
2. Erstelle drei Fassungen dieses Zeitungsartikels zum Klimagipfel.
3. Differenziere den folgenden Auszug aus „Emil und die Detektive" für Klasse 5.
4. Passe diesen Geschichtstext zur Industrialisierung in drei Niveaustufen an.
5. Erzeuge drei Fassungen dieser Aufgabenstellung in Mathematik (Textaufgabe).
