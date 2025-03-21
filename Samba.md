**Samba** to **otwartoźródłowy pakiet oprogramowania** dla systemów **Linux i Unix**, który umożliwia **udostępnianie plików i drukarek** w sieci **w taki sposób, by były widoczne i dostępne dla komputerów z systemem Windows**.



Samba implementuje **protokół SMB/CIFS (Server Message Block / Common Internet File System)**, czyli ten sam, którego używa Windows do komunikacji w sieci lokalnej (np. przy mapowaniu dysków sieciowych, przeglądaniu udostępnionych folderów, itp.).


Samba pozwala komputerowi z Linuxem:

- **zachowywać się jak "serwer plików Windows"** w sieci lokalnej,
- **dzielić się folderami i drukarkami**,
- **pozwalać innym komputerom (Windows, Linux, macOS)** na **przeglądanie, pobieranie i wysyłanie plików**.


## Konfiguracja
`sudo nano /etc/samba/smb.conf`

dodaj na końcu pliku
```bash

[Sprawdziany]
   path = /home/jarek/Sprawdziany
   browseable = yes
   guest ok = yes
   public = yes
   read only = yes
   force user = jarek

```




```bash
sudo systemctl restart smbd

```