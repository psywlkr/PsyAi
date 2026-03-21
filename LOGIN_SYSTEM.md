# PsyAi TTS - Login System Dokumentation

## Übersicht

Das PsyAi TTS System verfügt jetzt über ein Login-System mit einem Platzhalter-Logo, Triple-Click-Authentifizierung und änderbarem Administrator-Passwort.

## Features

### 1. Login-Seite

Die Login-Seite ist die erste Seite, die Benutzer sehen, wenn sie die Anwendung öffnen.

**Design:**
- Schwarzer Hintergrund mit metallic-purple Akzenten
- Platzhalter-Logo (300x300px) mit "PsyAi" Text
- Elegantes, futuristisches Design passend zum Rest der App

**Zugang:**
- URL: `http://localhost:5002/login`
- Wird automatisch angezeigt beim Öffnen von `http://localhost:5002/`

### 2. Triple-Click Authentifizierung

**So funktioniert es:**
1. Klicke **3 Mal** auf das Logo (innerhalb von 1 Sekunde)
2. Ein Administrator-Panel erscheint mit Passwort-Eingabefeld
3. Gib das Administrator-Passwort ein
4. Klicke auf "Einloggen"
5. Bei korrektem Passwort wirst du zur Haupt-App weitergeleitet

**Hinweis:**
- Unter dem Logo steht: "Klicke 3x auf das Logo für Administrator-Zugang"
- Die Klicks müssen innerhalb von 1 Sekunde erfolgen
- Bei jedem Klick gibt es eine kurze Puls-Animation

### 3. Standard-Passwort

**Default Passwort:** `12345678`

Das Passwort kann nach dem ersten Login geändert werden.

### 4. Passwort ändern

**In der Haupt-App:**
1. Oben rechts gibt es einen Button "Passwort ändern"
2. Klicke darauf, um ein Modal-Dialog zu öffnen
3. Gib das alte Passwort ein
4. Gib das neue Passwort ein (min. 8 Zeichen)
5. Klicke auf "Ändern"

**Passwort-Speicherung:**
- Das Passwort wird in der Datei `TTS/server/admin_password.txt` gespeichert
- Diese Datei ist in `.gitignore` und wird nicht ins Repository committed
- Beim ersten Start wird das Default-Passwort verwendet
- Nach der ersten Änderung wird das neue Passwort aus der Datei gelesen

### 5. Logout

**Abmelden:**
- Oben rechts in der Haupt-App gibt es einen "Logout" Button
- Klicke darauf, um dich abzumelden
- Du wirst zurück zur Login-Seite geleitet

## Technische Details

### Authentifizierungs-System

**Session-basierte Authentifizierung:**
- Verwendet Flask Sessions
- Session-Cookie wird beim erfolgreichen Login gesetzt
- Cookie-Name: `session`
- Session bleibt aktiv, bis der Browser geschlossen oder Logout geklickt wird

**Secret Key:**
- Flask Secret Key für Session-Verschlüsselung
- Kann über Umgebungsvariable `FLASK_SECRET_KEY` gesetzt werden
- Default: `psyai-tts-secret-key-change-in-production`
- **WICHTIG:** In Produktion sollte ein sicherer, zufälliger Key verwendet werden

### API-Endpunkte

**Öffentliche Endpunkte:**
```
GET  /              - Weiterleitung zu /login oder /app
GET  /login         - Login-Seite anzeigen
POST /admin/login   - Login-Request verarbeiten
```

**Geschützte Endpunkte (benötigen Authentifizierung):**
```
GET  /app                      - Haupt-TTS-Anwendung
GET  /admin/logout             - Logout
POST /admin/change-password    - Passwort ändern
GET  /details                  - Modell-Details (wenn aktiviert)
GET  /api/tts                  - TTS-API
```

### Passwort-Verwaltung

**Funktionen:**

1. **`get_admin_password()`**
   - Liest das Passwort aus `admin_password.txt`
   - Gibt Default-Passwort zurück, wenn Datei nicht existiert
   - Default: `12345678`

2. **`set_admin_password(new_password)`**
   - Speichert neues Passwort in `admin_password.txt`
   - Überschreibt vorhandenes Passwort

3. **`is_authenticated()`**
   - Prüft, ob Session `authenticated=True` enthält
   - Gibt `True` oder `False` zurück

### Sicherheits-Hinweise

**Für Produktions-Einsatz:**

1. **Ändere den Secret Key:**
   ```bash
   export FLASK_SECRET_KEY="dein-sehr-sicherer-zufälliger-key"
   ```

2. **Ändere das Default-Passwort sofort:**
   - Nach dem ersten Login
   - Verwende ein starkes Passwort (min. 8 Zeichen)

3. **HTTPS verwenden:**
   - In Produktion sollte HTTPS verwendet werden
   - Session-Cookies sollten als `secure` markiert werden

4. **Passwort-Datei schützen:**
   - Die Datei `TTS/server/admin_password.txt` sollte nur vom Server-Prozess lesbar sein
   - Unix: `chmod 600 TTS/server/admin_password.txt`

## Verwendung

### Server starten

**Normal (wie bisher):**
```bash
python TTS/server/server.py
```

**Mit eigenem Secret Key:**
```bash
export FLASK_SECRET_KEY="mein-secret-key"
python TTS/server/server.py
```

**Mit Custom Port:**
```bash
python TTS/server/server.py --port 8080
```

### Erste Schritte

1. **Server starten:**
   ```bash
   cd /home/runner/work/PsyAi/PsyAi
   python TTS/server/server.py
   ```

2. **Browser öffnen:**
   - Navigiere zu `http://localhost:5002/`
   - Du siehst die Login-Seite mit dem PsyAi Logo

3. **3x auf Logo klicken:**
   - Klicke schnell 3 Mal hintereinander auf das Logo
   - Das Admin-Panel erscheint

4. **Einloggen:**
   - Passwort eingeben: `12345678`
   - Auf "Einloggen" klicken
   - Du wirst zur Haupt-App weitergeleitet

5. **Passwort ändern (empfohlen):**
   - Klicke auf "Passwort ändern" (oben rechts)
   - Altes Passwort: `12345678`
   - Neues Passwort eingeben (min. 8 Zeichen)
   - Auf "Ändern" klicken

## Dateien

**Neue Dateien:**
- `TTS/server/templates/login.html` - Login-Seite Template
- `TTS/server/admin_password.txt` - Passwort-Speicher (wird automatisch erstellt)

**Geänderte Dateien:**
- `TTS/server/server.py` - Server mit Authentifizierung
- `TTS/server/templates/index.html` - Logout & Passwort-Ändern Buttons
- `.gitignore` - Ausschluss der Passwort-Datei

## Kompatibilität

**Rückwärtskompatibilität:**
- Alle bestehenden TTS-Funktionen funktionieren weiterhin
- API-Endpunkte sind unverändert (außer Authentifizierungs-Pflicht)
- Alle Modelle und Konfigurationen bleiben gleich

**Browser-Anforderungen:**
- Moderne Browser (Chrome, Firefox, Safari, Edge)
- JavaScript muss aktiviert sein
- Cookies müssen aktiviert sein

## Fehlerbehebung

**Problem: "Falsches Passwort" obwohl Passwort korrekt ist**
- Lösung: Überprüfe `TTS/server/admin_password.txt`
- Lösung: Lösche die Datei, um zum Default zurückzukehren

**Problem: Session läuft ab**
- Lösung: Neu einloggen
- Ursache: Browser-Cookies gelöscht oder Session-Timeout

**Problem: Kann nicht einloggen**
- Überprüfe, ob der Server läuft
- Überprüfe die Konsole auf Fehler
- Stelle sicher, dass JavaScript aktiviert ist

## Zukünftige Erweiterungen

**Mögliche Verbesserungen:**
- Mehrere Benutzer mit verschiedenen Rollen
- Passwort-Reset-Funktion
- 2-Faktor-Authentifizierung
- Rate-Limiting für Login-Versuche
- Session-Timeout-Konfiguration
- Passwort-Hashing (aktuell: Klartext)

---

**Version:** 1.0
**Datum:** 20. März 2026
**Autor:** PsyAi Development Team
