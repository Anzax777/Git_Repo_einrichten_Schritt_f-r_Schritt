# Git_Repo_einrichten_Schritt_fuer_Schritt

# Git · Mein IPT1-Repository einrichten und synchronisieren

**Ziel:** Am Ende hast du auf GitHub **und** auf deinem Laptop dasselbe Repository mit diesen Ordnern:

```text
IPT1/
├── README.md
├── LS01/
├── LS02/
├── LS03/
├── LS04/
├── LS05/
├── LS06/
├── LS07/
└── Lernjournal/
```

> 🐧 **Linux** = so zeigt es die Lehrperson am Beamer.
> 🪟 **Windows** = so machst **du** es auf deinem Laptop.
> Die Git-Befehle sind auf beiden Systemen **gleich**. Nur das Anlegen der Ordner ist anders.

---

## 📖 Wörter

| Wort | Bedeutung |
|------|-----------|
| **Repository (Repo)** | Projektordner, den Git überwacht |
| **Remote** | die Kopie auf GitHub (im Internet) |
| **lokal** | die Kopie auf deinem Laptop |
| **clone** | Repo von GitHub auf den Laptop **holen** (nur 1-mal) |
| **add** | Änderungen **vormerken** |
| **commit** | vorgemerkte Änderungen **speichern** (mit Nachricht) |
| **push** | gespeicherte Änderungen **hochladen** zu GitHub |
| **pull** | Änderungen von GitHub **herunterladen** |
| **synchronisieren** | lokal und GitHub sind gleich (pull + push) |

```text
   Laptop (lokal)                         GitHub (remote)
  ┌──────────────┐      git push  ──►    ┌──────────────┐
  │   IPT1/      │                       │   IPT1       │
  │              │  ◄──  git pull        │              │
  └──────────────┘                       └──────────────┘
```

---

## Schritt 0 · Prüfen, ob alles bereit ist · 3 Min.

Öffne **VS Code** → Menü **Terminal → New Terminal** (oder **Ctrl + J**).

🐧 Linux und 🪟 Windows – gleich:
```bash
git --version
```

✅ Es erscheint z. B. `git version 2.43.0`.
❌ «git wird nicht erkannt» → Hand hoch, Git ist nicht installiert.

- [ ] Fertig

---

## Schritt 1 · Git sagen, wer du bist · 2 Min. · nur 1-mal pro Laptop

🐧 Linux und 🪟 Windows – gleich (eigene Daten einsetzen, **mit** Anführungszeichen):
```bash
git config --global user.name "Vorname Nachname"
git config --global user.email "deine.mail@beispiel.ch"
```

> 💡 Nimm die **gleiche E-Mail wie bei deinem GitHub-Konto**.

Kontrolle:
```bash
git config --global --list
```
✅ Du siehst `user.name=…` und `user.email=…`.

- [ ] Fertig

---

## Schritt 2 · Repository auf GitHub erstellen · 5 Min.

Im **Browser** (gleich auf Linux und Windows):

1. Gehe auf **github.com** und melde dich an.
2. Oben rechts auf **+** → **New repository**.
3. Fülle aus:

| Feld | Eingabe |
|------|---------|
| **Repository name** | `IPT1` |
| **Description** | `IPT 1 · BMSD26b` |
| **Visibility** | **Private** |
| **Add a README file** | ✅ **Häkchen setzen!** |

4. Klicke **Create repository**.

✅ Du siehst dein Repo mit einer Datei `README.md`.

### Lehrperson Zugriff geben

5. Im Repo: **Settings** → links **Collaborators** → **Add people**.
6. Gib den GitHub-Namen der Lehrperson ein: **`__________________`** → **Add**.

- [ ] Fertig

---

## Schritt 3 · Repository auf den Laptop holen (clone) · 5 Min. · nur 1-mal

1. Auf GitHub im Repo: grüner Knopf **Code** → Reiter **HTTPS** → 📋 **kopieren**.
   Die Adresse sieht so aus: `https://github.com/DEIN-NAME/IPT1.git`
2. Im VS-Code-Terminal in deinen Benutzerordner wechseln und klonen:

🐧 Linux:
```bash
cd ~
git clone https://github.com/DEIN-NAME/IPT1.git
```

🪟 Windows:
```powershell
cd ~
git clone https://github.com/DEIN-NAME/IPT1.git
```

> 💡 Adresse einfügen im Terminal: **Ctrl + V** (oder Rechtsklick).
> 🪟 Beim ersten Mal öffnet sich ein Fenster **«Sign in with your browser»** → klicken → im Browser **Authorize** → zurück zu VS Code.

✅ Es erscheint `Cloning into 'IPT1'...` und `done`.

3. Den Ordner in VS Code öffnen:

🐧 Linux und 🪟 Windows – gleich:
```bash
code -r IPT1
```
*(Oder: Menü **File → Open Folder** → Ordner `IPT1` wählen.)*

✅ Links im Explorer steht **IPT1** mit der Datei `README.md`.
✅ Das Terminal zeigt jetzt den Ordner `IPT1` an:
- 🐧 `…/IPT1$`
- 🪟 `PS C:\Users\DeinName\IPT1>`

- [ ] Fertig

---

## Schritt 4 · Ordner LS01–LS07 und Lernjournal erstellen · 5 Min.

> ⚠️ **Wichtig:** Git speichert **keine leeren Ordner**. Ein leerer Ordner kommt **nie** auf GitHub.
> Darum legen wir in **jeden** Ordner eine kleine Datei `README.md`.

Prüfe zuerst: Das Terminal muss im Ordner **IPT1** sein (siehe Schritt 3).

🐧 Linux:
```bash
mkdir LS01 LS02 LS03 LS04 LS05 LS06 LS07 Lernjournal
touch LS01/README.md LS02/README.md LS03/README.md LS04/README.md
touch LS05/README.md LS06/README.md LS07/README.md Lernjournal/README.md
```

🪟 Windows (PowerShell) – jede Zeile macht **einen Ordner mit Datei**:
```powershell
New-Item -Path "LS01\README.md" -ItemType File -Force
New-Item -Path "LS02\README.md" -ItemType File -Force
New-Item -Path "LS03\README.md" -ItemType File -Force
New-Item -Path "LS04\README.md" -ItemType File -Force
New-Item -Path "LS05\README.md" -ItemType File -Force
New-Item -Path "LS06\README.md" -ItemType File -Force
New-Item -Path "LS07\README.md" -ItemType File -Force
New-Item -Path "Lernjournal\README.md" -ItemType File -Force
```

> 💡 **Ohne Terminal geht es auch:** Im VS-Code-Explorer mit der Maus über **IPT1** → Symbol **📁+ New Folder** → `LS01` → dann Rechtsklick auf `LS01` → **New File** → `README.md`. Für jeden Ordner wiederholen.

✅ Links im Explorer siehst du 8 Ordner. In jedem liegt `README.md`.

- [ ] Fertig

---

## Schritt 5 · Hochladen zu GitHub (add → commit → push) · 5 Min.

🐧 Linux und 🪟 Windows – **gleich**. Jeden Befehl einzeln eintippen und **Enter**:

```bash
git status
```
➡️ Zeigt in **rot**, was neu ist (deine 8 Ordner).

```bash
git add .
```
➡️ Merkt **alle** Änderungen vor. Der **Punkt** heisst «alles in diesem Ordner».

```bash
git status
```
➡️ Jetzt ist alles **grün** = vorgemerkt.

```bash
git commit -m "Ordner LS01 bis LS07 und Lernjournal angelegt"
```
➡️ Speichert die Änderungen mit einer **Nachricht**.

```bash
git push
```
➡️ Lädt alles zu GitHub hoch.

✅ Am Schluss steht etwas wie `main -> main`.

- [ ] Fertig

---

## Schritt 6 · Auf GitHub kontrollieren · 2 Min.

1. Browser → dein Repo `IPT1` → **F5** (neu laden).

✅ Du siehst die Ordner **LS01** bis **LS07** und **Lernjournal**.
✅ Oben steht deine Commit-Nachricht.

> ❓ Ein Ordner fehlt? → Er ist leer. Lege eine Datei hinein (Schritt 4), dann Schritt 5 wiederholen.

- [ ] Fertig

---

## Schritt 7 · Synchronisieren üben: von GitHub zum Laptop (pull) · 5 Min.

Jetzt ändern wir etwas **auf GitHub** und holen es auf den Laptop.

1. Auf GitHub: Klick auf **README.md** (die oberste, im Hauptordner) → ✏️ **Stift** (Edit).
2. Schreibe eine neue Zeile, z. B.: `Repository von Vorname Nachname · BMSD26b`
3. **Commit changes…** → nochmals **Commit changes**.
4. Zurück in VS Code, im Terminal:

🐧 Linux und 🪟 Windows – gleich:
```bash
git pull
```

5. Öffne in VS Code die Datei `README.md` (im Hauptordner).

✅ Deine neue Zeile ist jetzt **auch auf dem Laptop**. Laptop und GitHub sind **synchron**.

- [ ] Fertig

---

## Schritt 8 · Synchronisieren üben: vom Laptop zu GitHub (push) · 5 Min.

1. In VS Code: Öffne `Lernjournal/README.md`.
2. Schreibe hinein:
   ```text
   # Lernjournal
   Heute habe ich mein Git-Repository eingerichtet.
   ```
3. **Ctrl + S** (speichern).
4. Im Terminal:

```bash
git add .
git commit -m "Lernjournal begonnen"
git push
```

5. Auf GitHub **F5** → `Lernjournal` öffnen → Text ist da ✅

- [ ] Fertig

---

## 🔁 Ab jetzt: jedes Mal im Unterricht

| Wann | Befehl | Warum |
|------|--------|-------|
| **Am Anfang** | `git pull` | neuesten Stand holen |
| **Während der Arbeit** | Dateien in den richtigen Ordner (z. B. `LS08`) | Ordnung |
| **Vor der Pause / am Schluss** | `git add .` | alles vormerken |
| | `git commit -m "LS08: was ich gemacht habe"` | speichern mit Nachricht |
| | `git push` | hochladen |
| **Kontrolle** | GitHub im Browser → **F5** | Ist alles da? |

> 💡 Neue Lernsession = neuer Ordner, z. B. `LS08`. Leg sofort eine Datei hinein, sonst kommt er nicht auf GitHub.

---

## 🆘 Typische Fehler

| Meldung / Problem | Bedeutung | Lösung |
|-------------------|-----------|--------|
| `fatal: not a git repository` | Du bist im falschen Ordner. | `cd ~/IPT1` 🐧 bzw. `cd ~\IPT1` 🪟 |
| `fatal: destination path 'IPT1' already exists` | Du hast schon geklont. | Nicht nochmals klonen. `cd IPT1` |
| `Author identity unknown` | Schritt 1 fehlt. | Schritt 1 machen, dann `git commit …` wiederholen |
| `nothing to commit, working tree clean` | Es gibt keine Änderungen. | Datei gespeichert? (**Ctrl + S**) |
| `rejected … (fetch first)` beim `push` | Auf GitHub ist etwas Neues. | zuerst `git pull`, dann `git push` |
| Ordner fehlt auf GitHub | Der Ordner ist leer. | Datei hineinlegen, add → commit → push |
| Anmeldung klappt nicht | GitHub-Login fehlt. | 🪟 Fenster «Sign in with your browser» nutzen · sonst Hand hoch |
| Im Terminal steht `>>` und nichts passiert | Ein Anführungszeichen fehlt. | **Ctrl + C**, Befehl neu tippen |

---

## ✅ Checkliste

- [ ] `git --version` funktioniert
- [ ] Name und E-Mail sind eingestellt
- [ ] Repo `IPT1` auf GitHub ist **privat** und hat eine README
- [ ] Lehrperson ist als Collaborator eingeladen
- [ ] Repo ist auf dem Laptop geklont
- [ ] Ordner LS01–LS07 und Lernjournal sind **auf GitHub sichtbar**
- [ ] `git pull` hat die Änderung von GitHub geholt
- [ ] `git push` hat die Änderung vom Laptop hochgeladen
