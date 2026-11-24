# Svens Desktop Cockpit – Downloads

Kostenlose Windows-App zum Aufräumen und Pflegen des PCs. Ohne Werbung, ohne Telemetrie.

## Herunterladen
Die neueste Version steht rechts unter **Releases**.
Dort das ZIP `SvensDesktopCockpit_<Version>.zip` laden, entpacken und `SvensDesktopCockpit.exe` starten.
Es wird nichts installiert. Windows 10 oder 11 genügt.

**Blaue Windows-Meldung beim ersten Start?** Das Programm ist nicht digital signiert.
„Weitere Informationen“ → „Trotzdem ausführen“.

## Updates
Die App schaut beim Start und alle 15 Minuten hier nach einer neuen Version.
Gibt es eine, erscheint links unten der Knopf **„Update …“**. Die Datei wird vor dem Austausch per SHA-256-Prüfsumme geprüft.
Einstellungen und Verlauf bleiben erhalten.

Dieses Projekt enthält nur die fertigen Downloads, keinen Quellcode.

---

## Technik

| | |
|---|---|
| Plattform | Windows 10/11, 32 und 64 Bit, nichts nachzuinstallieren |
| Sprache / UI | C# 5, Windows Forms auf .NET Framework 4, gezeichnet mit GDI+, keine externen Bibliotheken |
| Bauen | `csc.exe` aus Windows (`Bauen.cmd`), keine Entwicklungsumgebung nötig |
| Daten | portabel: `config\` und `logs\` neben der `.exe`, keine Registry, kein Installer |
| Updates | GitHub-Releases; ZIP wird mit SHA-256 geprüft, ohne Prüfsumme kein Update; abschaltbar |
| Programme/Treiber | `winget` und Windows Update, keine eigene Update-Datenbank |
| Löschen | Scans nur lesend; Papierkorb als Standard; Duplikat nur bei Byte-Gleichheit und vorhandener Kopie; Systemordner geschützt |

**Entscheidungen**
- **.NET Framework 4:** in Windows enthalten, eine kleine Datei, keine Laufzeit-Installation.
- **WinForms + eigene Zeichnung:** schneller Start, wenig Speicher, alle Designs sehen gleich aus.
- **Portabel statt Installer:** kein Eingriff ins System, Entfernen = Ordner löschen.
- **GitHub-Releases + SHA-256:** kein eigener Server, keine Nutzerdaten beim Betreiber.
- **Datenschutz:** keine Telemetrie, kein Konto; einzige automatische Verbindung ist die Update-Prüfung (IP sichtbar für GitHub).

Die `.exe` ist nicht signiert: Windows zeigt beim ersten Start SmartScreen an.
