# mc_ccnet-state

Backup-Repo für **ccnet** (siehe [`JaVinni/mc_ccnet`](https://github.com/JaVinni/mc_ccnet)).

Der MainServer pushed hier **eine JSON pro Node** ab (plus `registry.json`).
Dateien werden von `os/main/statebackup.lua` als GitHub-Contents-PUT
(base64-content + `sha` bei Updates) auf `main` geschrieben.

- Nur der MainServer schreibt hier.
- Nodes lesen nie direkt von diesem Repo.
- Push ist **best-effort**: Fällt GitHub aus, läuft der Main normal weiter,
  der lokale State bleibt Quelle der Wahrheit.

Dateilayout:

```
registry.json          # Alle bekannten Nodes: name -> {role, caps, status, lastSeen, computerId, ...}
<nodeName>.json        # State eines einzelnen Nodes (z. B. dev.display.01.json)
```
