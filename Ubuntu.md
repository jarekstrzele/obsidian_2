#pop_shell [https://support.system76.com/articles/pop-shell/](https://support.system76.com/articles/pop-shell/)

#port

aby sprawdzić, jaki program nasłuchuje na danym porcie `sudo lsof -i :8000` `sudo lsof -i numer portu`

#ubuntu #linux #opera

# problem z odtwarzaniem filmów w operze

[](https://github.com/jarekstrzele/obsidian_notes/blob/master/linux/UBUNTU.md#problem-z-odtwarzaniem-film%C3%B3w-w-operze)

link do pliku: [https://onedrive.live.com/?authkey=%21AC7ddalBsUiWsUE&id=75D48EF8D3750510%21234&cid=75D48EF8D3750510](https://onedrive.live.com/?authkey=%21AC7ddalBsUiWsUE&id=75D48EF8D3750510%21234&cid=75D48EF8D3750510)




#opera [https://gist.github.com/Thomas-Ln/c4ae803e90f9984b6612c8983c8fde1f](https://gist.github.com/Thomas-Ln/c4ae803e90f9984b6612c8983c8fde1f) chodzi o plik `libffmpeg.so` _`cp libffmpeg.so /usr/lib/x86_64-linux-gnu/opera`_


## ta metoda działa
​Problem z odtwarzaniem filmów na Udemy i Amazon Prime Video w przeglądarce Opera 118 na systemie Linux (np. Ubuntu, Mint) wynika najczęściej z braku odpowiednich kodeków (np. H.264) oraz obsługi DRM (Widevine). Poniżej przedstawiam kroki, które mogą pomóc rozwiązać ten problem.​
Opera forums
### 1. Zainstaluj brakujące kodeki multimedialne
Opera na Linuxie nie zawiera domyślnie pełnego wsparcia dla kodeków H.264 i AAC, co powoduje problemy z odtwarzaniem filmów. Aby to naprawić:​

a) Pobierz i zainstaluj odpowiedni plik libffmpeg.so
Przejdź na stronę https://github.com/nwjs-ffmpeg-prebuilt/nwjs-ffmpeg-prebuilt/releases
i pobierz wersję odpowiadającą Twojej architekturze systemu (np. 0.78.1-linux-x64.zip).

Wypakuj archiwum i skopiuj plik libffmpeg.so do katalogu Opery:​
`sudo mkdir -p /usr/lib/x86_64-linux-gnu/opera/lib_extra`
`sudo cp libffmpeg.so /usr/lib/x86_64-linux-gnu/opera/lib_extra/`


Użytkownicy potwierdzają, że ta metoda przywraca odtwarzanie filmów na stronach takich jak Udemy czy Amazon Prime Video .​

### 2. Włącz obsługę treści chronionych (DRM)
Aby odtwarzać treści chronione, takie jak filmy na Amazon Prime Video, Opera musi mieć włączoną obsługę DRM (Widevine).​

W pasku adresu Opery wpisz `opera://settings/content/protectedContent`.

Upewnij się, że opcja "Zezwalaj witrynom na odtwarzanie chronionej zawartości" jest włączona.​

W pasku adresu wpisz `opera://about` i zanotuj ścieżkę do profilu użytkownika.

Usuń foldery `WidevineCdm` i `MediaFoundationWidevineCdm` w katalogu profilu.
Uruchom ponownie Operę i przejdź do opera://components.
Kliknij "Sprawdź aktualizacje" dla komponentu Widevine.

Po zaktualizowaniu komponentu uruchom ponownie Operę.​

Ta procedura pomogła wielu użytkownikom rozwiązać problemy z odtwarzaniem treści na Amazon Prime Video .​
Reddit

### 3. Sprawdź obsługę kodeków i DRM
Aby upewnić się, że Opera obsługuje wymagane kodeki i DRM:​

Odwiedź Bitmovin DRM Demo i sprawdź, czy film się odtwarza.

Przejdź na HTML5 Test i sprawdź, czy przeglądarka obsługuje H.264 i AAC.​


### 4. Wyczyść dane przeglądarki i wyłącz rozszerzenia
Czasami rozszerzenia lub dane przeglądarki mogą powodować problemy z odtwarzaniem wideo.​
Opera forums

Wyczyść pamięć podręczną i pliki cookie:​
`opera://settings/clearBrowserData`
Wyłącz wszystkie rozszerzenia, zwłaszcza blokery reklam.

Uruchom Operę w trybie incognito i sprawdź, czy problem nadal występuje.​


---

#bluetooth BLUeTOOTH: wget [https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-105b-e065.hcd](https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM43142A0-105b-e065.hcd) sudo cp BCM43142A0-105b-e065.hcd /lib/firmware/brcm/BCM.hcd

---

MEGA [https://flathub.org/apps/details/nz.mega.MEGAsync](https://flathub.org/apps/details/nz.mega.MEGAsync)

---

MONGODB #mongo_problems

gdy na ubuntu 22.04 nie moge zainstalować mongo:
```
echo "deb http://security.ubuntu.com/ubuntu impish-security main" | sudo tee /etc/apt/sources.list.d/impish-security.list

sudo apt-get update
sudo apt-get install libssl1.1

```




