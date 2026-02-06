# AI-Agenten Richtlinien für Sequenz e.V. Repository

## Zweck

Dieses Dokument ist ein **Arbeitsleitfaden für KI-Agenten und automatisierte Systeme**, die mit dem `sequenz_internal` Repository arbeiten. Es konkretisiert die Regeln aus `ai_context.md` und `mirror_rules.md` für automatisierte Workflows.

---

## Kernprinzipien

### 1. **Klassifizierung verstehen**

Bevor du eine Aufgabe startest, klassifiziere die Inhalte nach:

| Klasse | Erlaubnis | Beispiele |
|--------|-----------|----------|
| **PUBLIC** | ✅ Voll erlaubt | Satzung, Templates, öffentliche Prozesse |
| **INTERNAL** | ⚠️ Nur intern, KI-einsatz mit Vorsicht | Event-Docs, interne Prozesse |
| **CONFIDENTIAL** | ❌ Nicht mit KI | Verträge, Budgets, Infrastruktur |
| **PII** | ❌ Nicht mit KI | Namen, E-Mails, Adressen, Geburtsdaten |

**Richtlinie:** Im Zweifel → frag einen Menschen, bevor du handeln.

---

### 2. **Public Mirror ist die Single Source for Public**

- **Nur** Inhalte unter `/90_public_mirror/` dürfen öffentlich sein
- Alles andere ist **implizit intern** und **nicht öffentlich**
- KI-Agenten sollten **niemals** Inhalte aus anderen Ordnern in den Public Mirror verschieben

**Consequence:** Wenn du einen Vorschlag für öffentlichen Content machst → immer zuerst in den Fachordner, dann (nach Prüfung) in den Mirror.

---

### 3. **Datenschutz geht vor**

KI-Agenten dürfen **NICHT**:
- Personenbezogene Daten aus Commits auslesen und verarbeiten
- Namen, E-Mails, Adressen, Telefonnummern in Prompts einbeziehen
- Verträge mit Klarnamen analysieren
- IBAN, Passwörter, API-Keys je erwähnen
- Vertrauliche Geschäftsinformationen weiterleiten

**Best Practice:**
```
❌ FALSCH:
"Analysiere die Crew für das Event am 15.3. mit Namen: 
John Smith (john@example.de), Sarah Müller (sarah@example.de), ..."

✅ RICHTIG:
"Erstelle eine Vorlage für eine Event-Crew-Checkliste 
mit ~5-10 typischen Rollen."
```

---

## Konkrete Handlungsszenarien

### Szenario A: "Dokumentation für Public Mirror schreiben"

**Status:** ✅ **ERLAUBT**

**Workflow:**
1. Frage, ob der Inhalt wirklich in `90_public_mirror/` gehört
   - Enthält er personenbezogene Daten? → NEIN
   - Enthält er Budgets/Verhandlungszahlen? → NEIN
   - Wurde es explizit zur Veröffentlichung freigegeben? → JA
2. Schreibe den Content
3. Speichere direkt unter `/90_public_mirror/`
4. Commit mit klarer Beschreibung

**Beispiele:**
- Generic Rollenbeschreibungen (ohne Klarnamen)
- Public-Ready Event-Prozesse (ohne Crew-Details)
- Brand-Style-Guides (freigegebene Versionen)
- Blanko-Templates

---

### Szenario B: "Interne Prozess-Dokumentation aktualisieren"

**Status:** ⚠️ **ERLAUBT, MIT VORSICHT**

**Workflow:**
1. Lese die bestehende Datei
2. Ist es INTERNAL oder CONFIDENTIAL?
   - **INTERNAL:** KI kann helfen (Struktur, Stil, Prozess-Logik)
   - **CONFIDENTIAL:** KI sollte **NICHT** anfassen (außer strukturelle Helpers)
3. Wenn anonymisierbare Daten nötig sind:
   - Anonymisiere vor Verarbeitung ("Person A", "[email]", "[date]")
   - Gib nur das Minimum preis
4. Speichere Ergebnis im **Fachordner**, nicht im Public Mirror

**Beispiele:**
- Event-Checklisten strukturieren
- Prozessbeschreibungen formatieren
- Interne Onboarding-Guides schreiben

**Nicht erlaubtes Beispiel:**
- Finanzreports analysieren
- Verträge mit Klarnamen bearbeiten
- Sicherheitskonzepte detaillieren

---

### Szenario C: "Code/Skripte für interne Prozesse generieren"

**Status:** ✅ **ERLAUBT**

**Workflow:**
1. Code kann für Automatisierung, Datenverarbeitung, CI/CD helfen
2. **NICHT** in Skripte hardcoden:
   - Passwörter, API-Keys, IBAN-Nummern
   - Namen oder E-Mails aus Listendaten
3. Setze Variablen/Secrets voraus (z.B. `$SECRET_API_KEY`)
4. Dokumentiere deutlich: "Dieses Skript arbeitet mit sensiblen Daten"

**Beispiel-Szenario:**
```
✅ "Schreib ein Bash-Skript, das aus einer CSV-Datei 
   (Spalten: ROLLENNAME, AUFGABE) automatisch 
   eine Event-Checkliste generiert."

❌ "Schreib ein Skript, das die Crew-Liste aus events/event_2026_03.md 
   ausliest und E-Mails verschickt."
```

---

### Szenario D: "Die Struktur des Repository verbessern"

**Status:** ✅ **ERLAUBT**

**Workflow:**
1. Direkte Code/Config-Changes darf KI machen:
   - Verzeichnisstruktur reorganisieren
   - Namenkonventionen vereinheitlichen
   - Template-Struktur verbessern
2. **ABER:** Keine Inhalte dabei verschieben (außer Struktur-Helpers)
3. Dokumentiere die Änderung in der Commit-Message

**Beispiele:**
- "Reorganisiere die Ordner-Nummern logischer"
- "Erstelle ein einheitliches Header-Format für alle Dateien"
- "Schreib ein Git-Hook-Skript zur Klassifizierungs-Prüfung"

---

### Szenario E: "Fehler in öffentlichen Dokumenten fixen"

**Status:** ✅ **ERLAUBT**

**Workflow:**
1. Nur in `/90_public_mirror/` korrigieren
2. Grammatik, Rechtschreibung, Formatierung
3. **NICHT:** Inhaltliche Änderungen ohne Review

**Beispiel:**
- "Fixe Tippfehler in satzung.md"
- "Aktualisiere Links in der Brand-Dokumentation"

---

## Checkliste für AI-Agenten

Bevor du eine Aktion startest, durchlaufe diese Checkliste:

```
[ ] 1. Klassifizierung geklärt?
     - PUBLIC / INTERNAL / CONFIDENTIAL / PII?
     
[ ] 2. Darf KI damit arbeiten?
     - PUBLIC → JA, unbeschränkt
     - INTERNAL → JA, aber keine PII
     - CONFIDENTIAL → NEIN (außer Struktur-Helpers)
     - PII → NEIN (außer Anonymisierung)
     
[ ] 3. Keine sensiblen Daten in meinen Prompts?
     - Keine Klarnamen
     - Keine E-Mails
     - Keine Budgets/IBAN
     - Keine API-Keys
     
[ ] 4. Zielort richtig?
     - PUBLIC Content → `/90_public_mirror/`?
     - INTERNAL Content → Fachordner?
     - CONFIDENTIAL → Nicht mit KI bearbeitet?
     
[ ] 5. Dokumentation klar?
     - Commit-Message beschreibt die Änderung
     - Referenzen auf verwandte Dokumente?
     
[ ] 6. Mensch sollte Review?
     - Governance / Legal / Finance Inhalte → JA
     - Sicherheitskritisches → JA
     - Öffentliche Inhalte → Empfohlen
```

---

## Konkrete "Do's and Don'ts"

### ✅ DO

- Verwende `ai_context.md`, `mirror_rules.md`, `data_classification.md` als Referenz
- Anonymisiere Daten, bevor du sie verarbeitest
- Frag im Zweifelsfall → "Ist das PUBLIC, INTERNAL oder CONFIDENTIAL?"
- Nutze die Ordner-Struktur als Hinweis für Sensitivität
- Schreib hilfreiche Commit-Messages
- Dokumentiere KI-generierten Code
- Vorschlag-basiert arbeiten (Branches, PRs)

### ❌ DON'T

- Verschiebe Inhalte ohne Klassifizierungs-Check in Public Mirror
- Lese direkt aus CONFIDENTIAL Dateien und verarbeite Daten
- Ignoriere PII-Warnungen
- Speichere Passwörter, API-Keys, IBAN in versioniertem Code
- Schreib Script, die real existierende Menschen-Daten hardcoden
- Mache große Inhalts-Änderungen ohne Review-Prozess
- Vergesse, dass Git alles speichert → auch gelöschte Secrets in History

---

## Spezial: Work mit externen KI-Services

Falls ein Agent mit **ChatGPT, Claude, Gemini** etc. arbeitet (z.B. über API):

1. **IMMER anonymisieren** vor dem Senden
   ```
   ❌ FALSCH: "Event am 15.3. mit Sarah Müller, John Smith..."
   ✅ RICHTIG: "Event mit ~50 Gästen, welche Prozesse nötig?"
   ```

2. **Keine CONFIDENTIAL Daten senden** (Verträge, Budgets, IPs)

3. **Keine API-Keys / Passwörter** in Prompts

4. **Logging prüfen** – Falls der Service Prompts speichert (z.B. ChatGPT), könnte das ein Datenschutz-Risiko sein

5. **Lokale Alternative:** Falls möglich, nutze lokal gehostete Modelle (Ollama, etc.), um PII-Daten nicht hochzuladen

---

## Eskalation & Grenzen

### Wenn du unsicher bist:

1. **Schaue in die Klassifizierung:** Steht die Datei / das Feld als CONFIDENTIAL oder PII?
2. **Konsultiere die Meta-Dokumente:** `ai_context.md`, `mirror_rules.md`, `data_classification.md`
3. **Im Zweifel:** Blockiere die Aktion und hinterlasse einen **Review-Request** oder Kommentar für einen Menschen
4. **Niemals:** Rät, dass "du dir nicht sicher bist" und machweiber trotzdem

### Für zukünftige Agenten:

Falls diese Richtlinien nicht ausreichen oder ein neuer Use-Case auftaucht:
- Erstelle einen Issue im Repository mit dem Tag `[agent-question]`
- Beschreibe das Szenario konkret
- Warte auf Rückmeldung durch ein Mitglied vor Aktion

---

## Referenzen

- `ai_context.md` – Grundsätzliche KI-Richtlinien
- `mirror_rules.md` – Regeln für Public Mirror
- `data_classification.md` – Detaillierte Klassifizierung
- `INDEX.md` – Repository-Navigation
- `README.md` – Projekt-Übersicht

---

**Letzte Aktualisierung:** 2026-02-03  
**Gültig für:** Alle KI-Agenten und automatisierten Systeme, die mit diesem Repository arbeiten
