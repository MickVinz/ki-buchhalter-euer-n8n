# KI-Buchhalter / Rechnungsautomatisierung EÜR (n8n Workflow)

n8n-Workflow, der Belege aus E-Mail, Telegram (Foto + Sprachnachricht) und Google Drive automatisch erfasst, per Mistral OCR ausliest, mit GPT-4o-mini in EÜR-Kategorien strukturiert und revisionssicher in Google Drive/Sheets ablegt. Zusätzlich ein KI-Finanz-Agent mit Calculator-Tool für Rückfragen zu den eigenen Finanzen per Telegram.

## Inhalt

- `Rechnungsautomatisierung EÜR.json` – n8n-Workflow-Export, importierbar in n8n
- `KI-Automatisierung_der_Buchhaltungsprozesse.png` – Übersicht des Workflows
- `Screenshot 2026-07-17 115158.png` – Screenshot
- `EÜR 2025.xlsx` – Beispiel-EÜR-Tabelle
- `einleitung.txt` – Begleitartikel

## Übersicht

![Workflow-Übersicht](KI-Automatisierung_der_Buchhaltungsprozesse.png)

## Screenshots

![Screenshot 1](Screenshot%202026-07-17%20115158.png)

## Funktionen

- 📥 **Multi-Quellen-Erfassung** – Belege per E-Mail-Anhang, Telegram-Foto oder Drive-Upload
- 🎙 **Voice-to-Text** – Sprachnachrichten an den Telegram-Bot statt Tippen
- 🔍 **Mistral OCR v3** – Texterkennung auch bei schlechten Fotos, Tabellen, Handschrift
- 🧠 **Information Extractor (GPT-4o-mini)** – erkennt Lieferant, Brutto/Netto, USt-Satz, EÜR-Kategorie
- ✅ **Human-in-the-Loop** – Bot fragt per Knopfdruck Einnahme/Ausgabe ab, Bestätigung vor Verarbeitung
- 🔒 **Chat-ID-Schutz** – nur der eigene Telegram-Account hat Zugriff auf den Bot
- 🗂 **Revisionssichere Ablage** – automatische Jahres-/Monatsordner in Drive, Umbenennung nach `[Datum][Kategorie]`
- 📊 **Zentrales Register** – jeder Sheets-Eintrag verlinkt direkt zum Beleg in Drive
- 💬 **KI-Finanz-Agent** – Fragen zu Finanzen per Telegram (Text/Sprache), Calculator-Tool gegen Halluzinationen

## Setup

1. `Rechnungsautomatisierung EÜR.json` in n8n importieren
2. Credentials verknüpfen: Telegram Bot, Mistral API, OpenAI (GPT-4o-mini), Google Drive, Google Sheets
3. Eigene Telegram Chat-ID im Filtermodul eintragen (Zugriffsschutz)
4. `EÜR 2025.xlsx` als Vorlage für die Google-Sheets-Tabelle verwenden
5. Workflow aktivieren

## Verwendete Nodes

- Telegram Trigger/Node (inkl. Voice-Transkription)
- Gmail/E-Mail-Trigger, Google Drive Trigger
- Mistral OCR
- Information Extractor / LangChain Agent (GPT-4o-mini)
- Calculator Tool
- Google Drive, Google Sheets Nodes
