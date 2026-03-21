# PsyAi (Coqui TTS) - Komplette Funktionsanalyse

## Übersicht

**PsyAi** ist eine umfassende Text-to-Speech (TTS) Bibliothek, basierend auf Coqui TTS (Version 0.22.0). Die Anwendung bietet fortschrittliche Deep Learning-Modelle für die Sprachsynthese mit Unterstützung für über 1100 Sprachen.

## Hauptfunktionalitäten

### 1. Text-zu-Sprache-Synthese (TTS)

#### A. Grundlegende TTS-Funktionen
- **Mehrsprachige Unterstützung**: Über 1100 Sprachen durch Fairseq-Integration
- **Multi-Speaker-Modelle**: Unterstützung verschiedener Sprecher innerhalb eines Modells
- **Einfache Textsynthese**: Konvertierung von Text zu Sprache mit verschiedenen Modellen
- **Satzweise Synthese**: Automatische Aufteilung langer Texte in Sätze für optimale Verarbeitung

#### B. Voice Cloning (Stimmen-Klonen)
- **Zero-Shot Voice Cloning**: Klonen einer Stimme aus einer einzelnen Audio-Referenz
- **XTTS-Modelle**: Hochwertige Voice-Cloning-Funktionen mit 17 Sprachen
- **YourTTS**: Mehrsprachiges Voice Cloning (Englisch, Französisch, Portugiesisch)
- **Cross-Language Voice Cloning**: Klonen einer Stimme und Sprechen in einer anderen Sprache

#### C. Erweiterte TTS-Funktionen
- **Style Transfer**: Verwendung von GST (Global Style Tokens) für emotionale Sprachsynthese
- **Speed Control**: Anpassung der Sprechgeschwindigkeit (bei bestimmten Modellen)
- **Emotion Control**: Steuerung von Emotionen in der synthetisierten Sprache

### 2. Voice Conversion (Stimmkonvertierung)

#### A. FreeVC24
- **Stimmumwandlung**: Konvertierung der Stimme aus einer Quell-Audiodatei zu einer Zielstimme
- **Mehrsprachig**: Unterstützt mehrere Sprachen über das VCTK-Dataset
- **Kombination mit TTS**: Kann mit TTS kombiniert werden für erweiterte Voice-Cloning-Funktionen

### 3. Speaker Encoder (Sprecher-Kodierung)

#### A. D-Vector Generation
- **Sprecher-Embeddings**: Generierung von Sprecher-Vektoren für Sprecher-Identifikation
- **GE2E-Modell**: Implementierung des Generalized End-to-End Loss Modells
- **Angular Loss**: Alternative Loss-Funktion für bessere Sprecher-Unterscheidung
- **Visualisierung**: Tools zur Visualisierung von Sprecher-Embeddings (UMAP)

### 4. Vocoder-Modelle

Die App unterstützt mehrere hochmoderne Vocoder:

- **HiFiGAN**: Hochqualitative, schnelle Vocoder
- **MelGAN**: Effiziente GAN-basierte Vocoder
- **Multiband MelGAN**: Verbesserte Version mit mehreren Frequenzbändern
- **WaveGrad**: Diffusionsbasierte Vocoder
- **WaveRNN**: Autoregressive Vocoder
- **UnivNet**: Universal Vocoder
- **ParallelWaveGAN**: Parallele Wellenform-Generierung

### 5. Verfügbare TTS-Modelle

#### A. End-to-End-Modelle
- **XTTS v2**: Neuestes Modell mit 17 Sprachen
- **XTTS v1.1**: Vorherige Version mit 14 Sprachen
- **VITS**: Variational Inference Text-to-Speech
- **YourTTS**: Mehrsprachiges Zero-Shot Voice Cloning
- **Tortoise TTS**: Hochqualitative, langsame Synthese
- **Bark**: Generatives Audio-Modell von Suno AI

#### B. Zwei-Stufen-Modelle (Spectrogram + Vocoder)
- **Tacotron 2**: Beliebtes Seq2Seq-Modell
- **Tacotron**: Original-Modell
- **Glow-TTS**: Flow-basiertes Modell
- **Speedy Speech**: Schnelles TTS-Modell
- **FastPitch**: Pitch-kontrolliertes TTS
- **FastSpeech / FastSpeech2**: Nicht-autoregressive Modelle
- **Align-TTS**: Alignment-fokussiertes Modell
- **Overflow**: Neueres TTS-Modell
- **Neural HMM TTS**: HMM-basiertes neuronales Modell
- **Delightful TTS**: Fortgeschrittenes TTS mit mehreren Features
- **Capacitron**: Prosody-kontrolliertes TTS

### 6. Unterstützte Sprachen und Modelle

Die App bietet vortrainierte Modelle für folgende Sprachen:

**Europäische Sprachen:**
- Deutsch (de): 4 Modelle
- Englisch (en): 16 Modelle
- Spanisch (es): 2 Modelle
- Französisch (fr): 2 Modelle
- Italienisch (it): 4 Modelle
- Niederländisch (nl): 2 Modelle
- Portugiesisch (pt): 1 Modell
- Polnisch (pl): 1 Modell
- Türkisch (tr): 2 Modelle
- Ukrainisch (uk): 2 Modelle
- Und viele weitere...

**Afrikanische Sprachen:**
- Ewe, Hausa, Lingala, Twi (Akuapem & Asante), Yoruba

**Asiatische Sprachen:**
- Chinesisch (zh-CN): 1 Modell
- Japanisch (ja): 1 Modell
- Bengali (bn): 2 Modelle
- Persisch (fa): 1 Modell

**Mehrsprachige Modelle:**
- XTTS v2: 17 Sprachen
- YourTTS: Multi-Dataset mehrsprachig
- Bark: Mehrsprachig
- Fairseq: Über 1100 Sprachen

### 7. API-Schnittstellen

#### A. Python API (`TTS.api.TTS`)

**Hauptmethoden:**
```python
# Modell-Management
- list_models()                    # Liste aller verfügbaren Modelle
- load_tts_model_by_name()        # Laden eines Modells nach Namen
- load_tts_model_by_path()        # Laden eines benutzerdefinierten Modells

# Text-zu-Sprache
- tts(text, speaker, language)     # Synthese in Speicher
- tts_to_file()                    # Synthese in Datei

# Voice Conversion
- voice_conversion()               # Stimmkonvertierung in Speicher
- voice_conversion_to_file()       # Stimmkonvertierung in Datei

# Kombinierte Funktionen
- tts_with_vc()                    # TTS + Voice Conversion
- tts_with_vc_to_file()            # TTS + VC in Datei
```

**Eigenschaften:**
- `is_multi_speaker`: Prüft, ob Modell mehrere Sprecher unterstützt
- `is_multi_lingual`: Prüft, ob Modell mehrere Sprachen unterstützt
- `speakers`: Liste verfügbarer Sprecher
- `languages`: Liste verfügbarer Sprachen

#### B. Command-Line Interface (CLI)

**tts-Befehl:**
```bash
# Modell-Information
tts --list_models                           # Alle Modelle auflisten
tts --model_info_by_name <model_name>       # Modell-Details anzeigen

# Basis-Synthese
tts --text "Text" --out_path output.wav     # Einfache Synthese

# Mit spezifischem Modell
tts --text "Text" --model_name <model> --out_path output.wav

# Multi-Speaker
tts --text "Text" --model_name <model> --speaker_idx <id> --out_path output.wav

# Voice Cloning
tts --text "Text" --model_name <model> --speaker_wav <ref.wav> --language "en" --out_path output.wav

# Pipe-Ausgabe
tts --text "Text" --pipe_out | aplay
```

#### C. Web-Server API

**Server-Start:**
```bash
tts-server --model_name <model> --port 5002
```

**HTTP-Endpunkte:**

1. **`GET /`** - Web-Interface für interaktive Nutzung

2. **`GET|POST /api/tts`** - TTS-Synthesize-Endpunkt
   - Parameter: `text`, `speaker_id`, `language_id`, `style_wav`
   - Rückgabe: Audio/WAV-Datei

3. **`GET /locales`** - MaryTTS-kompatibel: Verfügbare Sprachen

4. **`GET /voices`** - MaryTTS-kompatibel: Verfügbare Stimmen

5. **`GET|POST /process`** - MaryTTS-kompatibel: TTS-Verarbeitung

### 8. Training-Funktionalitäten

#### A. TTS-Modell-Training
- **Trainer API**: Flexibles, feature-reiches Training-Framework
- **Multi-GPU-Support**: Verteiltes Training auf mehreren GPUs
- **Tensorboard-Integration**: Detaillierte Training-Logs und Visualisierungen
- **Dataset-Loader**: Unterstützung für verschiedene TTS-Datasets
- **Checkpoint-Management**: Automatisches Speichern und Fortsetzen
- **Evaluation**: Automatische Evaluierung während des Trainings

**Training-Befehle:**
```bash
# TTS-Modell trainieren
python TTS/bin/train_tts.py --config_path <config.json>

# Vocoder trainieren
python TTS/bin/train_vocoder.py --config_path <config.json>

# Speaker Encoder trainieren
python TTS/bin/train_encoder.py --config_path <config.json>
```

#### B. Fine-Tuning
- **XTTS Fine-Tuning**: Spezielles Demo für XTTS-Fine-Tuning
- **Transfer Learning**: Nutzung vortrainierter Modelle als Basis
- **Custom Datasets**: Training mit eigenen Daten

### 9. Dataset-Verwaltung und Preprocessing

#### A. Unterstützte Dataset-Formate
- **LJSpeech**: Standard-englisches Dataset
- **VCTK**: Multi-Speaker-englisches Dataset
- **Common Voice**: Mozilla Common Voice Datasets
- **CSS10**: Cross-lingual Multi-Speaker Dataset
- **Custom Datasets**: Eigene Datasets mit Formattern

#### B. Preprocessing-Tools
```bash
# Einzigartige Zeichen finden
python TTS/bin/find_unique_chars.py

# Einzigartige Phoneme finden
python TTS/bin/find_unique_phonemes.py

# Statistiken berechnen
python TTS/bin/compute_statistics.py

# Audio-Resampling
python TTS/bin/resample.py

# Stille entfernen (VAD)
python TTS/bin/remove_silence_using_vad.py

# Attention-Masken berechnen
python TTS/bin/compute_attention_masks.py

# Spektrogramme extrahieren
python TTS/bin/extract_tts_spectrograms.py

# Speaker-Embeddings berechnen
python TTS/bin/compute_embeddings.py
```

### 10. Audio-Verarbeitung

#### A. Audio-Transformationen
- **Mel-Spektrogramm-Generierung**: Konvertierung zu Mel-Spektrogrammen
- **STFT**: Short-Time Fourier Transform
- **Griffin-Lim**: Vocoder-Alternative für schnelle Synthese
- **Audio-Normalisierung**: Verschiedene Normalisierungs-Strategien
- **Resampling**: Konvertierung zwischen verschiedenen Sample-Raten
- **Trimming**: Automatisches Entfernen von Stille

#### B. Audio-Features
- **Sample Rate Support**: 16kHz, 22.05kHz, 24kHz, 48kHz
- **Bit Depth**: 16-bit WAV-Unterstützung
- **Channels**: Mono-Audio für TTS

### 11. Attention-Mechanismen

Implementierte Attention-Mechanismen für bessere Sprachqualität:

- **Guided Attention**: Führt das Modell zu korrekten Alignments
- **Forward-Backward Decoding**: Bidirektionale Dekodierung
- **Graves Attention**: Location-aware Attention
- **Double Decoder Consistency**: Verbesserte Attention-Stabilität
- **Dynamic Convolutional Attention**: Adaptive Attention-Fenster
- **Alignment Network**: Separates Alignment-Netzwerk

### 12. Zusätzliche Features

#### A. Modell-Management
- **Automatischer Download**: Automatisches Herunterladen vortrainierter Modelle
- **Model Cache**: Lokales Caching heruntergeladener Modelle
- **Model Registry**: Zentrale Verwaltung aller verfügbaren Modelle
- **Version Control**: Tracking von Modell-Versionen

#### B. Entwickler-Tools
- **Environment Info**: System- und Umgebungsinformationen sammeln
- **Config System**: Flexibles Konfigurationssystem für alle Modelle
- **Logging**: Ausführliches Logging für Debugging
- **Testing**: Umfangreiche Test-Suite

#### C. Deployment-Optionen
- **Docker-Support**: Vorgefertigte Docker-Images (CPU und GPU)
- **REST API**: Web-Server für Produktions-Deployments
- **Batch Processing**: Verarbeitung mehrerer Texte gleichzeitig
- **Streaming**: Low-Latency-Streaming (<200ms mit XTTS)

## Technische Architektur

### Modulstruktur

```
TTS/
├── api.py                 # Haupt-Python-API
├── bin/                   # Ausführbare Skripte (CLI-Tools)
├── tts/                   # TTS-Modelle und -Logik
│   ├── models/            # Modell-Implementierungen
│   ├── layers/            # Neuronale Netzwerk-Layer
│   ├── datasets/          # Dataset-Loader
│   └── utils/             # TTS-spezifische Utilities
├── vocoder/               # Vocoder-Modelle
│   ├── models/            # Vocoder-Implementierungen
│   ├── layers/            # Vocoder-Layer
│   └── datasets/          # Vocoder-Datasets
├── encoder/               # Speaker Encoder
├── vc/                    # Voice Conversion
├── server/                # Web-Server-Implementierung
├── config/                # Konfigurationssystem
├── utils/                 # Allgemeine Utilities
└── demos/                 # Demo-Anwendungen
```

### Modell-Typen

1. **Autoregressive Modelle**: Tacotron, Tacotron2
2. **Flow-basierte Modelle**: Glow-TTS, Overflow
3. **Non-Autoregressive**: FastSpeech, FastPitch, Speedy-Speech
4. **End-to-End**: VITS, XTTS, YourTTS
5. **Generative**: Tortoise, Bark

### Hardware-Anforderungen

- **Python-Version**: 3.9 bis 3.11
- **CPU**: Alle Modelle funktionieren auf CPU (langsamer)
- **GPU**: CUDA-fähige GPU empfohlen für:
  - Training aller Modelle
  - Schnelle Inferenz
  - Real-time Anwendungen
- **RAM**: Mindestens 8GB, 16GB+ empfohlen für große Modelle

## Zusammenfassung der Funktionen

### Was die App bereits kann:

✅ **Text-zu-Sprache-Synthese** in über 1100 Sprachen
✅ **Voice Cloning** aus einer einzigen Audio-Referenz
✅ **Multi-Speaker-Synthese** mit verschiedenen Stimmen
✅ **Voice Conversion** zwischen verschiedenen Sprechern
✅ **Mehrsprachige Synthese** mit einem Modell
✅ **Training** eigener TTS-, Vocoder- und Encoder-Modelle
✅ **Fine-Tuning** vortrainierter Modelle
✅ **Web-Server** für Produktions-Deployments
✅ **REST API** für Integration in andere Anwendungen
✅ **CLI-Tools** für Kommandozeilen-Nutzung
✅ **Batch-Verarbeitung** mehrerer Texte
✅ **Low-Latency-Streaming** (<200ms)
✅ **Dataset-Preprocessing** und Analyse-Tools
✅ **Speaker-Embedding-Generierung** und Visualisierung
✅ **Style Transfer** für emotionale Sprache
✅ **Audio-Preprocessing** (Resampling, Trimming, VAD)
✅ **Docker-Deployment** (CPU und GPU)
✅ **Tensorboard-Integration** für Training-Monitoring
✅ **Umfangreiche Test-Suite** für Qualitätssicherung

### Besondere Highlights:

- **XTTS v2**: State-of-the-art Voice Cloning mit 17 Sprachen
- **Fairseq-Integration**: Zugriff auf ~1100 TTS-Modelle
- **Bark**: Generatives Audio mit natürlichen Spracheffekten
- **Produktionsreif**: MaryTTS-kompatible API für einfache Migration
- **Open Source**: MPL 2.0 Lizenz für die meisten Komponenten

## Lizenzierung

- **Haupt-Framework**: MPL 2.0 (Mozilla Public License 2.0)
- **XTTS-Modelle**: CPML (Coqui Public Model License), TOS erforderlich
- **Andere Modelle**: Verschiedene (meist CC BY-NC-ND 4.0)
- **Bark, Tortoise**: Entsprechende Original-Lizenzen

## Version

Aktuelle Version: **0.22.0**

---

**Stand der Analyse**: 20. März 2026
**Analysierte Repository**: psywlkr/PsyAi (Fork von coqui-ai/TTS)
