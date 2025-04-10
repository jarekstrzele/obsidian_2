# 📘 Jak stworzyć stronę projektu (Project Page) GitHub przy użyciu Docusaurusa

Poniżej znajdziesz kompletną instrukcję krok po kroku, jak stworzyć stronę projektu GitHub (np. `https://twoja-organizacja.github.io/nazwa-projektu/`) opartą na Docusaurusie.

---

## ✅ 1. Wymagania

- Konto GitHub z repozytorium (w organizacji lub na koncie osobistym)
- Node.js + npm zainstalowane lokalnie
- Docusaurus CLI (`npm create docusaurus@latest`)

---

## 🏗️ 2. Utwórz repozytorium projektu

Na GitHubie (np. w organizacji):

📦 Nazwa repozytorium może być dowolna, np.:
```
kurs-csharp
```

🔧 W repozytorium:
- GitHub Pages: `Source: gh-pages`, folder `/ (root)`

---

## 💻 3. Lokalnie stwórz projekt Docusaurusa

```bash
npx create-docusaurus@latest kurs-csharp classic
cd kurs-csharp
```

---

## 🌳 4. Skonfiguruj Gita

```bash
git init
git remote add origin git@github.com:twoja-organizacja/kurs-csharp.git
git checkout -b main
```

---

## ⚙️ 5. Skonfiguruj Docusaurusa

W pliku `docusaurus.config.ts`:

```ts
url: 'https://twoja-organizacja.github.io',
baseUrl: '/kurs-csharp/',
organizationName: 'twoja-organizacja',
projectName: 'kurs-csharp',
deploymentBranch: 'gh-pages',
```

---

W `package.json`, skrypt `deploy`:

```json
"deploy": "USE_SSH=true DEPLOYMENT_BRANCH=gh-pages GIT_USER=twoj_login docusaurus deploy"
```

---

## 🚀 6. Pierwszy commit

```bash
git add .
git commit -m "Initial commit from Docusaurus"
git push -u origin main
```

---

## 🌐 7. Publikacja strony

```bash
npm run build
npm run deploy
```

Docusaurus wypchnie `/build` na gałąź `gh-pages`.

---

## ✅ 8. Gotowe!

Twoja strona projektu będzie dostępna pod:

```
https://twoja-organizacja.github.io/kurs-csharp/
```

---

## 🔁 Praca z projektem

- Pracujesz zawsze na `main`
- Po każdej zmianie:
  ```bash
  git add .
  git commit -m "Aktualizacja treści"
  git push
  npm run deploy
  ```

---

🎯 To idealne rozwiązanie na dokumentację, kursy tematyczne i projekty edukacyjne 🚀


----
## Uruchamianie projektu
```shell
npm run start
```










