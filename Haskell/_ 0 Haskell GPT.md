
# Instalacja

`curl -sSL https://get.haskellstack.org/ | sh`
https://docs.haskellstack.org/en/stable/

INTELIJ IDEA + plugins

- **Haskell Language Server (HLS)** — to narzędzie, które IDE używa do analizy składni, autouzupełniania, diagnostyki błędów itd.
	- doinstalowanie `stack install haskell-language-server`


VS-CODE

## `GHCup`
**GHCup** to narzędzie, które bardzo upraszcza zarządzanie środowiskiem Haskella, zwłaszcza w kontekście wielu wersji narzędzi.
**GHCup** to **menedżer wersji dla narzędzi Haskella**, takich jak:
- `ghc` – Glasgow Haskell Compiler    
- `cabal` – system budowania i zarządzania paczkami    
- `haskell-language-server` – językowy serwer LSP dla IDE    
- `stack` – alternatywny system budowania    
- `hlint`, `ghcup itself`, itd.


## `GHC`
**GHC** to skrót od **Glasgow Haskell Compiler** — to **główny kompilator języka Haskell**, rozwijany od lat 90. na Uniwersytecie w Glasgow.

To on:

- Tłumaczy Twój kod Haskella na kod maszynowy (lub na pośrednie formy jak LLVM, JavaScript itd.).
- Weryfikuje typy (w tym zaawansowane rozszerzenia systemu typów).
- Obsługuje lazy evaluation, pattern matching, type classes, monady, itd.
- Jest bardzo rozbudowany — ma **masę rozszerzeń językowych**, które możesz włączyć dyrektywami

Co portafi?
- **Kompilować do binarek** (np. `stack build` → plik wykonywalny)
- **Uruchamiać interaktywną konsolę** (`ghci`) — REPL do eksperymentowania
- **Generować dokumentację** (`haddock`)
- **Debugować i profilować** programy

## `Stack`

**Stack** to **narzędzie do budowania projektów Haskella**, które:
- zarządza kompilacją kodu
- pobiera zależności
- zarządza wersją GHC (kompilatora)
- upraszcza pracę nad wieloma projektami
- dba o reprodukowalne buildy dzięki **snapshotom**


Co robi?
- **Zarządza GHC**  
    Stack pobiera dokładnie tę wersję GHC, która jest potrzebna dla danego projektu.
- **Pobiera biblioteki z Hackage/Stackage**  
    Stack bazuje na tzw. **snapshotach** (`lts-X.Y`, `nightly`), które określają dokładne wersje bibliotek, co eliminuje konflikty wersji.
- **Buduje Twój projekt**  
    Kompiluje kod, linkuje zależności i tworzy binarkę, np.:
```
stack build
stack run
```

- **Uruchamia REPL (`ghci`)**  
    Środowisko interaktywne: `stack ghci`
- **Tworzy nowy projekt**   `stack new my-project simple`
    

---





































# Projekt Hello-World

## dodatkowe info *Path*
- zmienna środowiskowa `Path` - tu jest lista folderów, w których Twój system szuka programów do uruchomienia, gdy wpisujesz je w terminalu

- `stack` domyślnie instaluje swoje binarki (czyli np. zbudowane programy) w folderze:
`/home/js/.local/bin`






# Spis


- **Podstawy składni i typów** – wartości, funkcje, pattern matching, if / case.
    
- **Listy i rekursja** – podstawowe struktury i sposób ich przetwarzania.
    
- **Typy algebraiczne i dopasowanie wzorców** – `data`, `newtype`, `Maybe`, `Either`.
    
- **Wyższe funkcje i curryfikacja** – `map`, `foldr`, `filter`, itd.
    
- **Type classes** – `Eq`, `Ord`, `Show`, `Functor`, `Applicative`, `Monad`.
    
- **Efekty z Monady IO** – jak robić input/output w czystym języku.
    
- **Testowanie i debugowanie** – np. `QuickCheck`.
    
- **Narzędzia i kompilacja** – GHC, Cabal, Stack.
    
- **Projekt praktyczny** – np. parser, prosty serwer HTTP, interpreter mini-języka.





















