# telli-builder

Ein **Claude-Skill** für Lehrkräfte, der fertige, copy-paste-fähige Konfigurationen für den Schul-KI-Chatbot [telli](https://telli.schule) erzeugt: Lernszenarien, Dialogpartner und Assistenten.

Der Skill enthält **Pflichtbausteine gegen Schwätzigkeit**: kurze Knappheitsregeln, die wortgleich in die Verhaltensfelder der telli-Konfiguration eingebaut werden. Dadurch antwortet telli im späteren Einsatz deutlich knapper: keine Floskeln, keine ausufernden Erklärungen, keine ungefragten Zusatzideen.

---

## Was ist ein „Skill"?

Ein Skill ist ein Erweiterungspaket für [Claude](https://claude.ai), das Claude für eine bestimmte Aufgabe Experten-Wissen mitgibt. Man lädt die Skill-Datei einmalig hoch, und ab dann erkennt Claude automatisch, wenn eine telli-Konfiguration erstellt werden soll, und arbeitet nach den hier definierten Regeln.

Skills sind ein Feature der bezahlten Claude-Accounts (Pro, Team, Enterprise).

## Für wen ist das?

Lehrkräfte, die:

* telli an ihrer Schule nutzen (aktuell Baden-Württemberg, Bayern, Brandenburg, Bremen, Hessen, Niedersachsen, NRW, Saarland, Schleswig-Holstein, Thüringen; weitere Länder folgen),
* einen Claude-Pro-Account oder höher haben,
* und regelmäßig telli-Konfigurationen erstellen.

Wer keinen Claude-Zugang hat, kann alternativ den webbasierten [telli-Konfigurator](https://mgkurz.github.io/telli-konfig/) nutzen. Dieser funktioniert mit allen gängigen KIs und braucht keine Installation.

---

## Download und Installation

### Schritt 1: Datei herunterladen

Klicke auf **[telli-builder.skill](./telli-builder.skill)** und dann auf den Download-Button rechts oben (drei Punkte oder Pfeil-Symbol).

Alternativ: Im Bereich „Releases" am rechten Rand dieser Seite findest Du die jeweils aktuellste Version.

### Schritt 2: In Claude installieren

1. Öffne [claude.ai](https://claude.ai) und melde Dich an.
2. Klicke unten links auf Dein Profil und dann auf **Einstellungen**.
3. Wähle den Bereich **Fähigkeiten** (englisch: „Capabilities") und dort **Skills**.
4. Klicke auf **Skill hochladen** und wähle die heruntergeladene `telli-builder.skill`-Datei aus.
5. Fertig.

### Schritt 3: Nutzen

Starte einen neuen Chat mit Claude und schreibe etwa:

> Erstelle mir einen telli-Dialogpartner mit Marie Curie für Klasse 9 Physik.

Claude erkennt die Absicht automatisch und liefert die fertigen Feldinhalte zum direkten Einkopieren in telli.

---

## Was der Skill kann

Drei Konfigurationstypen werden unterstützt:

**Lernszenario.** Ein themengebundener Chat-Raum, in dem Lernende selbstständig mit telli an einem Thema arbeiten (4 Felder).

**Dialogpartner.** Eine simulierte Person oder Figur, die Lernende im Gespräch begleitet und konsequent in ihrer Rolle bleibt (7 Felder).

**Assistent.** Ein KI-Werkzeug für Lehrkräfte zur Unterrichtsvorbereitung (4 Felder plus Promptvorschläge).

## Was ist besonders an diesem Skill?

Die Verhaltensfelder in telli-Konfigurationen (Dialogpartner Feld 6 und 7, Lernszenario Feld 4, Assistent Feld 3) enthalten automatisch einen fest formulierten Baustein, der telli zu knappen Antworten zwingt:

* keine Floskeln, keine Einleitungen, keine Zusammenfassungen
* maximal eine gezielte Rückfrage pro Antwort
* keine ungefragten Zusatzideen
* Schluss, sobald die Aufgabe erfüllt ist

Diese Bausteine werden **wortgleich** eingesetzt, nicht sinngemäß. Dadurch sind sie verlässlich wirksam.

---

## Disclaimer

Dieser Skill ist eine Vorlage. Die durch Claude mithilfe des Skills erzeugten telli-Konfigurationen sollten vor dem Einsatz im Unterricht fachlich und didaktisch geprüft werden. Für die generierten Inhalte übernehme ich keine Verantwortung.

telli ist ein Angebot des FWU (Institut für Film und Bild in Wissenschaft und Unterricht gGmbH) im Auftrag der 16 Bundesländer. Informationen zu telli: [telli.schule](https://telli.schule).

## Datenschutz

Das Repository wird bei GitHub gehostet (GitHub Inc., 88 Colin P. Kelly Jr St, San Francisco, CA 94107, USA). Beim Aufruf der Repository-Seite verarbeitet GitHub technische Daten, insbesondere IP-Adresse, Browser- und Betriebssysteminformationen, Referrer-URL sowie Zeitpunkt des Zugriffs. Auf diese Daten habe ich keinen direkten Zugriff. GitHub speichert diese Daten in Server-Logfiles.

Rechtsgrundlage ist Art. 6 Abs. 1 lit. f DSGVO (berechtigtes Interesse an der Bereitstellung des Repositories). GitHub ist unter dem EU-U.S. Data Privacy Framework zertifiziert und nutzt zusätzlich Standardvertragsklauseln (SCCs) als Grundlage für den Datentransfer. Weitere Informationen: [GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement).

Die Nutzung des heruntergeladenen Skills findet in Claude statt. Für die Verarbeitung dort gilt die Datenschutzerklärung von Anthropic: [anthropic.com/privacy](https://www.anthropic.com/privacy). Anthropic verarbeitet Daten außerhalb der EU. Personenbezogene Daten von Lernenden sollten nicht in die Konfigurations-Prompts eingegeben werden.

## Lizenz

[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.de): Namensnennung, Weitergabe unter gleichen Bedingungen. Der Skill darf weitergegeben, angepasst und in abgewandelter Form verteilt werden, solange die Quelle genannt wird und die bearbeitete Version unter derselben Lizenz steht.

## Hintergrund

Dieser Skill ist die Claude-Skill-Fassung meines bereits existierenden webbasierten [telli-Konfigurators](https://mgkurz.github.io/telli-konfig/). Während der Konfigurator als HTML-Seite mit beliebigen KIs funktioniert (ChatGPT, Duck AI, Claude u. a.), arbeitet dieser Skill direkt und nativ in Claude. Neu hinzugekommen sind die Pflichtbausteine gegen Schwätzigkeit und die direkte Integration in Claudes Skill-Mechanik. Feldstruktur, Zeichenlimits und didaktische Logik stammen aus dem ursprünglichen Konfigurator.

## Kontakt

Martin Kurz  
Hessische Lehrkräfteakademie, Dezernat II.3 Medien  
[martin.kurz@bildung.hessen.de](mailto:martin.kurz@bildung.hessen.de)

Verbesserungsvorschläge, Fehlermeldungen oder neue Beispiele gerne über die GitHub-Issues oder per Mail.
