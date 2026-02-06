# Public Mirror Rules – Sequenz e.V.

Dieses Dokument definiert verbindliche Regeln für den **Public Mirror** (`/90_public_mirror/`).

Ziel:
Sicherstellen, dass nur ausdrücklich freigegebene, bereinigte und nicht-sensible Inhalte in das öffentliche Repository (`sequenz_public`) gelangen.

Single Source of Truth ist immer dieses Repository (`sequenz_internal`).

---

## Grundprinzip

> Alles ist intern, solange es nicht explizit im Public Mirror liegt.

Nur Inhalte unter:
`/90_public_mirror/`
dürfen in das öffentliche Repo gespiegelt werden.

Kein anderer Ordner darf direkt oder indirekt veröffentlicht werden.

---

## Klassifikation von Inhalten

Jede Datei fällt in eine der folgenden Klassen:

### ✅ PUBLIC

Darf öffentlich erscheinen.

Beispiele:

* Satzung
* öffentlich freigegebene Ordnungen
* Rollenbeschreibungen ohne Namen
* allgemeine Prozesse & Handbuchtexte
* Brand Assets (freigegebene Versionen)
* Blanko-Templates (ohne Klarnamen, ohne Zahlen)

Nur diese Inhalte dürfen in den Public Mirror.

---

### ⚠️ INTERNAL

Nur für Vereinsinterne Nutzung.

Beispiele:

* Event-Dokumentationen
* Projektpläne
* interne Entscheidungsdokumente
* interne Prozessvarianten
* Roadmaps
* interne Templates

Diese Inhalte dürfen **nicht** in den Public Mirror.

---

### 🔒 CONFIDENTIAL

Besonders schützenswert.

Beispiele:

* Verträge mit Dienstleistern
* Sicherheitskonzepte
* Budget-Ist-Zahlen
* Angebote & Rechnungen
* Infrastrukturdetails (IPs, Hostnamen)
* Vendor Accounts

Diese Inhalte dürfen **niemals** in den Public Mirror.

---

### 🧍 PII (personenbezogene Daten)

DSGVO-relevant – höchste Schutzstufe.

Beispiele:

* Namen mit Funktion + Kontext
* E-Mail-Adressen
* Telefonnummern
* Unterschriften
* IBAN
* private Anschriften
* Geburtsdaten

PII darf **niemals** in den Public Mirror gelangen.

---

## Red Flags (niemals public)

Wenn eine Datei eines der folgenden Elemente enthält, ist sie automatisch NICHT public-fähig:

* echte Namen von Mitgliedern, Artists, Dienstleistern
* konkrete Geldbeträge (Budgets, Rechnungen, Gagen)
* Telefonnummern / E-Mail-Adressen
* IBAN / Bankdaten
* Vertragsklauseln mit Verhandlungsergebnissen
* Sicherheitsmaßnahmen für Events
* Zugangsdaten oder Systemdetails
* IP-Adressen oder Servernamen
* Konflikte, Vorfälle, Beschwerden
* Protokolle (MV, Vorstand, Ausschüsse)

Im Zweifel: **nicht spiegeln.**

---

## Public Mirror Struktur

Der Public Mirror liegt unter:

`/90_public_mirror/`

Er enthält nur folgende Hauptbereiche:

* `governance/`
* `roles/`
* `handbook/`
* `brand/`
* `finance/`
* `templates/`

Diese Struktur spiegelt logisch die Fachbereiche wider, aber enthält nur freigegebene Inhalte.

---

## Workflow: Wie kommt etwas in den Public Mirror?

### Schritt 1 – Quelle erstellen

Inhalt wird im Fachordner erstellt, z.B.:
`01_governance/01_statutes/satzung.md`

### Schritt 2 – Prüfung

Checkliste:

* Keine Namen?
* Keine Zahlen?
* Keine Verträge?
* Keine Eventdetails?
* Keine Sicherheitsinfos?
* Keine personenbezogenen Daten?

Wenn ein Punkt kritisch: STOP.

### Schritt 3 – Bereinigung

Erstelle eine bereinigte Version:

* anonymisiert
* abstrahiert
* generalisiert
* ohne sensible Metadaten

### Schritt 4 – Spiegeln

Kopiere die bereinigte Version nach:
`90_public_mirror/<bereich>/...`

Beispiel:
`90_public_mirror/governance/satzung.md`

### Schritt 5 – Review (empfohlen)

Mindestens eine zweite Person prüft:

* Inhalt
* Klassifikation
* Risiko

---

## Metadatenpflicht (für Markdown-Dateien)

Alle Dateien im Public Mirror müssen folgenden Header besitzen:

```yaml
---
title: ""
status: draft | active | deprecated
visibility: public
owner_role: ""
last_review: YYYY-MM-DD
source_path: ""
---
```

Beispiel:

```yaml
---
title: Satzung Sequenz e.V.
status: active
visibility: public
owner_role: Vorstand
last_review: 2026-02-03
source_path: 01_governance/01_statutes/satzung.md
---
```

---

## Technische Regeln

* Der Public Mirror enthält keine Binärdateien mit Metadaten (z.B. PDFs mit Autorendaten), wenn nicht geprüft.
* Bilder nur in bereinigter Export-Version (`brand/exports_public/`).
* Keine `.env`, `.xlsx`, `.docx` mit personenbezogenen Daten.
* Keine Event-Ordner.
* Keine Protokolle.
* Keine Verträge.

---

## KI-Regel

Für KI-gestützte Aufgaben gilt:

* Öffentliche Inhalte: nur aus `/90_public_mirror/` verwenden.
* Interne Aufgaben: Fachordner nutzen.
* Keine sensiblen Inhalte an externe KI-Dienste übergeben.
* PII niemals in Prompts einfügen.

Kontext: `00_meta/ai_context.md`

---

## Verantwortung

Jede Person, die Inhalte in den Public Mirror legt, trägt Verantwortung für:

* Datenschutz
* Rechtssicherheit
* Reputationsschutz des Vereins

Bei Unsicherheit entscheidet: Vorstand / Governance-Verantwortliche.

---

## Leitsatz

> Der Public Mirror ist kein Backup.
> Der Public Mirror ist kein Dump.
> Der Public Mirror ist eine kuratierte Veröffentlichung.

Im Zweifel bleibt ein Dokument intern.
