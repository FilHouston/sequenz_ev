# Datenklassifizierung – Detaillierte Richtlinien

## Klassifizierungsstufen

### 1. **PUBLIC**
Inhalte, die vollständig öffentlich gemacht werden dürfen und sollen.

**Merkmale:**
- Keine personenbezogenen Daten (Namen, E-Mails, etc.) außer in generischen Beispielen
- Keine Budgetzahlen oder verhandelten Konditionen
- Keine internen Konflikte oder Entscheidungshintergründe
- Geprüfter, freigegebener Inhalt

**Beispiele:**
- Satzung (öffentliche Version)
- Generische Prozessbeschreibungen
- Öffentliche Templates (Blanko-Vorlagen)
- Brand-Assets und Presskit
- Rollenbeschreibungen ohne Klarnamen

**Ort:** `90_public_mirror/`

---

### 2. **INTERNAL**
Operative Inhalte, die intern verfügbar sein müssen, aber nicht öffentlich gehören.

**Merkmale:**
- Interne Prozesse, Checklisten, FAQs
- Entscheidungen und Protokolle mit Klarnamen
- Teilweise personenbezogene Daten
- Operative Runbooks und Guides

**Beispiele:**
- Event Run-of-Shows mit Crewlisten
- Interne Protokolle (Vorstand, Mitgliederversammlung)
- Ist-Zahlen der Buchhaltung
- Interne Onboarding-Materialien
- Projektarbeitsstände

**Ort:** Fachordner (`01_governance/`, `04_events/`, etc.) – **NICHT** im Mirror

---

### 3. **CONFIDENTIAL**
Besonders schützenswerte Inhalte mit erhöhtem Sicherheitsrisiko.

**Merkmale:**
- Verträge mit Klarnamen oder verhandelten Konditionen
- Buchhaltung: Belege, IBAN, Kontoauszüge, Auszahlungen
- Sicherheitskonzepte und Infrastruktur-Operationen
- Datenschutz- und Compliance-sensible Daten
- Interne Konflikte, HR-Belange

**Beispiele:**
- Verträge mit Partnern/Lieferanten (mit Namen/Konditionen)
- Budgets und Finanzauszüge
- Hostnamen, IPs, Backups, Zugangspfade
- Compliance-Dokumentation
- Vertrauliche Geschäftsinformationen

**Ort:** Fachordner – **NIEMALS** versioniert oder in Git

**Besonderheit:** Sollte ggf. separat (z.B. in Passwort-Managern, verschlüsselten Docs) verwahrt werden.

---

### 4. **PII (Personenbezogene Daten)**
Besondere Behandlung gemäß DSGVO.

**Definition:** Alle Informationen, die sich auf eine identifizierte oder identifizierbare Person beziehen
- Namen, Anschriften, Telefonnummern
- E-Mail-Adressen
- Geburtsdatum, Geschlecht
- IBAN/Bankkonten
- IP-Adressen, Cookies
- Vertragliche Beziehungen mit Klarnamen

**Regel:** Im Zweifel **nicht versionieren**. 

**Ausnahmen (mit Begründung):**
- Mitgliederlisten intern (notwendig für Governance)
- Crewlisten für Events (für operative Abläufe)
- Adressen in Verträgen (notwendig, aber CONFIDENTIAL)

**Best Practice:**
- Minimale Erfassung (Datensparsamkeit)
- Löschkonzept definieren
- Zugriff einschränken
- Keine Weitergabe an externe Tools/Services ohne Verschlüsselung

---

## Entscheidungshilfe: Baum

```
Soll das öffentlich sein?
│
├─ NEIN
│  │
│  ├─ Enthält CONFIDENTIAL-Inhalte?
│  │  ├─ JA → CONFIDENTIAL (nicht versionieren oder speziell schützen)
│  │  └─ NEIN → INTERNAL (im Fachordner, nicht im Mirror)
│  │
│  └─ (z.B. Event-Unterlagen, interne Protokolle, Ist-Budgets)
│
└─ JA
   │
   ├─ Enthält PII/personenbezogene Daten?
   │  ├─ JA → Entfernen/anonymisieren → PUBLIC (dann im Mirror)
   │  └─ NEIN → PUBLIC (im Mirror)
   │
   └─ (z.B. Satzung, Templates, Rollen-Guides ohne Namen)
```

---

## Checkliste für neue Inhalte

Vor dem Commit:

- [ ] Ist der Inhalt im richtigen Ordner?
- [ ] Falls PUBLIC-kandidat: Ist alles bereinigt (keine PII, keine Interna)?
- [ ] Falls ja: Liegt eine kopie/Version im `90_public_mirror/`?
- [ ] Keine Passwörter, IBANs, Hostnamen, API-Keys?
- [ ] Freigabe-Status geklärt (wer darf das sehen)?

---

## FAQ

**F: Darf ich eine Teilnehmerliste mit Namen versionieren?**  
A: Wenn es für operative Dinge (Event-Crew) notwendig ist → INTERNAL/CONFIDENTIAL, im passenden Fachordner. Nicht öffentlich.

**F: Und die Satzung?**  
A: Ja, die ist PUBLIC und gehört in den Mirror – idealerweise bereinigt (keine internen Anmerkungen).

**F: Beleg einer Ausgabe – ist das CONFIDENTIAL?**  
A: Ja, wenn der Beleg Klarnamen oder spezifische Konditionen enthält. Für die Buchhaltung notwendig, aber **nicht** im Git versionieren.

**F: Kann ich PII mit Git-Secret oder .gitignore schützen?**  
A: `.gitignore` ist kein Schutz (Fehler möglich). Git-Secret ist besser, aber als Default: **nicht versionieren**.

---

**Fragen?** → Abstimmung im Team oder mit der Governance-Gruppe.
