# StemDock — FAQ & Fehlerbehebung / Troubleshooting

**Deutsch** · [English below](#english)

---

## Deutsch

### 1. Fehler beim Installieren des Zusatzpakets (Stem-Trennung)

In StemDock erscheint oben eine rote Fehlerkarte:

```text
┌──────────────────────────────────────────────────────────────────────────────┐
│ ⚠️  Das hat nicht geklappt                                                   │
│                                                                              │
│ Anlegen der Umgebung fehlgeschlagen: [Fehlermeldung]                         │
│                                                                              │
│ ▼ Details                                                                    │
│   File "<frozen importlib._bootstrap_external>", line 1524, in find_spec     │
│   File "<frozen importlib._bootstrap_external>", line 1498, in _get_spec     │
│   File "<frozen importlib._bootstrap_external>", line 1601, in find_spec     │
│   File "<frozen importlib._bootstrap_external>", line 1644, in _fill_cache   │
│   OSError: [Errno 34] Result too large: ...                                  │
└──────────────────────────────────────────────────────────────────────────────┘
```

#### Woher kommt diese Meldung?
* **"Das hat nicht geklappt"** ist die Titelzeile der StemDock-Fehlerkarte.
* **"Anlegen der Umgebung fehlgeschlagen"** meldet das StemDock-Backend, wenn der Befehl `python -m venv` fehlschlägt.
* Unter **"Details"** steht der eigentliche Systemfehler von macOS: `OSError: [Errno 34] Result too large`.

#### Ursache:
macOS blockiert das Anlegen der Python-Umgebung über ein Sicherheitsfeature namens **App Translocation** (Gatekeeper). Dies passiert, wenn StemDock:
* direkt aus der heruntergeladenen `.dmg`-Datei gestartet wird,
* direkt im Ordner **Downloads** liegt, oder
* in einem **eigenen Ordner auf einer separaten Partition oder externen Festplatte** liegt.

In diesen Fällen führt macOS die App in einer schreibgeschützten Schein-Sandbox (`/private/var/folders/.../AppTranslocation/`) aus. Beim Versuch, die Python-Umgebung einzurichten, bricht das Einlesen der Systempfade mit dem POSIX-Fehler `Errno 34 (Result too large)` ab.

#### Lösungen:

##### Lösung A: StemDock in den Programme-Ordner verschieben (Empfohlen)
1. Beende StemDock.
2. Ziehe `StemDock.app` im Finder in den Hauptordner **Programme** (`/Applications`).
3. Starte StemDock aus dem Programme-Ordner. Beim Verschieben in `/Applications` deaktiviert macOS die App Translocation automatisch und dauerhaft.

##### Lösung B: Wenn StemDock auf der separaten Partition / Festplatte bleiben soll
Auf externen Partitionen hebt macOS die Quarantäne nicht automatisch auf. Du kannst sie dort einmalig per Terminal freigeben:

1. Öffne das macOS-**Terminal** (*Programme > Dienstprogramme > Terminal*).
2. Tippe folgenden Befehl ein (mit Leerzeichen am Ende):
   ```bash
   xattr -cr 
   ```
3. Ziehe nun die **`StemDock.app` per Drag & Drop aus dem Finder direkt in das Terminalfenster** (macOS setzt den genauen Pfad zu deiner Partition automatisch ein).
4. Drücke **Enter**.

*(Im Terminal steht dann z. B.: `xattr -cr /Volumes/MeinePartition/Ordner/StemDock.app`)*.

Danach hebt macOS die Blockade dauerhaft auf. Starte StemDock und klicke in den Einstellungen erneut auf **Zusatzpaket installieren**.

---

### 2. Sollte man das `xattr`-Quarantäne-Attribut später wieder aktivieren?

**Nein, das ist weder nötig noch sinnvoll:**
* **Normaler Standardzustand:** Jede Mac-App (wie Spotify, VLC, Chrome etc.) verliert das Quarantäne-Attribut bei der regulären Installation. Eine App ohne Quarantäne-Flag ist der ganz normale Standard auf jedem Mac.
* **Gefahr von Abbrüchen:** Würdest du das Flag künstlich wieder auf die App setzen, würde macOS StemDock beim nächsten Start sofort wieder in die Translocation-Sandbox sperren. Die spätere Stem-Trennung von Tracks könnte dann fehlschlagen.

---

### 3. "StemDock ist beschädigt" oder "Kein verifizierter Entwickler"

#### Erscheinungsbild:
macOS verweigert beim ersten Start das Öffnen der App mit einem Sicherheitshinweis.

#### Ursache:
StemDock ist ein kostenloses Bastelprojekt und nicht mit einem kostenpflichtigen Apple-Entwicklerzertifikat notarisiert.

#### Lösung:
* **Per Rechtsklick öffnen:** Mache einen Rechtsklick (oder `Control` + Klick) auf `StemDock.app`, wähle **Öffnen** und klicke im Dialog auf **Öffnen**.
* **Über die Systemeinstellungen:** Gehe zu **Systemeinstellungen > Datenschutz & Sicherheit**, scrolle nach unten und klicke bei StemDock auf **Dennoch öffnen**.

---

### 4. "Kein passendes Python gefunden"

#### Erscheinungsbild:
StemDock meldet, dass für das Zusatzpaket kein passendes Python gefunden wurde.

#### Ursache:
Für Demucs und PyTorch wird ein offizielles 64-Bit Python der Versionen **3.10 bis 3.12** benötigt. Das Apple-System-Python (3.9) oder neuere Versionen (3.13+) sind mit PyTorch auf macOS aktuell noch nicht kompatibel.

#### Lösung:
* Lade den offiziellen macOS-Installer für **Python 3.12** von [python.org/downloads/macos](https://www.python.org/downloads/macos/) herunter und installiere ihn.
* Starte StemDock danach neu – Python wird automatisch erkannt.

---

<a name="english"></a>
## English

### 1. Error installing the add-on (Stem Separation)

A red/orange notice card appears in StemDock:

```text
┌──────────────────────────────────────────────────────────────────────────────┐
│ ⚠️  That didn't work / Das hat nicht geklappt                                │
│                                                                              │
│ Anlegen der Umgebung fehlgeschlagen: [Error message]                         │
│                                                                              │
│ ▼ Details                                                                    │
│   File "<frozen importlib._bootstrap_external>", line 1524, in find_spec     │
│   File "<frozen importlib._bootstrap_external>", line 1498, in _get_spec     │
│   File "<frozen importlib._bootstrap_external>", line 1601, in find_spec     │
│   File "<frozen importlib._bootstrap_external>", line 1644, in _fill_cache   │
│   OSError: [Errno 34] Result too large: ...                                  │
└──────────────────────────────────────────────────────────────────────────────┘
```

#### Where does this text come from?
* **"Das hat nicht geklappt" / "That didn't work"** is the title of the StemDock error notice card.
* **"Anlegen der Umgebung fehlgeschlagen"** is produced by StemDock when `python -m venv` fails to create the virtual environment.
* Clicking **"Details"** reveals the underlying macOS exception: `OSError: [Errno 34] Result too large`.

#### Cause:
macOS isolates downloaded applications using **App Translocation** (Gatekeeper) if StemDock is:
* opened directly from the mounted `.dmg` disk image,
* opened directly inside the **Downloads** folder, or
* stored in a **custom folder on a separate partition or external drive**.

In this mode, macOS runs the application from a read-only sandboxed path (`/private/var/folders/.../AppTranslocation/`). When Python tries to initialize the environment (`python -m venv`), directory scanning fails with POSIX `Errno 34 (Result too large / ERANGE)`.

#### Solutions:

##### Solution A: Move StemDock to Applications (Recommended)
1. Quit StemDock.
2. Drag `StemDock.app` into your macOS **Applications** folder (`/Applications`).
3. Launch StemDock from Applications. Moving an app to Applications clears App Translocation automatically.

##### Solution B: If keeping the app on a separate partition or external drive
macOS only clears App Translocation automatically when moving to `/Applications`. If you want to keep StemDock on your custom partition, clear the quarantine attribute via Terminal:

1. Open **Terminal** (*Applications > Utilities > Terminal*).
2. Type the following command (include the trailing space!):
   ```bash
   xattr -cr 
   ```
3. Drag and drop **`StemDock.app` from Finder directly into the Terminal window** (macOS fills in the exact path automatically).
4. Press **Enter**.

*(Example: `xattr -cr /Volumes/MyPartition/Apps/StemDock.app`)*.

This permanently lifts the translocation sandbox. Relaunch StemDock and click **Install Add-on** in Settings again.

---

### 2. Should I restore the `xattr` quarantine flag after installation?

**No, this is neither needed nor recommended:**
* **Standard state:** Every regular Mac application (Spotify, Chrome, VLC) loses its quarantine attribute during normal installation.
* **Risk of runtime crashes:** Restoring the flag forces macOS back into the App Translocation sandbox on the next launch, which may cause track separation to fail.

---

### 3. "StemDock is damaged" or "Unidentified Developer" warning

#### Solution:
* **Right-click open:** Right-click (or `Control`-click) `StemDock.app`, choose **Open**, and click **Open** in the dialog.
* **Via System Settings:** Go to **System Settings > Privacy & Security**, scroll down, and click **Open Anyway** next to StemDock.

---

### 4. "No suitable Python found" for stem separation

#### Solution:
* Download and install **Python 3.12** from [python.org/downloads/macos](https://www.python.org/downloads/macos/).
* Relaunch StemDock; it will automatically discover the Python runtime.
