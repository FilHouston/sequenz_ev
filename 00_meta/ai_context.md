# KI-Kontext und Richtlinien für Sequenz e.V.

## Allgemeine Prinzipien

Dieses Repository wird mit KI-Unterstützung gepflegt und entwickelt. Folgende Richtlinien sollen sicherstellen, dass der Einsatz von KI-Tools produktiv bleibt und gleichzeitig Sicherheit und Datenschutz gewährleistet sind.

---

## Wo KI verwendet werden darf

### ✅ ERLAUBT: Öffentliche Inhalte (`90_public_mirror/`)
- KI kann direkt mit Inhalten aus `90_public_mirror/` arbeiten
- Generierung von Dokumenten, Code, Prozessbeschreibungen für öffentliche Kontexte
- Keine Bedenken bezüglich Datenschutz oder Vertraulichkeit
- **Hinweis:** Ausgaben prüfen auf Haftung und Korrektheit

### ✅ ERLAUBT: Allgemeine Aufgaben (intern)
- Strukturelle Aufgaben (Verzeichnisse, Vorlagen, Boilerplate)
- Grammatik, Stil, Formatierung (ohne inhaltliche Änderungen)
- Code-Review und technische Bewertungen
- Prozess-Automationen und Skripte

### ⚠️ EINGESCHRÄNKT: Operative Inhalte (INTERNAL)
- KI darf mit INTERNAL-Inhalten arbeiten, wenn:
  - **KEINE personenbezogenen Daten** (Namen, E-Mails, Adressen) in den Prompt kommen
  - **KEINE spezifischen Zahlen/Budgets** weitergegeben werden
  - Allgemeine Struktur/Logik, Anonyme Beispiele verwendet werden
  
**Beispiel ERLAUBT:**  
> "Ich habe ein Event mit ~150 Teilnehmern. Welche Risiken sollte ich im Run-of-Show planen?"

**Beispiel NICHT ERLAUBT:**  
> "Mein Event am 15.3. mit John Smith, Sarah Müller, ... (Crewliste mit Namen)"

### ❌ VERBOTEN: Vertrauliche Inhalte (CONFIDENTIAL)
- Verträge mit Klarnamen/Konditionen
- Buchhaltung (Belege, Kontoauszüge, Ausgaben)
- Sicherheitskonzepte, Infrastruktur-Details
- Passwörter, API-Keys, IBAN-Nummern
- Interne Konflikte, HR-Belange

**Ausnahme:** Mit expliziter Genehmigung und unter strikter Anonymisierung (z.B. Redaction-Tools).

---

## Handhabung von personenbezogenen Daten (PII)

### Vor der Übergabe an KI-Tools:
1. **Anonymisieren** – Namen durch "Person A", E-Mails durch "[email]" ersetzen
2. **Minimieren** – Nur die wirklich notwendigen Daten einbeziehen
3. **Begründen** – Warum braucht die KI diese Information?

### Best Practice:
```
❌ FALSCH:
"Bitte schreib eine Einladung für Anna Schmidt (anna.schmidt@example.com), 
 die am 20.3. zur Crew gehört."

✅ RICHTIG:
"Bitte schreib eine generische Event-Crew-Einladungs-Vorlage 
 für [DATE], die die wichtigsten Punkte abdeckt."
```

### Nach der Arbeit mit KI:
- Ausgaben **vor Speicherung im Repo prüfen** auf unerwünschte Ausgaben
- Falls nötig: Wieder anonymisieren/redaktionell bearbeiten
- **Versionshistorie prüfen** – Git speichert alles!

---

## Datenschutz bei externen KI-Services

Falls externe Tools (ChatGPT, Claude, etc.) verwendet werden:

1. **Keine Klarnamen/E-Mails/IBANs** in die Prompts
2. **Anonymisieren** vor dem Kopieren (s.o.)
3. **Datenschutzerklärung prüfen** des Services
4. **Keine Langzeitspeicherung** auf Diensten (z.B. ChatGPT History deaktivieren, wo möglich)
5. **Alternative:** Lokale/selbstgehostete Tools verwenden (z.B. Ollama)

**Hinweis:** Externe Services können den Text zur Modell-Verbesserung nutzen – deshalb der Extra-Schutz bei PII.

---

## KI für Governance und Compliance

### Was KI helfen kann:
- **Satzungen/Policies schreiben** – Struktur, Entwürfe, Vorschläge
- **Checklisten generieren** – Compliance, Security, Events
- **Prozesse dokumentieren** – Flowcharts, Textbeschreibungen
- **Templates erstellen** – Verträge, Formulare, Briefe

### Was KI NICHT machen sollte:
- **Rechtsberatung** – KI kann nicht als Anwalt dienen
- **Finanzberatung** – Budgetentscheidungen müssen Menschen treffen
- **Personelle Entscheidungen** – HR/Recruitment sind Menschensache
- **Geheimhaltung garantieren** – KI-Output kann geleakt werden

---

## Code und technische Inhalte

### Für Code in `07_infrastructure/`, `08_projects/` etc.:
- KI darf Code generieren und reviewen
- **Keine Secrets/Credentials** in Code oder Prompts
- **Best Practice:** Code-Review vor Merge, auch wenn von KI generiert
- **Dokumentation:** KI-generierter Code sollte kommentiert sein

---

## Feedback und Revisions

**Wenn KI-Output problematisch ist:**

1. **Manuell korrigieren** (schneller oft als KI-Iteration)
2. **Feedback dokumentieren** – Was war falsch/problematisch?
3. **Prozess verbessern** – Bessere Prompts, andere Tools?

---

## Zusammenfassung

| Kontext | KI erlaubt? | Bedingungen |
|---------|------------|-------------|
| Öffentlich (`90_public_mirror/`) | ✅ Ja | Ausgabe prüfen, Quellen verifizieren |
| INTERNAL (ohne PII) | ✅ Ja | Keine Namen/Adressen; anonymisiert |
| INTERNAL (mit PII) | ⚠️ Mit Vorsicht | Anonymisieren, lokale Tools bevorzugt |
| CONFIDENTIAL | ❌ Nein | Nicht an externe Services, gar nicht versenden |
| Code/Tech | ✅ Ja | Mit Review; keine Secrets |
| Rechtliche/HR-Entscheidungen | ❌ Nein | Menschen entscheiden |

---

## Fragen?

Abstimmung im Team oder mit dem Governance-Committee.

**Motto:** Produktiv mit KI, aber mit Bedacht.
