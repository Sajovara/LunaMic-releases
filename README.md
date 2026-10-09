# LunaMic – Downloads

LunaMic filtert dein Mikrofon (Noise Gate, Kompressor, EQ, De-Esser …) und
gibt es als virtuelles Mikrofon „LunaMic“ an Discord, OBS, Spiele und den
Browser weiter. Für Windows und Linux (PipeWire).

Hier liegen nur die fertigen Programmdateien.

## Herunterladen

**[Neueste Version](https://github.com/Sajovara/LunaMic-releases/releases/latest)**

- Windows: `LunaMic-windows.zip` – entpacken, `LunaMic.exe` in einen eigenen
  Ordner legen (z. B. `Dokumente\LunaMic`, **nicht** `C:\Programme`) und starten.
  Die Anleitung steht in `LIESMICH-Windows.txt`.
- Linux: `LunaMic-linux.tar.gz` – entpacken und `./LunaMic` starten.
  Anleitung in `LIESMICH-Linux.txt`.

## Aktualisieren

Am einfachsten in LunaMic selbst: **Settings → Updates → Update now**.
LunaMic schaut auch von allein nach. Einstellungen bleiben erhalten.

Oder im Terminal (beendet LunaMic, lädt die neue Version an dieselbe Stelle
und startet sie):

**Windows (PowerShell)**
```powershell
$p=(Get-Process LunaMic -EA 0).Path; if(!$p){$p="$env:USERPROFILE\Documents\LunaMic\LunaMic.exe"; ni -Force -ItemType Directory (Split-Path $p) | Out-Null}; Stop-Process -Name LunaMic -EA 0; sleep 2; iwr https://github.com/Sajovara/LunaMic-releases/releases/latest/download/LunaMic.exe -OutFile $p; start $p
```

**Linux**
```sh
p=$(readlink -f /proc/$(pgrep -x LunaMic)/exe 2>/dev/null || echo ~/Programme/LunaMic/LunaMic); p=${p% (deleted)}; mkdir -p "$(dirname "$p")"; pkill -x LunaMic; sleep 2; curl -fL -o "$p.new" https://github.com/Sajovara/LunaMic-releases/releases/latest/download/LunaMic-linux && chmod +x "$p.new" && mv "$p.new" "$p" && setsid -f "$p"
```

## Gut zu wissen

- Windows warnt beim ersten Start evtl. vor einem „unbekannten Herausgeber“,
  weil die Datei nicht signiert ist: „Weitere Informationen“ → „Trotzdem ausführen“.
- `SHA256SUMS` enthält die Prüfsummen; LunaMics eigener Updater prüft sie.
- Das virtuelle Mikrofon unter Windows ist VB-CABLE von VB-Audio
  (Spendenware, https://vb-audio.com/Cable/), in LunaMic enthalten.
