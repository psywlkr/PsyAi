# PsyAi TTS Server - Start-Anleitung

## So startest du den Server

### Voraussetzungen

1. **Python 3.9 bis 3.11** muss installiert sein
   - Die App wurde für Python 3.9-3.11 entwickelt
   - Python 3.12 könnte Kompatibilitätsprobleme haben

2. **Abhängigkeiten installieren:**
   ```bash
   cd /home/runner/work/PsyAi/PsyAi
   pip install -e .
   ```

### Server starten

**Option 1: Mit Standard-Modell**
```bash
cd /home/runner/work/PsyAi/PsyAi
python TTS/server/server.py
```

**Option 2: Mit spezifischem Modell**
```bash
python TTS/server/server.py --model_name tts_models/de/thorsten/tacotron2-DDC
```

**Option 3: Mit eigenem Port**
```bash
python TTS/server/server.py --port 8080
```

### Server öffnet sich auf:

```
http://localhost:5002/
```

Oder bei eigenem Port:
```
http://localhost:[DEIN_PORT]/
```

### Was du sehen wirst:

1. **Terminal-Ausgabe:**
   ```
   * Running on http://[::]:5002
   * Running on http://127.0.0.1:5002
   ```

2. **Im Browser:**
   - Login-Seite mit PsyAi Logo
   - Schwarzer Hintergrund mit metallic-purple Design

### Login-Prozess:

1. **3x auf das Logo klicken** (schnell hintereinander)
2. **Admin-Panel erscheint**
3. **Passwort eingeben:** `12345678`
4. **Einloggen klicken**
5. **Weiterleitung zur TTS-App**

### Wichtige Hinweise:

⚠️ **Beim ersten Start:**
- Das Modell wird automatisch heruntergeladen
- Dies kann einige Minuten dauern
- Internetverbindung erforderlich

⚠️ **Fehlerbehebung:**

**Problem: ModuleNotFoundError**
```bash
# Lösung: Installiere Dependencies
pip install -e .
```

**Problem: Port bereits belegt**
```bash
# Lösung: Verwende einen anderen Port
python TTS/server/server.py --port 5003
```

**Problem: CUDA-Fehler**
```bash
# Lösung: Deaktiviere CUDA
python TTS/server/server.py --use_cuda False
```

### Server stoppen:

- Drücke `Ctrl+C` im Terminal

### Alle Server-Optionen:

```bash
python TTS/server/server.py --help
```

**Verfügbare Optionen:**
- `--list_models` - Zeigt alle verfügbaren Modelle
- `--model_name` - Wählt spezifisches TTS-Modell
- `--vocoder_name` - Wählt spezifischen Vocoder
- `--port` - Ändert Port (Standard: 5002)
- `--use_cuda` - Aktiviert GPU-Unterstützung
- `--debug` - Aktiviert Debug-Modus
- `--show_details` - Zeigt Modell-Details-Seite

### Beispiel-Befehle:

**Deutsches Modell mit Details:**
```bash
python TTS/server/server.py \
  --model_name tts_models/de/thorsten/tacotron2-DDC \
  --show_details true
```

**Multi-Language-Modell:**
```bash
python TTS/server/server.py \
  --model_name tts_models/multilingual/multi-dataset/xtts_v2
```

**Mit GPU:**
```bash
python TTS/server/server.py \
  --use_cuda true
```

### Nach dem Login:

**Verfügbare Funktionen:**
- ✅ Text-zu-Sprache Synthese
- ✅ Multi-Speaker (falls Modell unterstützt)
- ✅ Multi-Language (falls Modell unterstützt)
- ✅ Passwort ändern (oben rechts)
- ✅ Logout (oben rechts)

### Test-Text für TTS:

```
Hallo! Dies ist ein Test der Text-zu-Sprache-Funktion von PsyAi.
```

### Logs anschauen:

Der Server gibt Logs im Terminal aus:
- Model loading Fortschritt
- Synthesize Requests
- Fehler und Warnungen

---

## Schnellstart (Copy & Paste)

```bash
# 1. Ins Verzeichnis wechseln
cd /home/runner/work/PsyAi/PsyAi

# 2. Dependencies installieren (nur beim ersten Mal)
pip install -e .

# 3. Server starten
python TTS/server/server.py

# 4. Browser öffnen
# http://localhost:5002/

# 5. Login
# - 3x auf Logo klicken
# - Passwort: 12345678
# - Einloggen
```

---

## Troubleshooting

### Python-Version prüfen:
```bash
python3 --version
```

Sollte zeigen: 3.9.x, 3.10.x oder 3.11.x

### Dependencies prüfen:
```bash
pip list | grep TTS
```

Sollte zeigen: TTS [VERSION]

### Port prüfen:
```bash
netstat -tulpn | grep 5002
# oder
lsof -i :5002
```

### Logs mit Debug-Modus:
```bash
python TTS/server/server.py --debug true
```

---

**Viel Erfolg beim Testen!** 🚀

Bei Problemen schaue in die Log-Ausgabe im Terminal.
