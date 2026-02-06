# Sequenz e.V. Styleguide

## Visuelle Identität

### Farbpalette (Brand Colors)

| Name | Hex | Anwendung |
|------|-----|-----------|
| **Brand Red** | `#D60000` | Primär- farbe: Buttons, Headlines, Links, Highlights |
| **Surface** | `#121212` | Hintergrund: Seiten, Cards, Container |
| **Void** | `#050505` | Tiefe Hintergründe: Hero-Bereiche, Global-Overlay |
| **Surface Hover** | `#1E1E1E` | Hover-Zustand: Noch dunklerer Hintergrund |
| **Border Strong** | `#444` | Trennlinien, Input-Outer-Border |
| **Border** | `#2A2A2A` | Standard-Border: Cards, Panels |
| **Text Primary** | `#EDEDED` | Haupttext: Headlines, wichtige Inhalte |
| **Text Secondary** | `#999` | Sekundärtext: Paragraphs, meta-Infos |
| **Text Disabled** | `#555` | Deaktivierte Elemente, placeholder, Hinweis-Text |

> **Tipp:** Nutze `#D60000` psychoaktiv — es sollte *nicht* überall sein. Nur dort, wo Energie, Einladung oder Dringlichkeit gebraucht wird. Alles andere bleibt dunkel und ruhig.

---

### Typografie

#### Fonts

- **Hauptfont (Text):** `Work Sans` — --
  - Regular, Medium, SemiBold, Bold
  - Verwendet für alle Headlines und Fließtexte
- **Code / Monospace:** `JetBrains Mono`
  - Verwendet für technische Infos, Code-Beispiele, Git-Hints

#### Textgrößen (Typography Scale)

| Level | CSS | Verwendung |
|-------|-----|------------|
| `h1` | `clamp(3rem, 5vw, 4.5rem)` | Hero-Headline („Die Nacht gehört denen…”) |
| `h2` | `clamp(1.5rem, 4vw, 2.25rem)` | Section-Titel („Wofür wir stehen", „Residents") |
| `h3` | `clamp(1.125rem, 3vw, 1.5rem)` | Subsection-Titel, Card-Headline („Erlebnis", „Event-Kontingent") |
| `body` | `1rem` | Fließtext (ab 640px: 16px) |
| `text-sm` | `0.875rem` | Footer, Meta-Infos,的小标签 |
| `text-xs` | `0.75rem` | Small print, Datenschutz, Rechtliches |
| `label-meta` | `0.875rem`, uppercase, bold | Visual Tags: „Resident“, „Mitglied werden" |
| `uppercase-small-caps` | `text-transform: uppercase; font-variant: small-caps; letter-spacing: 0.12em; font-weight: 600` | Navigation, CTA-Sektionen, klar und prominent |

> **Hinweis:** Alle Headlines verwenden `letter-spacing: -0.02em` bis `-0.05em`. Vermeide Standard-Text-Shapes. Lass die Schrift *atmen*.

---

### Layout & Abstände

| Abstand | Bezeichnung | px | Verwendung |
|---------|-------------|----|------------|
| `xs` | 8px | 0.5rem | Buttons, Kleinigkeiten |
| `sm` | 12px | 0.75rem | Einzelne Elemente, Paddings |
| `md` | 16px | 1rem | Standard Padding, Margin |
| `lg` | 24px | 1.5rem | Content-Blocks, Cards |
| `xl` | 32px | 2rem | Sections, Hero-Bereiche |
| `xxl` | 64px | 4rem | Sekundäre Abstände (Header/Footer) |

> **Regel:** Alle horizontalen Abstände sind *gerade Zahlen* — 16px, 24px, 40px, 80px. Kein Einsamkeit — alles hat ein Gegenstück.

---

### Interaktionen & Zustände

#### Hover-Effekte

- **Buttons (Primary):** `translate-y: -0.25rem` + Drop Shadow
  - `box-shadow: 0 0 15px rgba(214,0,0,0.15)`
- **Cards:** `border-color: #D60000` (nicht füllung)
- **Links:** `color: #EDEDED` auf Hover — kein Underline, kein Jitter. Nur Licht.
- **Alle interaktiven Elemente:** 200ms `ease-out` Transition

#### Focus-Variante

```css
:focus {
  outline: 2px solid transparent;
  outline-offset: 2px;
  box-shadow: 0 0 0 1px #D60000;
}
```

> *Kein gelbes Highlight. Kein Border-Style. Nur eine feine rote Aura. Ein Leuchten.*

---

### Grafische Elemente

#### Farbverläufe

Du findest keine üppigen Farbverläufe auf der Website — **aber du findest sie im Hintergrund.**

```css
background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='60' height='60'%3E%3Crect width='60' height='60' fill='none' stroke='%23D60000' stroke-width='1'/%3E%3C/svg%3E");
opacity: 0.06;
```

→ Dieser **subtile Raster-Muster** aus exakt `#D60000`-Liniengitter (1px) auf `#050505`-Hintergrund ist **eine visuelle Signature** von Sequenz.

#### Waves / Topography

Matthias benutzt Wellenformen (SVG) in Hero-Sections — aber nicht als sheer Dekoration. Sie symbolisieren:

> „Energie, die durch den Raum zerreißt.“

→ Die Wellen sind **nicht frei beweglich**. Sie haben eine stille, mechanische Frequenz.

#### Equalizer / Audio-Visualisation

Auf der Residents-Seite: Die kleinen Linienelemente, die „pulsieren“, sind **nicht animiert** — sondern mit CSS-Animationen, die mit dem Rhythmus der Musik synchron laufen würden — wenn sie ein Echo wären.

> *Sie sind kein Geräusch. Sie sind sein Nachhall.*

---

### Anpassung für den Verein

#### Im Repo: Spricht das Styleguide zu den folgenden Bereichen:

| Bereich | Styleguide-Regel |
|--------|------------------|
| `90_public_mirror/` | **Grundsätzlich** — Comic-Sans, Poppins, überfeinerte Farben: NEVER. Nur `#D60000` und Schwarz. |
| `05_brand/` | **Nur diese Datei.** Keine PSDs. Keine PNGs. Nur Markdown. |
| `05_brand/assets/` | **Nur `.svg`-Dateien.** Keine `.jpg`, `.png` — auch nicht für Logos. SVG skalieren, bleiben immer stark. |
| `00_meta/ai_quickstart.md` | **KI darf nicht** einen neuen Farbton vorschlagen. Weder `#D60000`, noch `#E20000`. Der Rot ist heilig. |
| `10_templates/` | Vorlagen für Dokumente: Nur `Work Sans` (Regular), `#EDEDED` im Text, Hintergrund `#121212`. |
| Doku, PDFs, Notizen | **Schwarze Schrift auf weißem Grund: STRICTLY forbidden.** 
Sofern nötig: `#EDEDED` auf `#121212` — wie die Website. |

---

## Warum dies funktioniert

Auf der Website landest du nicht — du **gehst hinein**. Die Schrift spricht nicht. Die Farbe schreit nicht.