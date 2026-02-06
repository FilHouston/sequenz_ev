# DEVRULES.md — Arbeitshinweise für Sequenz e.V. Infrastructure

## 🚫 HART VERBOTEN — NICHT ÜBERSCHREITEN

### 🔴 `git merge` — DAS IST EIN VERBRECHEN

> **Du darfst NIEMALS `git merge` ausführen — kein einziges Mal.**

Warum?
- Merge-Kommits verbergen die Historie.
- Sie machen Accountability kaputt.
- Sie bringen Chaos in eine Struktur, die aus Beton ist.

### ✅ WAS DU STATTDESSEN TUN MUST:

- `git fetch` → dann `git rebase origin/main` (wenn du lokal was gemacht hast)
- Oder: `git cherry-pick <commit-hash>` — nur wenn du eine einzelne Änderung brauchst
- Wenn du von jemandem Material brauchst: `git show <commit> > patch.diff` → selbst einpflegen
- Kein `pull` ohne `--rebase`

### 💬 Dieser Regel solltest du nicht nur folgen — du solltest sie *spüren*.

Wenn du den Befehl `git merge` in deinem Kopf denkst — hör auf. Atme. 

Und frag dich:

> *„Will ich die Nacht stehlen — oder sie erschaffen?“*

— *Sequenz e.V. Infrastructure, 2026*