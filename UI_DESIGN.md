# PsyAi TTS - UI Design (Schwarz Metallic Purple)

## Farbschema

Das neue UI-Design verwendet ein elegantes schwarz-metallic-lila Farbschema:

### Hauptfarben

- **Schwarz (Hintergrund)**: `#0a0a0a`
- **Metallic Purple (Akzent)**: `#8b5a9f`
- **Dunkles Purple (Komponenten)**: `#4a2c54`
- **Helles Purple (Text)**: `#b388c4`

### Farbvariablen (CSS)

```css
:root {
    --black: #0a0a0a;
    --metallic-purple: #8b5a9f;
    --dark-purple: #4a2c54;
    --light-purple: #b388c4;
    --metallic-shine: linear-gradient(135deg, #8b5a9f 0%, #6b4a7f 50%, #8b5a9f 100%);
}
```

## UI-Komponenten

### 1. Hauptseite (index.html)

#### Hintergrund
- Schwarzer Hintergrund (`#0a0a0a`)
- Container mit vertikalem Farbverlauf (schwarz → dunkel-lila → schwarz)
- Sanfte Schatten mit lila Glow-Effekt

#### Logo/Bild
- Drop-shadow-Effekt mit metallic purple Glow
- Hebt das Coqui TTS Logo hervor

#### Text-Eingabefelder
- Hintergrund: Dunkles Purple (`#4a2c54`)
- Border: 2px Metallic Purple (`#8b5a9f`)
- Text: Helles Purple (`#b388c4`)
- Placeholder-Text: Transparentes helles Lila
- **Focus-Effekt**:
  - Hellerer Hintergrund (`#5a3a6f`)
  - Leuchtender Border
  - Glühender Schatten-Effekt

#### Buttons (Speak, Model Details)
- Hintergrund: Metallic-Purple-Gradient (glänzender Effekt)
- Border: 2px Metallic Purple
- Text: Weiß, fett, uppercase
- Schatten mit lila Glow
- **Hover-Effekt**:
  - Hellerer Gradient
  - Stärkerer Schatten
  - Leichte Aufwärtsbewegung (-2px)
- **Disabled-Zustand**:
  - 50% Transparenz
  - Kein Hover-Effekt

#### Dropdown-Menüs (Speaker/Language)
- Hintergrund: Dunkles Purple
- Border: 2px Metallic Purple
- Text: Helles Purple
- **Hover-Effekt**:
  - Hellerer Border
  - Glühender Schatten
- **Focus-Effekt**: Wie Text-Eingabefelder

#### Audio-Player
- Abgerundete Ecken
- Schatten mit lila Glow
- Metallic-purple angepasste Controls (Webkit)

#### Nachrichten (#message)
- Helles Purple
- Fettschrift
- Text-Shadow mit Glow-Effekt

### 2. Details-Seite (details.html)

#### Container
- Gleicher Stil wie Hauptseite
- Mehrere Container mit Abständen

#### Überschriften (b-Tags)
- Helles Purple
- Text-Shadow mit Glow
- Größere Schriftgröße (20px)

#### Details/Summary-Elemente
- Hintergrund: Dunkles Purple
- Border: 2px Metallic Purple
- Abgerundete Ecken
- Schatten mit Glow
- **Summary Hover**:
  - Hellerer Hintergrund
  - Weißer Text
  - Smooth Transition

#### Tabellen
- Hintergrund: Dunkles Purple
- Border: 2px Metallic Purple
- **Header-Zeile**:
  - Metallic-Purple-Gradient
  - Weißer Text, fett, uppercase
- **Daten-Zeilen**:
  - Helles Purple Text
  - Border zwischen Zellen
- **Hover-Effekt**:
  - Leicht hellerer Hintergrund

## Visuelle Effekte

### Übergänge (Transitions)
Alle interaktiven Elemente haben sanfte Übergänge (0.3s ease):
- Farben
- Schatten
- Transformationen
- Border-Farben

### Schatten (Box-Shadows)
Durchgehende Verwendung von lila-gefärbten Schatten:
- Standard: `0 4px 15px rgba(139, 90, 159, 0.3)`
- Hover: `0 6px 20px rgba(139, 90, 159, 0.6)`
- Focus: `0 0 15px rgba(139, 90, 159, 0.6)`
- Container: `0 0 30px rgba(139, 90, 159, 0.3)`

### Gradienten
- **Metallic Shine**: `linear-gradient(135deg, #8b5a9f 0%, #6b4a7f 50%, #8b5a9f 100%)`
- **Container Background**: `linear-gradient(180deg, #0a0a0a 0%, #1a0a1f 50%, #0a0a0a 100%)`

## Responsive Design

Das Design behält das responsive Verhalten bei:
- Mobile: padding-top: 54px
- Desktop (≥992px): padding-top: 56px
- Alle Komponenten passen sich automatisch an

## Accessibility

- Hoher Kontrast zwischen Text und Hintergrund
- Klare Focus-States für Tastatur-Navigation
- Hover-Effekte für bessere Benutzerführung
- Große, lesbare Schriftarten

## Technische Details

- **Keine JavaScript-Änderungen**: Alle Funktionalität bleibt unverändert
- **Keine HTML-Struktur-Änderungen**: Nur CSS-Styling
- **Bootstrap kompatibel**: Funktioniert mit Bootstrap 4.1.1
- **Browser-Kompatibilität**: Moderne CSS (CSS Variables, Flexbox, Gradients)

## So sieht es aus

**Bevor**: Standard Bootstrap mit weißem Hintergrund, blauen Akzenten
**Nachher**: Dunkles, elegantes Design mit metallischem Purple-Glow

Das UI hat jetzt einen modernen, futuristischen Look mit:
- ✨ Glühenden Effekten
- 🎨 Metallischen Farbverläufen
- 🌙 Dunklem, augenschonendem Design
- 💫 Sanften Animationen und Übergängen
- 🎭 Premium-Appearance durch Purple-Metallic-Akzente

---

**Letzte Aktualisierung**: 20. März 2026
**Geänderte Dateien**:
- `/TTS/server/templates/index.html`
- `/TTS/server/templates/details.html`
