# KI-Nutzung – Schnellreferenz für Teammitglieder

Benutzt ihr KI (ChatGPT, Claude, Ollama, etc.) für Sequenz e.V.?

Folgt diesem 3-Schritt-Plan:

## 1. WO arbeitest du?

| Bereich | Erlaubt? | Was du tun musst |
|--------|----------|------------------|
| `90_public_mirror/` | ✅ Ja | Ohne Bedenken nutzen |
| `01_governance/`, `02_roles/` | ✅ Ja, mit Vorsicht | **KEINE** Namen, E-Mails, IBANs |
| `06_finance/`, `07_infrastructure/` | ⚠️ Nur lokal | Niemals an Cloud-KI senden. Nur mit Ollama lokal |
| `04_events/` | ⚠️ Mit Anonymisierung | Aus „Maria Schmidt – Vorstand“ → „Person A – Vorstand“ |

## 2. Wie anonymisierst du?

❌ **FALSCH:**
> „Maria Schmidt ist die neue Schichtmanagerin"

✅ **RICHTIG:**
> „[Name] ist die neue Schichtmanagerin"

Benutze `[]` für alles, was identifizierbar ist.

## 3. Wo speicherst du KI-Ausgaben?

- **Nur in `90_public_mirror/` → öffentlich**
- **Nur in den Fachordnern → intern**
- **Niemals in `99_archive/` oder `00_meta/`**

## Warnung

KI **kann dich verpflichten** – sie erzeugt vermeintlich rechtssichere Texte.  
Daher: **Jeder KI-Output muss von einer echten Person geprüft werden** – besonders bei Satzung, Vertrag, Mitgliederversammlung.

**KI ist ein Kopierer. Du bist der Entscheider.**