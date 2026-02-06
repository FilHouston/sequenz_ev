# Git-Workflow – Sequenz e.V. (Stabil. Nichts Gangbang.)

Mein Ziel: Keine Merge-Konflikte. Keine nervigen PRs. Kein „Wer hat was geändert?"

## Regel 1: Nur Fast-Forward

Wir machen **KEINE merge-commits**.  
Nur:  
- `git rebase`  
- `git cherry-pick`

Warum?  
→ Manage-Log wird linear.  
→ Git history wird lesbar.  
→ Du siehst, wer was gemacht hat – **ohne Bruchstellen.**

## Regel 2: Branch-Naming

Benutze:  
`<type>/<beschreibung>`

Beispiele:  
- `feat/beitragsordnung-5-eur`  
- `fix/verhaltenskodex-typo`  
- `docs/ai_quickstart`  
- `chore/cleanup-archived`

**Kein „update“, kein „fix“, kein „test“ ohne Kontext.**

## Regel 3: PR-Checkliste

Bevor du PR-erstellst:  
✅ Alle Dateien im richtigen Ordner?  
✅ PII entfernt, wenn es öffentlich ist?  
✅ `90_public_mirror/` mitge-updated, wenn nötig?  
✅ `git diff` gecheckt?  
✅ PR-Title klar? (z.B. „feat: beitragsordnung: Auf 5,50 Euro aktualisiert“)  
✅ PR-Body: „Warum? Was wurde geändert? Was muss geprüft werden?"

## Regel 4: Mergetag

Jeden **Dienstag um 14:00 Uhr** ist „Merge-Mittwoch“.  
Alle PRs, die bis Montag 23:59 eingetragen wurden, werden geprüft.  
Falls keine Kommentare da sind → automatisch gemergt.  
Wenn was unklar ist → bleibt’s offen.

---

## Zusatz: Du willst was löschen?

- Dein Branch → mit `git branch -d dein-branch`  
- Alte Dateien in `99_archive/` verschieben – nicht löschen  
- Niemals `rm` im Repo; nur `git rm`

---

„Git ist keine Kunst. Es ist ein Werkzeug.“  
— Philipp, wahrscheinlich 2025