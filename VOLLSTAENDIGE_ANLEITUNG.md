# 🎨 PsyAi TTS - Vollständige Anleitung

## 📋 Inhaltsverzeichnis

1. [Übersicht](#übersicht)
2. [Installation](#installation)
3. [Server starten](#server-starten)
4. [Login-System nutzen](#login-system-nutzen)
5. [Hauptanwendung verwenden](#hauptanwendung-verwenden)
6. [Passwort ändern](#passwort-ändern)
7. [Fehlerbehebung](#fehlerbehebung)
8. [UI-Beschreibungen](#ui-beschreibungen)
9. [Technische Details](#technische-details)

---

## 🌟 Übersicht

**PsyAi TTS** ist eine Text-to-Speech-Anwendung basierend auf Coqui TTS mit einem modernen Login-System und schwarzem metallic-purple Design.

### Hauptfunktionen:
- ✅ Login-System mit Triple-Click-Mechanismus
- ✅ Text-zu-Sprache-Synthese in über 1100 Sprachen
- ✅ Multi-Speaker-Unterstützung
- ✅ Multi-Language-Unterstützung
- ✅ Voice Cloning
- ✅ Passwort-Management
- ✅ Modernes schwarzes metallic-purple UI

---

## 💿 Installation

### Voraussetzungen

**Python-Version:**
- Python 3.9, 3.10 oder 3.11
- ⚠️ Python 3.12 könnte Kompatibilitätsprobleme haben

**Betriebssystem:**
- Linux (getestet auf Ubuntu 18.04+)
- macOS
- Windows (mit zusätzlichen Anpassungen)

### Installationsschritte

```bash
# 1. Repository klonen (falls noch nicht geschehen)
git clone https://github.com/psywlkr/PsyAi.git
cd PsyAi

# 2. Python-Version prüfen
python3 --version
# Sollte zeigen: 3.9.x, 3.10.x oder 3.11.x

# 3. Abhängigkeiten installieren
pip install -e .

# Alternativ mit allen Extras:
pip install -e .[all,dev,notebooks]
```

### Abhängigkeiten verifizieren

```bash
# Prüfen, ob TTS installiert wurde
pip list | grep TTS

# Sollte ausgeben: TTS [VERSION]
```

---

## 🚀 Server starten

### Methode 1: Standard (empfohlen für den Start)

```bash
cd /pfad/zu/PsyAi
python TTS/server/server.py
```

**Ausgabe im Terminal:**
```
* Running on http://[::]:5002
* Running on http://127.0.0.1:5002
```

### Methode 2: Mit spezifischem Modell

```bash
# Deutsches Modell
python TTS/server/server.py --model_name tts_models/de/thorsten/tacotron2-DDC

# Multi-Language XTTS
python TTS/server/server.py --model_name tts_models/multilingual/multi-dataset/xtts_v2
```

### Methode 3: Mit eigenem Port

```bash
python TTS/server/server.py --port 8080
```

### Methode 4: Mit GPU-Unterstützung

```bash
python TTS/server/server.py --use_cuda true
```

### Methode 5: Mit Debug-Modus

```bash
python TTS/server/server.py --debug true
```

### Server-URL öffnen

Nach dem Start öffne im Browser:
```
http://localhost:5002/
```

Oder bei eigenem Port:
```
http://localhost:[DEIN_PORT]/
```

---

## 🔐 Login-System nutzen

### Schritt-für-Schritt-Anleitung

#### 1. Login-Seite öffnen

Öffne `http://localhost:5002/` im Browser.

**Du siehst:**
```
┌─────────────────────────────────────────┐
│         PsyAi TTS - Login              │
│                                         │
│         ╔═══════════════════╗          │
│         ║                   ║          │
│         ║      PsyAi        ║  ← Logo  │
│         ║                   ║          │
│         ╚═══════════════════╝          │
│                                         │
│  Klicke 3x auf das Logo für           │
│  Administrator-Zugang                   │
└─────────────────────────────────────────┘
```

#### 2. Triple-Click auf Logo

**Klicke 3 Mal schnell** (innerhalb von 1 Sekunde) auf das Logo.

**Nach 3 Klicks:**
```
┌─────────────────────────────────────────┐
│         ╔═══════════════════╗          │
│         ║      PsyAi        ║          │
│         ╚═══════════════════╝          │
│                                         │
│         ┌───────────────────┐          │
│         │ [Passwort......]  │ ← Input │
│         └───────────────────┘          │
│            [ EINLOGGEN ]    ← Button   │
└─────────────────────────────────────────┘
```

#### 3. Passwort eingeben

**Standard-Passwort:** `12345678`

Tippe das Passwort ins Eingabefeld.

#### 4. Einloggen

Klicke auf den Button **"Einloggen"**.

#### 5. Erfolgreiche Anmeldung

Du wirst automatisch zur Hauptanwendung weitergeleitet: `/app`

---

## 🎤 Hauptanwendung verwenden

### Oberfläche

Nach dem Login siehst du:

```
┌──────────────────────────────────────────────────────┐
│ GitHub                     [Passwort ändern][Logout] │
│                                                       │
│              [Coqui TTS Logo]                        │
│                                                       │
│        [Type here...........................]        │
│               [  SPEAK  ]                            │
│                                                       │
│        Choose a speaker: [Dropdown ▼]                │
│        Choose a language: [Dropdown ▼]               │
│                                                       │
│        ▶ ━━━━━━━━━━━━━━━━ 🔊  ← Audio Player        │
└──────────────────────────────────────────────────────┘
```

### Text-zu-Sprache-Synthese

#### Schritt 1: Text eingeben

Klicke in das Textfeld und tippe deinen Text:
```
Beispiel: "Hallo! Dies ist ein Test der Text-zu-Sprache-Funktion."
```

#### Schritt 2: Sprecher wählen (optional)

Falls Multi-Speaker-Modell geladen ist:
- Wähle einen Sprecher aus dem Dropdown

#### Schritt 3: Sprache wählen (optional)

Falls Multi-Language-Modell geladen ist:
- Wähle eine Sprache aus dem Dropdown

#### Schritt 4: Synthese starten

**Option A:** Klicke auf den Button **"SPEAK"**

**Option B:** Drücke **Enter** im Textfeld

#### Schritt 5: Audio abspielen

- Status-Nachricht: "Synthesizing..."
- Nach der Synthese erscheint der Audio-Player
- Klicke auf ▶ um die Sprache abzuspielen

### Verfügbare Funktionen

#### 1. Multi-Speaker (falls aktiviert)
- Verschiedene Stimmen zur Auswahl
- Dropdown-Menü mit Sprecher-Namen
- Dynamische Auswahl

#### 2. Multi-Language (falls aktiviert)
- Verschiedene Sprachen verfügbar
- Dropdown-Menü mit Sprachcodes
- Beispiel: en, de, fr, es, etc.

#### 3. Style Transfer (falls GST aktiviert)
- Eingabefeld für Style-WAV
- JSON-Format oder Pfad zu WAV-Datei
- Beispiel: `{"0": 0.1}`

#### 4. Model Details (falls aktiviert)
- Button "Model Details"
- Zeigt Modell-Konfiguration
- CLI-Argumente und Parameter

---

## 🔑 Passwort ändern

### Schritt-für-Schritt

#### 1. Button klicken

Klicke oben rechts auf **"Passwort ändern"**

#### 2. Modal öffnet sich

```
┌─────────────────────────────────────┐
│      Passwort ändern                │
│                                      │
│  [Altes Passwort.............]      │
│                                      │
│  [Neues Passwort (min. 8...)]      │
│                                      │
│  [Status-Nachricht]                 │
│                                      │
│  [ÄNDERN]    [ABBRECHEN]            │
└─────────────────────────────────────┘
```

#### 3. Altes Passwort eingeben

Standard: `12345678` (oder dein aktuelles Passwort)

#### 4. Neues Passwort eingeben

- Minimum 8 Zeichen
- Keine speziellen Anforderungen

#### 5. Ändern klicken

- Bei Erfolg: Grüne Bestätigungsnachricht
- Bei Fehler: Rote Fehlermeldung

#### 6. Modal schließt automatisch

Nach 2 Sekunden bei Erfolg

### Passwort-Speicherung

Das Passwort wird gespeichert in:
```
TTS/server/admin_password.txt
```

⚠️ **Wichtig:** Diese Datei wird nicht ins Git-Repository committed (.gitignore)

---

## 🚪 Logout

### So meldest du dich ab:

1. Klicke oben rechts auf **"Logout"**
2. Du wirst zur Login-Seite zurückgeleitet
3. Session wird gelöscht

---

## 🛠️ Fehlerbehebung

### Problem 1: ModuleNotFoundError

**Symptom:**
```
ModuleNotFoundError: No module named 'TTS'
```

**Lösung:**
```bash
pip install -e .
```

### Problem 2: Port bereits belegt

**Symptom:**
```
OSError: [Errno 98] Address already in use
```

**Lösung:**
```bash
# Verwende einen anderen Port
python TTS/server/server.py --port 5003

# Oder finde und beende den Prozess
lsof -i :5002
kill -9 [PID]
```

### Problem 3: Python-Version-Inkompatibilität

**Symptom:**
```
RuntimeError: TTS requires python >= 3.9 and < 3.12
```

**Lösung:**
```bash
# Installiere Python 3.9, 3.10 oder 3.11
# Dann verwende:
python3.10 TTS/server/server.py
```

### Problem 4: CUDA-Fehler

**Symptom:**
```
RuntimeError: CUDA is not available
```

**Lösung:**
```bash
# Deaktiviere CUDA
python TTS/server/server.py --use_cuda False
```

### Problem 5: Modell-Download schlägt fehl

**Symptom:**
```
ConnectionError: Failed to download model
```

**Lösung:**
1. Prüfe Internetverbindung
2. Versuche erneut
3. Verwende VPN falls nötig

### Problem 6: Session läuft ab

**Symptom:**
- Wirst zur Login-Seite zurückgeleitet
- Trotz Login

**Lösung:**
1. Neu einloggen
2. Ursache: Browser-Cookies gelöscht oder Session-Timeout

### Problem 7: Falsches Passwort

**Symptom:**
```
Fehlermeldung: "Falsches Passwort"
```

**Lösung:**
1. Überprüfe `TTS/server/admin_password.txt`
2. Lösche Datei um zum Default zurückzukehren (12345678)
3. Starte Server neu

---

## 🎨 UI-Beschreibungen

### Farbschema

Das gesamte UI verwendet ein konsistentes schwarzes metallic-purple Theme:

#### CSS-Variablen:
```css
:root {
    --black: #0a0a0a;              /* Hintergrund */
    --metallic-purple: #8b5a9f;    /* Hauptakzent */
    --dark-purple: #4a2c54;        /* Komponenten */
    --light-purple: #b388c4;       /* Text */
}
```

#### Farb-Verwendung:
- **Hintergrund:** Tiefschwarz (#0a0a0a)
- **Container:** Gradient (schwarz → dunkel-lila → schwarz)
- **Buttons:** Metallic-purple Gradient mit Glow
- **Inputs:** Dunkles Purple mit Border
- **Text:** Helles Purple (#b388c4)
- **Hover:** Hellere Töne + Glow-Effekte

### Animationen

#### Login-Seite:
- **Logo-Klick:** Puls-Animation (0.3s)
- **Admin-Panel:** Fade-in und Expand (0.5s)
- **Input-Focus:** Glow-Effekt

#### Haupt-App:
- **Button-Hover:** Lift-up (-2px Bewegung)
- **Input-Focus:** Leuchtender Glow
- **Modal:** Fade-in mit dunklem Backdrop
- **Status-Nachrichten:** Farbwechsel (grün/rot)

### Responsive Design

#### Mobile (< 992px):
- Body padding-top: 54px
- Logo skaliert proportional
- Buttons volle Breite
- Container angepasste Padding

#### Desktop (≥ 992px):
- Body padding-top: 56px
- Optimale Darstellung
- Container begrenzte Max-Breite

---

## 🔧 Technische Details

### Architektur

#### Backend:
- **Framework:** Flask (Python)
- **Session-Management:** Flask Sessions
- **TTS-Engine:** Coqui TTS
- **Vocoders:** HiFiGAN, MelGAN, WaveRNN, etc.

#### Frontend:
- **Framework:** Bootstrap 4.1.1
- **JavaScript:** Vanilla JS (kein Framework)
- **API-Kommunikation:** Fetch API

#### Authentifizierung:
- **Typ:** Session-basiert
- **Session-Cookie:** Verschlüsselt
- **Passwort:** Plaintext in Datei (änderbar)

### API-Endpunkte

#### Öffentlich:
```
GET  /                  - Root (Redirect)
GET  /login             - Login-Seite
POST /admin/login       - Login-Authentifizierung
```

#### Geschützt (benötigt Login):
```
GET  /app               - Hauptanwendung
GET  /details           - Modell-Details
GET  /api/tts           - TTS-API
POST /admin/change-password - Passwort ändern
GET  /admin/logout      - Logout
```

### Modelle

#### Verfügbare TTS-Modelle:
- **39 TTS-Modelle** in verschiedenen Sprachen
- **8 Vocoder-Modelle**
- **1 Voice-Conversion-Modell**

#### Beispiel-Modelle:
```
tts_models/de/thorsten/tacotron2-DDC    # Deutsch
tts_models/en/ljspeech/tacotron2-DDC    # Englisch
tts_models/multilingual/multi-dataset/xtts_v2  # Multi-Language
```

#### Modell-Liste anzeigen:
```bash
python TTS/server/server.py --list_models
```

### Konfiguration

#### Environment-Variablen:
```bash
# Flask Secret Key (empfohlen zu ändern)
export FLASK_SECRET_KEY="dein-sehr-sicherer-key"
```

#### Konfigurationsdatei:
```
TTS/server/conf.json
```

Beispiel-Inhalt:
```json
{
    "model_path": "path/to/model.pth",
    "config_path": "path/to/config.json",
    "vocoder_path": "path/to/vocoder.pth",
    "vocoder_config_path": "path/to/vocoder_config.json",
    "port": 5002,
    "use_cuda": false,
    "debug": false
}
```

---

## 📊 Systemanforderungen

### Minimum:
- **CPU:** Dual-Core 2.0 GHz
- **RAM:** 8 GB
- **Speicher:** 5 GB frei
- **Python:** 3.9-3.11
- **Internet:** Für Modell-Download

### Empfohlen:
- **CPU:** Quad-Core 2.5+ GHz
- **RAM:** 16 GB
- **GPU:** CUDA-fähige GPU (optional)
- **Speicher:** 10+ GB frei
- **Python:** 3.10

### Mit GPU:
- **GPU:** NVIDIA mit CUDA-Support
- **CUDA:** 11.0+
- **cuDNN:** Kompatible Version
- **VRAM:** 4+ GB

---

## 🎯 Verwendungszwecke

### Mögliche Anwendungen:
1. **Text-zu-Sprache-Generierung** für Projekte
2. **Voice-Over** für Videos
3. **Audiobook-Erstellung**
4. **Accessibility-Features** für Apps
5. **Prototyping** von Sprachanwendungen
6. **Forschung** im Bereich TTS
7. **Multi-Language-Content** erstellen

---

## 📝 Nützliche Kommandos

### Server-Verwaltung:

```bash
# Server starten
python TTS/server/server.py

# Mit Log-Output
python TTS/server/server.py 2>&1 | tee server.log

# Im Hintergrund laufen lassen
nohup python TTS/server/server.py &

# Prozess finden
ps aux | grep server.py

# Server stoppen
# Drücke Ctrl+C im Terminal
# Oder finde PID und:
kill [PID]
```

### Modell-Management:

```bash
# Liste aller Modelle
python TTS/server/server.py --list_models

# Modell-Info abrufen
tts --model_info_by_name tts_models/de/thorsten/tacotron2-DDC

# Modell herunterladen (ohne Server)
tts --model_name tts_models/de/thorsten/tacotron2-DDC --text "Test" --out_path test.wav
```

### Debugging:

```bash
# Python-Umgebung prüfen
python -c "import TTS; print(TTS.__version__)"

# Flask-Version prüfen
python -c "import flask; print(flask.__version__)"

# Alle installierten Pakete
pip list

# Dependency-Check
pip check
```

---

## 🔒 Sicherheit

### Wichtige Sicherheitshinweise:

#### 1. Secret Key ändern (Produktion)
```bash
export FLASK_SECRET_KEY="$(openssl rand -hex 32)"
```

#### 2. Passwort ändern
Nach dem ersten Login sofort ändern!

#### 3. Passwort-Datei schützen
```bash
chmod 600 TTS/server/admin_password.txt
```

#### 4. HTTPS verwenden (Produktion)
```bash
# Mit gunicorn und SSL
gunicorn --certfile=cert.pem --keyfile=key.pem -b 0.0.0.0:443 TTS.server.server:app
```

#### 5. Firewall konfigurieren
```bash
# Nur lokaler Zugriff (Standard)
# Für externe Zugriffe Port freigeben
sudo ufw allow 5002/tcp
```

---

## 📚 Weitere Dokumentation

### Dateien im Repository:

1. **`README.md`** - Haupt-README der Coqui TTS
2. **`FUNKTIONSANALYSE.md`** - Komplette Funktionsanalyse
3. **`UI_DESIGN.md`** - UI-Design-Dokumentation
4. **`LOGIN_SYSTEM.md`** - Login-System-Dokumentation
5. **`BUGFIX_LOGIN.md`** - Bug-Fix-Dokumentation
6. **`UI_SCREENSHOTS.md`** - Visuelle UI-Beschreibungen
7. **`SERVER_START.md`** - Server-Start-Anleitung

### Online-Ressourcen:

- **Coqui TTS Docs:** https://tts.readthedocs.io/
- **GitHub Issues:** https://github.com/coqui-ai/TTS/issues
- **Modell-Zoo:** https://github.com/coqui-ai/TTS/releases

---

## 🤝 Support

### Bei Problemen:

1. **Logs prüfen:** Terminal-Ausgabe anschauen
2. **Dokumentation lesen:** Alle .md Dateien im Repository
3. **GitHub Issues:** Suche nach ähnlichen Problemen
4. **Debug-Modus:** Server mit `--debug true` starten

### Häufige Fragen:

**Q: Warum ist das erste Starten langsam?**
A: Beim ersten Start wird das Modell heruntergeladen. Das kann einige Minuten dauern.

**Q: Kann ich eigene Modelle verwenden?**
A: Ja! Verwende `--model_path` und `--config_path` Parameter.

**Q: Funktioniert es offline?**
A: Nach dem ersten Download ja, aber der erste Start benötigt Internet.

**Q: Wie viel VRAM brauche ich?**
A: Für kleine Modelle 2-4GB, für große Modelle (XTTS) 6-8GB.

**Q: Kann ich mehrere Instanzen starten?**
A: Ja, mit unterschiedlichen Ports: `--port 5003`, `--port 5004`, etc.

---

## 🎉 Zusammenfassung

### Schnellstart in 5 Schritten:

1. **Installieren:**
   ```bash
   pip install -e .
   ```

2. **Server starten:**
   ```bash
   python TTS/server/server.py
   ```

3. **Browser öffnen:**
   ```
   http://localhost:5002/
   ```

4. **Einloggen:**
   - 3x auf Logo klicken
   - Passwort: `12345678`

5. **Verwenden:**
   - Text eingeben
   - "Speak" klicken
   - Audio anhören

### Das war's! 🚀

Viel Spaß mit PsyAi TTS!

---

**Version:** 1.0
**Datum:** 21. März 2026
**Autor:** PsyAi Development Team

---

## 📎 Anhang

### Keyboard-Shortcuts:

| Shortcut | Aktion |
|----------|--------|
| Enter | Synthese starten (im Textfeld) |
| Escape | Modal schließen |
| Tab | Zwischen Feldern navigieren |

### Browser-Kompatibilität:

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | 90+ | ✅ Vollständig unterstützt |
| Firefox | 88+ | ✅ Vollständig unterstützt |
| Safari | 14+ | ✅ Vollständig unterstützt |
| Edge | 90+ | ✅ Vollständig unterstützt |
| Opera | 76+ | ✅ Vollständig unterstützt |

### Status-Codes:

| Code | Bedeutung |
|------|-----------|
| 200 | OK - Erfolgreich |
| 401 | Unauthorized - Nicht authentifiziert |
| 404 | Not Found - Seite nicht gefunden |
| 500 | Internal Server Error - Server-Fehler |

---

**Ende der Anleitung**

Bei Fragen oder Problemen schaue in die anderen Dokumentationsdateien oder erstelle ein GitHub Issue.
