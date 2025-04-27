# 📘 Jak stworzyć główną stronę organizacji GitHub przy użyciu Docusaurusa

Poniżej znajdziesz kompletną instrukcję krok po kroku, jak stworzyć główną stronę organizacji GitHub (np. `https://twoja-organizacja.github.io`) opartą na Docusaurusie.

---

## ✅ 1. Wymagania

- Konto GitHub z uprawnieniami do organizacji
- Node.js + npm zainstalowane lokalnie
- Docusaurus CLI (`npm create docusaurus@latest`)

---

## 🏗️ 2. Utwórz repozytorium organizacyjne

Na koncie organizacji GitHub:

📦 **Nazwa repozytorium musi być taka sama jak domena GitHub Pages**:
```
twoja-organizacja.github.io
```

🔧 W repozytorium:
- Ustaw domyślną gałąź: `master`
- GitHub Pages: `Source: master`, folder `/root`

---

## 💻 3. Lokalnie stwórz projekt Docusaurusa

```bash
npx create-docusaurus@latest main-page classic
cd main-page
```

---

## 🌳 4. Skonfiguruj Gita

```bash
git init
git remote add origin git@github.com:twoja-organizacja/twoja-organizacja.github.io.git
git checkout -b source
```

---

## ⚙️ 5. Zmień konfigurację Docusaurusa

W pliku `docusaurus.config.ts`:

```ts
url: 'https://twoja-organizacja.github.io',
baseUrl: '/',
organizationName: 'twoja-organizacja',
projectName: 'twoja-organizacja.github.io',
deploymentBranch: 'master',
```

---

W `package.json`, skrypt `deploy`:

```json
"deploy": "USE_SSH=true DEPLOYMENT_BRANCH=master GIT_USER=twoj_login docusaurus deploy"
```

---

## 🚀 6. Pierwszy commit

```bash
git add .
git commit -m "Initial commit from Docusaurus"
git push -u origin source
```

---

## 🌐 7. Publikacja strony

Będąc na gałęzi `source`, wykonaj:

```bash
npm run build
npm run deploy
```

Docusaurus zbuduje stronę i wypchnie ją do `master`.

---

## ✅ 8. Gotowe!

Twoja strona będzie dostępna pod:

```
https://twoja-organizacja.github.io/
```

---

## 🔁 Praca z projektem

- Pracuj zawsze na gałęzi `source`
- Po każdej zmianie:
  ```bash
  git add .
  git commit -m "Zmiany w stronie"
  git push
  npm run deploy
  ```

---


