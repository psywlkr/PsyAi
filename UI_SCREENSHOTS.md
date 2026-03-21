# PsyAi TTS - UI Screenshots und Beschreibungen

## Übersicht aller Seiten

Dieses Dokument zeigt, wie alle Seiten der PsyAi TTS Anwendung aussehen.

---

## 1. Login-Seite (`/login` oder `/`)

**URL:** `http://localhost:5002/` oder `http://localhost:5002/login`

### Beschreibung:
Die Login-Seite ist die erste Seite, die du siehst.

### Visuelle Elemente:

```
┌─────────────────────────────────────────────────────────────┐
│                                                               │
│                    [PsyAi TTS - Login]                       │
│                                                               │
│                  ╔═══════════════════════╗                   │
│                  ║                       ║                   │
│                  ║                       ║                   │
│                  ║                       ║                   │
│                  ║        PsyAi          ║  ← Placeholder Logo
│                  ║                       ║     (300x300px)
│                  ║                       ║                   │
│                  ║                       ║                   │
│                  ╚═══════════════════════╝                   │
│                                                               │
│          Klicke 3x auf das Logo für Administrator-Zugang     │
│                                                               │
│              [Admin-Panel - verborgen]                       │
│                                                               │
└─────────────────────────────────────────────────────────────┘
```

**Nach 3 Klicks auf das Logo:**

```
┌─────────────────────────────────────────────────────────────┐
│                                                               │
│                    [PsyAi TTS - Login]                       │
│                                                               │
│                  ╔═══════════════════════╗                   │
│                  ║                       ║                   │
│                  ║        PsyAi          ║  ← Logo           │
│                  ║                       ║                   │
│                  ╚═══════════════════════╝                   │
│                                                               │
│          Klicke 3x auf das Logo für Administrator-Zugang     │
│                                                               │
│              ┌─────────────────────────────┐                 │
│              │ [Administrator-Passwort...] │  ← Eingabefeld │
│              └─────────────────────────────┘                 │
│                    [  EINLOGGEN  ]          ← Button         │
│                                                               │
│                    [Fehlermeldung]          ← (falls falsch) │
│                                                               │
└─────────────────────────────────────────────────────────────┘
```

### Farben:
- **Hintergrund:** Schwarz (#0a0a0a)
- **Logo-Box:** Dunkles Purple (#4a2c54) mit metallic-purple Border (#8b5a9f)
- **Logo-Text:** Metallic Purple (#8b5a9f) mit Glow-Effekt
- **Eingabefeld:** Dunkles Purple mit metallic-purple Border
- **Button:** Metallic-purple Gradient mit Glow
- **Text:** Helles Purple (#b388c4)

### Interaktionen:
1. **Logo:** Klickbar, bei 3 Klicks erscheint Admin-Panel
2. **Passwort-Eingabe:** Default: `12345678`
3. **Einloggen-Button:** Sendet Login-Request
4. **Bei Erfolg:** Weiterleitung zu `/app`

---

## 2. Haupt-TTS-Anwendung (`/app`)

**URL:** `http://localhost:5002/app`

**Zugriff:** Nur nach erfolgreichem Login

### Beschreibung:
Die Hauptanwendung für Text-to-Speech Synthese.

### Visuelle Elemente:

```
┌─────────────────────────────────────────────────────────────┐
│  GitHub                              [Passwort ändern][Logout]│← Admin-Controls
│  Fork Me                                                      │
│                                                               │
│                  ┌─────────────────────┐                     │
│                  │  Coqui TTS Logo     │  ← Logo (512px)    │
│                  │  (grün)             │                     │
│                  └─────────────────────┘                     │
│                                                               │
│            [Type here..............................]          │← Text-Eingabe
│                      [  SPEAK  ]                 ← Button    │
│                                                               │
│            ┌─ Choose a speaker: ─┐              ← (optional)│
│            │ [Speaker Dropdown  ▼]│                          │
│            └──────────────────────┘                          │
│                                                               │
│            ┌─ Choose a language: ─┐             ← (optional)│
│            │ [Language Dropdown ▼]│                          │
│            └──────────────────────┘                          │
│                                                               │
│                 [ MODEL DETAILS ]                ← (optional)│
│                                                               │
│            ┌──────────────────────────┐          ← Audio     │
│            │ ▶️ ━━━━━━━━━━━━━━━ 🔊    │            Player    │
│            └──────────────────────────┘                      │
│                                                               │
│                  [Status-Nachricht]                          │
│                                                               │
└─────────────────────────────────────────────────────────────┘
```

**Mit Passwort-Ändern Modal:**

```
┌─────────────────────────────────────────────────────────────┐
│                 ╔═══════════════════════════════╗            │
│                 ║   Passwort ändern            ║            │
│                 ║                               ║            │
│                 ║ [Altes Passwort........]     ║            │
│                 ║                               ║            │
│                 ║ [Neues Passwort (min. 8...)] ║            │
│                 ║                               ║            │
│                 ║ [Status-Nachricht]            ║            │
│                 ║                               ║            │
│                 ║  [ÄNDERN]    [ABBRECHEN]     ║            │
│                 ║                               ║            │
│                 ╚═══════════════════════════════╝            │
└─────────────────────────────────────────────────────────────┘
```

### Farben:
- **Hintergrund:** Schwarz (#0a0a0a)
- **Container:** Dunkler Gradient (schwarz → dunkel-lila → schwarz)
- **Eingabefelder:** Dunkles Purple mit metallic-purple Border
- **Buttons:** Metallic-purple Gradient mit Glow
- **Dropdown:** Dunkles Purple mit metallic-purple Border
- **Audio-Player:** Angepasste Controls in Purple-Tönen

### Interaktionen:
1. **Text-Eingabe:** Tippe Text für TTS
2. **Speak-Button:** Startet Synthese
3. **Enter-Taste:** Startet auch Synthese
4. **Speaker-Dropdown:** Wählt Sprecher (falls Multi-Speaker)
5. **Language-Dropdown:** Wählt Sprache (falls Multi-Language)
6. **Model Details:** Zeigt Modell-Konfiguration
7. **Passwort ändern:** Öffnet Modal
8. **Logout:** Zurück zur Login-Seite

### Features:
- Text-zu-Sprache Synthese
- Multi-Speaker Support (wenn aktiviert)
- Multi-Language Support (wenn aktiviert)
- Style Transfer mit GST (wenn aktiviert)
- Audio-Player mit Controls
- Status-Nachrichten
- Passwort-Ändern-Funktion
- Logout-Funktion

---

## 3. Details-Seite (`/details`)

**URL:** `http://localhost:5002/details`

**Zugriff:** Nur wenn `--show_details=true` beim Server-Start

### Beschreibung:
Zeigt detaillierte Modell-Konfigurationen.

### Visuelle Elemente:

```
┌─────────────────────────────────────────────────────────────┐
│  GitHub Fork Me                                              │
│                                                               │
│                  Model details                               │
│                                                               │
│            ┌─ ▶ CLI arguments: ────────────┐                │
│            │                                 │                │
│            │  ┌──────────────┬──────────┐  │                │
│            │  │ CLI key      │ Value    │  │                │
│            │  ├──────────────┼──────────┤  │                │
│            │  │ model_name   │ ...      │  │                │
│            │  │ port         │ 5002     │  │                │
│            │  │ use_cuda     │ False    │  │                │
│            │  └──────────────┴──────────┘  │                │
│            └─────────────────────────────────┘                │
│                                                               │
│            ┌─ ▶ Model config: ───────────┐                  │
│            │                                │                 │
│            │  ┌──────────────┬──────────┐ │                 │
│            │  │ Key          │ Value    │ │                 │
│            │  ├──────────────┼──────────┤ │                 │
│            │  │ model        │ ...      │ │                 │
│            │  │ audio        │ {...}    │ │                 │
│            │  └──────────────┴──────────┘ │                 │
│            └──────────────────────────────┘                  │
│                                                               │
│            ┌─ ▶ Vocoder model config: ───┐                  │
│            │                                │                 │
│            │  ┌──────────────┬──────────┐ │                 │
│            │  │ Key          │ Value    │ │                 │
│            │  ├──────────────┼──────────┤ │                 │
│            │  │ model        │ ...      │ │                 │
│            │  └──────────────┴──────────┘ │                 │
│            └──────────────────────────────┘                  │
│                                                               │
└─────────────────────────────────────────────────────────────┘
```

### Farben:
- **Hintergrund:** Schwarz (#0a0a0a)
- **Container:** Dunkler Gradient mit Purple-Tönen
- **Details-Boxen:** Dunkles Purple mit metallic-purple Border
- **Tabellen:** Dunkles Purple mit Border
- **Header-Zeile:** Metallic-purple Gradient
- **Text:** Helles Purple (#b388c4)

### Interaktionen:
1. **Details-Abschnitte:** Ausklappbar (▶/▼)
2. **Tabellen-Zeilen:** Hover-Effekt
3. **Summary-Elemente:** Klickbar zum Aufklappen

---

## Farbpalette (für alle Seiten)

### CSS-Variablen:
```css
:root {
    --black: #0a0a0a;                    /* Hintergrund */
    --metallic-purple: #8b5a9f;          /* Hauptakzent */
    --dark-purple: #4a2c54;              /* Komponenten-Hintergrund */
    --light-purple: #b388c4;             /* Text */
    --metallic-shine: linear-gradient(   /* Gradient für Buttons */
        135deg,
        #8b5a9f 0%,
        #6b4a7f 50%,
        #8b5a9f 100%
    );
}
```

### Verwendung:
- **Hintergrund:** Tiefschwarz (#0a0a0a)
- **Container:** Gradient (schwarz → dunkel-lila → schwarz)
- **Buttons:** Metallic-purple Gradient mit Glow
- **Inputs:** Dunkles Purple mit Border
- **Text:** Helles Purple für Lesbarkeit
- **Hover:** Hellere Töne und Glow-Effekte

---

## Animationen und Effekte

### Login-Seite:
- **Logo-Klick:** Puls-Animation (0.3s)
- **Admin-Panel:** Fade-in und Expand (0.5s)
- **Eingabefeld-Focus:** Glow-Effekt

### Haupt-App:
- **Button-Hover:** Lift-up-Effekt (-2px)
- **Input-Focus:** Glow-Effekt
- **Modal:** Fade-in mit Backdrop
- **Passwort-Nachricht:** Farbwechsel (grün/rot)

### Details-Seite:
- **Summary-Hover:** Hintergrund-Highlight
- **Tabellen-Zeilen:** Hover-Highlight
- **Details-Aufklappen:** Smooth Expand

---

## Responsive Design

### Mobile (< 992px):
- **Body padding-top:** 54px
- **Logo:** Skaliert proportional
- **Buttons:** Volle Breite auf kleinen Screens
- **Container:** Angepasste Padding

### Desktop (≥ 992px):
- **Body padding-top:** 56px
- **Optimale Darstellung:** Alle Elemente zentriert
- **Max-Breite:** Container begrenzt für Lesbarkeit

---

## Navigation zwischen Seiten

### Flow-Diagramm:

```
┌─────────────┐
│  / (Root)   │
└──────┬──────┘
       │
       ▼
   Authentifiziert?
       │
   ┌───┴───┐
   │       │
   Nein    Ja
   │       │
   ▼       ▼
┌─────┐  ┌────┐
│Login│  │/app│
└──┬──┘  └─┬──┘
   │       │
   │3x     │
   │Klick  │Logout
   │+      │
   │Pass   │
   │       │
   └───┬───┘
       │
       ▼
   ┌────────┐
   │  /app  │ ◄──┐
   └───┬────┘    │
       │         │
       │Details  │
       │         │
       ▼         │
   ┌─────────┐  │
   │/details │──┘
   └─────────┘
```

### Routen:
1. **`/`** → Redirect zu `/login` oder `/app`
2. **`/login`** → Login-Seite
3. **`/app`** → Haupt-TTS-App (geschützt)
4. **`/details`** → Modell-Details (geschützt, optional)
5. **`/admin/logout`** → Logout, Redirect zu `/login`

---

## Zusammenfassung

### Login-Seite:
✅ Schwarzer Hintergrund mit Purple-Akzenten
✅ 300x300px Platzhalter-Logo mit "PsyAi"
✅ Triple-Click-Mechanismus
✅ Passwort-Eingabe (Default: 12345678)
✅ Glow-Effekte und Animationen

### Haupt-App:
✅ TTS-Funktionalität vollständig erhalten
✅ Logout-Button oben rechts
✅ Passwort-Ändern-Button oben rechts
✅ Modal für Passwort-Änderung
✅ Alle TTS-Features funktionsfähig

### Details-Seite:
✅ Modell-Konfiguration anzeigen
✅ Ausklappbare Details-Abschnitte
✅ Tabellen mit Konfigurationswerten
✅ Konsistentes Purple-Design

---

**Status:** Alle Seiten implementiert und funktionsfähig
**Design:** Einheitliches schwarz-metallic-purple Theme
**Funktionalität:** Vollständig getestet

