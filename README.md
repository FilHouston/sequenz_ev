# Sequenz e.V. – Internal Repository (Single Source of Truth)

Dieses Repository ist das **interne Haupt-Repo** von Sequenz e.V.  
Es enthält operative Dokumente, Event-Unterlagen, interne Prozesse, Vorlagen sowie (teilweise) sensible Inhalte.

✅ **Wichtiges Konzept:** Wir nutzen ein **Public-Mirror-Modell**  
- **Single Source of Truth:** Dieses Repo (`sequenz_internal`)
- **Öffentliches Repo:** `sequenz_public` wird **aus einem dedizierten Mirror-Baum** erzeugt

---

## Public Mirror (Export nach außen)

Alles, was öffentlich sein darf, liegt ausschließlich unter:

`/90_public_mirror/`

Dieser Ordner ist der **einzige** Inhalt, der 1:1 in das öffentliche Repo gespiegelt wird.  
Alles außerhalb davon gilt standardmäßig als **nicht öffentlich**.

**Prinzip:**  
> Wenn es public sein soll, muss es im Mirror liegen.  
> Wenn es nicht im Mirror liegt, bleibt es intern.

---

## Datenklassifizierung (Kurzregeln)

- **Public:** darf öffentlich ins `sequenz_public`
- **Internal:** nur intern, keine Veröffentlichung
- **Confidential:** besonders schützenswert (z.B. Verträge, Budgets, Sicherheitskonzepte)
- **PII:** personenbezogene Daten (DSGVO-relevant) – im Zweifel nicht versionieren

Details: siehe `00_meta/data_classification.md`

---

## Was gehört wohin?

### Typisch PUBLIC (im Mirror)
- Satzung, öffentlich freigegebene Ordnungen/Regelwerke
- Rollenbeschreibungen ohne personenbezogene Daten
- Generische Prozesse/Handbuch-Inhalte
- Brand-Exporte, Presskit, freigegebene Grafiken
- Öffentliche Templates (Blanko-Vorlagen ohne Klarnamen)

### Typisch INTERNAL / CONFIDENTIAL (NICHT im Mirror)
- Event-Ordner, Run-of-Show, Crewlisten, Security-Pläne
- Protokolle (Vorstand/MV), interne Entscheidungen, Konflikte
- Buchhaltung: Ist-Zahlen, Belege, IBAN/Kontoauszüge, Auszahlungen
- Infrastruktur-Operations: Hostnamen, IPs, Backups, Zugangspfade
- Verträge mit Klarnamen oder verhandelten Konditionen

---

## Repository-Navigation

- `00_meta/` – Regeln, Klassifizierung, Konventionen, KI-Kontext
- `01_governance/` – Satzung, Policies, rechtliche Grundlagen (intern + Quellen)
- `02_roles/` – Rollen, Onboarding, RACI
- `03_handbook/` – Prozesse, Checklisten, FAQs
- `04_events/` – Events (immer intern)
- `05_brand/` – Brand-Assets (Source + freigegebene Exporte)
- `06_finance/` – Richtlinien, Vorlagen, Buchhaltung (teils sensibel)
- `07_infrastructure/` – Overview vs. Operations (Ops bleibt intern)
- `08_projects/` – Arbeitsstände
- `09_minutes/` – Protokolle (intern)
- `10_templates/` – Templates (public_ready vs internal_only)
- `90_public_mirror/` – **Export-Baum für das öffentliche Repo**
- `99_archive/` – Abgelegt/Deprecated

Startpunkt: `INDEX.md`

---

## Contribution / Änderungen

1. Neue Inhalte immer im passenden Fachordner erstellen (Source of Truth).
2. Prüfen: Darf das öffentlich sein?
3. Wenn ja:
   - Inhalt bereinigen (keine PII, keine Interna)
   - Im `90_public_mirror/` ablegen bzw. aktualisieren
4. Optional: Review durch eine zweite Person (Empfehlung für Governance/Legal/Finance)

---

## KI-Hinweis

Für KI-gestützte Arbeit gilt:
- Für öffentliche Artefakte ausschließlich `90_public_mirror/` verwenden.
- Für interne/operative Aufgaben primär die Fachordner nutzen.
- Keine personenbezogenen Daten in Prompts kopieren, wenn das externe Tools/Services betrifft.

Kontext für KI: `00_meta/ai_context.md`
