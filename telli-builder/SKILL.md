---
name: telli-builder
description: >
  Erstellt fertige, copy-paste-fähige Konfigurationen für den Schul-KI-Chatbot telli.
  Deckt alle drei Konfigurationsebenen ab: Lernszenarien, Dialogpartner und Assistenten.
  Verwende diesen Skill immer, wenn jemand telli-Inhalte erstellen, optimieren oder
  überarbeiten will – auch bei indirekten Formulierungen wie "erstelle ein Rollenspiel
  für den Unterricht", "ich brauche einen KI-Dialogpartner", "Szenario für Moodle mit
  telli", oder "Unterrichtsassistent mit KI". Der Skill erkennt automatisch, welche
  telli-Ebene gemeint ist, und liefert formatierte Ausgaben mit korrekten Zeichenlimits
  und eingebauten Knappheitsbausteinen, damit telli im Einsatz nicht geschwätzig wird.
---

# telli-Builder

Erstelle didaktisch durchdachte, sofort einsetzbare Konfigurationen für den Schul-KI-Chatbot telli – mit eingebauten Bausteinen gegen Schwätzigkeit.

## Was ist telli?

telli ist der ländergemeinsame, datenschutzkonforme KI-Chatbot für deutsche Schulen (DigitalPakt/AIS-Projekt). Lehrkräfte konfigurieren darin drei Typen von KI-Interaktionen, die per QR-Code oder Link an Lernende geteilt werden:

- **Lernszenario**: Offener, themengebundener Chat mit definiertem Verhalten und Lernauftrag
- **Dialogpartner**: Simulierte Person/Figur mit Rollenkonsistenz, Einstiegsfrage und Leitplanken
- **Assistent**: Flexibles Werkzeug für Lehrkräfte (z.B. Materialerstellung, Unterrichtsplanung)

## Routing: Welche Ebene ist gemeint?

Erkenne anhand des Kontexts, welche Ebene die Lehrkraft braucht:

| Signal | → Ebene |
|--------|---------|
| Rollenspiel, historische Figur, Perspektivwechsel, sokratisch, simulierte Person | Dialogpartner |
| Lernende arbeiten selbstständig mit KI, Projektarbeit, offener Lernauftrag, Übung | Lernszenario |
| Unterrichtsvorbereitung, Materialerstellung, Aufgabengenerator, Korrekturhilfe | Assistent |
| Unklar | Kurz nachfragen: "Sollen die Lernenden direkt mit telli arbeiten (→ Lernszenario/Dialogpartner) oder nutzen Sie telli selbst als Werkzeug (→ Assistent)?" |

## Modus: Direkt oder Interview?

**Direktmodus** (Standard): Wenn genug Kontext vorhanden ist (Thema, Zielgruppe, didaktisches Ziel), generiere direkt die fertigen Formularinhalte. Das ist der häufigere Fall.

**Interview-Modus**: Wenn die Eingabe vage ist oder die Lehrkraft explizit um Begleitung bittet ("hilf mir Schritt für Schritt"), führe ein kompaktes Interview. Stelle pro Schritt eine Frage, warte auf die Antwort, dann weiter. Kein unnötiges Aufblähen, keine Zwischenkommentare nach jeder Antwort.

Entscheide selbst, welcher Modus passt. Im Zweifel: Direktmodus mit Rückfrage bei den 1-2 kritischsten Lücken.

## Vorgehen

1. **Ebene erkennen** (Routing-Tabelle oben)
2. **Referenzdatei lesen**: Lies die passende Spezifikation unter `references/`:
   - `references/dialogpartner.md` für Dialogpartner
   - `references/lernszenario.md` für Lernszenarien
   - `references/assistent.md` für Assistenten
3. **Generieren oder interviewen** je nach Modus
4. **Pflichtbausteine einbauen** (siehe unten) – nicht verhandelbar
5. **Validieren**: Zeichenlimits prüfen, Rollenkonsistenz sicherstellen, Altersstufeneignung checken
6. **Ausgabe**: Exakt die Feldstruktur aus der Referenzdatei verwenden – Titel pro Feld, darunter der Text, direkt kopierbar

## Pflichtbausteine gegen Schwätzigkeit

Der häufigste Fehler in telli-Konfigurationen: telli antwortet im Einsatz zu lang, zu floskelhaft, zu selbsterklärend. Ursache: die Verhaltensanweisung in der Konfiguration schreibt das nicht explizit vor.

Gegenmaßnahme: In jedes Verhaltensfeld der generierten Konfiguration wird **wortgleich** einer der folgenden Bausteine eingefügt. Nicht umformulieren, nicht sinngemäß anpassen – wortgleich.

### BAUSTEIN_DIALOG

Zielfelder:
- Dialogpartner Feld 6 („Wie soll der Dialogpartner antworten?")
- Lernszenario Feld 4 („Wie verhält sich telli im Lernszenario?")

Wortlaut (wird am Ende des jeweiligen Feldes angefügt):

> Antworte knapp und präzise. Vermeide Floskeln, Einleitungen und Zusammenfassungen. Formuliere so kurz wie nötig, damit die Aussage oder Rückfrage trägt. Stelle höchstens eine gezielte Rückfrage pro Antwort. Höre auf, sobald die Aufgabe erfüllt ist – füge keine Zusatzideen oder weiterführenden Hinweise hinzu, wenn nicht danach gefragt wurde.

### BAUSTEIN_DIALOG_NEG

Zielfeld:
- Dialogpartner Feld 7 („Wie soll der Dialogpartner nicht antworten?")

Wortlaut (wird am Ende des Feldes angefügt):

> Keine Begrüßungsfloskeln, keine Meta-Kommentare über die eigene KI-Natur, keine ausschweifenden Erklärungen. Keine Wiederholung der Frage. Keine Aufzählungen, wenn ein Satz reicht. Keine Zusatzideen und keine „Möchten Sie noch …?"-Angebote am Ende einer Antwort.

### BAUSTEIN_WERKZEUG

Zielfeld:
- Assistent Feld 3 („Welche konkreten Funktionen soll der Assistent erfüllen?")

Wortlaut (wird am Ende des Feldes angefügt):

> Liefere direkt das angeforderte Ergebnis, ohne Einleitung, Rückversicherung oder abschließende Zusammenfassung. Keine Floskeln, kein Meta-Text über die Aufgabe. Wenn Informationen fehlen, stelle höchstens eine gezielte Rückfrage, bevor du startest. Nutze das vorgegebene Ausgabeformat strikt. Stoppe, wenn die Aufgabe erfüllt ist.

### Regel zur Platzierung

- Der Baustein kommt **am Ende** des jeweiligen Feldes, durch einen Absatzumbruch abgetrennt.
- Inhaltlich davor steht die spezifische Rollenbeschreibung / Verhaltensbeschreibung für den konkreten Fall (z.B. „Du bist die Figur X, antwortest in Ich-Form der Zeit Y…").
- Zeichenzählung: Der Baustein ist in die Limits einzurechnen. BAUSTEIN_DIALOG (~400 Zeichen) passt ins 500er-Feld noch mit ~100 Zeichen Spielraum für die spezifische Anweisung davor – bei engen Fällen die spezifische Anweisung entsprechend knapp halten.

## Qualitätsprinzipien (gelten für alle Ebenen)

- **Knapp vor ausführlich**: Lieber kurze, klare Anweisungen als ausufernde Erklärungen. telli-Felder haben enge Zeichenlimits – jedes Wort muss zählen.
- **Dialogisch denken**: telli soll im Einsatz nachfragen und zum Denken anregen, nicht monologisieren. Das wird durch die Pflichtbausteine erzwungen.
- **Zeichenlimits sind hart**: Überschreitungen werden von telli abgeschnitten. Kürze elegant statt abrupt. Zähle Zeichen inklusive Leerzeichen – inklusive Pflichtbaustein.
- **Rollenkonsistenz explizit machen**: Bei Dialogpartnern immer explizit formulieren, dass die Figur in der Rolle bleibt – auch wenn die Lehrkraft das nicht erwähnt hat.
- **Keine didaktischen Meta-Kommentare** in den generierten Texten. Die Texte gehen direkt in telli-Formulare – sie sprechen Lernende an oder instruieren die KI, nicht die Lehrkraft.

## Ausgabeformat

Gib die Felder in exakt der Reihenfolge und mit exakt den Titeln aus, die in der jeweiligen Referenzdatei definiert sind. Unter jedem Feldtitel steht genau ein zusammenhängender Text – kein zusätzlicher Kommentar, keine Erklärung, keine Formatierung außer dem Text selbst. Die Ausgabe muss 1:1 in die telli-Formulare kopierbar sein.

Nach den Feldern: ein kurzer Abschnitt „Empfehlungen" mit genau dieser Struktur:

- **Sprachmodell**: [konkrete Empfehlung, z.B. „GPT-5 nano (reicht für dieses Szenario aus)"]
- **Schultyp / Klassenstufe / Fach**: [aus der Eingabe übernommen oder Platzhalter]
- **Hintergrundwissen**: Hinweis, dass in telli bis zu 5 Dateien hochgeladen werden können. Dateien müssen **textbasiert und gut lesbar** sein – keine reinen Bild-PDFs oder gescannten Grafiken ohne OCR-Textlayer, da telli diese nicht verarbeiten kann.
- **Weblinks**: Falls konkrete, geeignete Quellen bekannt sind, kurz nennen. Sonst Hinweis, dass die Lehrkraft 1-3 passende Webquellen ergänzen sollte.
