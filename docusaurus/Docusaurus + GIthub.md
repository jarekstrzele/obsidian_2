
# Konfiguracja Docusaurusa + GitHub Pages krok po kroku

---

## Utwórz repozytorium na GitHub

- Publiczne (bo GitHub Pages nie działa z prywatnymi repo na darmowym koncie)
    
- Np. `teoria-test-github-classroom`
    
- W organizacji lub na koncie osobistym
    

---

## Zainicjalizuj Docusaurusa lokalnie

```
npx create-docusaurus@latest <nazwa-projektu> classic 

cd <nazwa-projektu>

npm install
```


## Uruchom projekt
```
npm run start
```


##  Skonfiguruj `docusaurus.config.js`

Zmień te linie:

```js
url: 'https://twojanazwa.github.io', // bez nazwy repo! 
baseUrl: '/teoria-test-github-classroom/', 
organizationName: 'twojanazwa', // konto lub organizacja GitHub 
projectName: 'teoria-test-github-classroom', // nazwa repozytorium`
```

	

---

## 📦 4. W pliku `package.json`

Dodaj pole `homepage` i scriptd
```json
`"homepage": "https://twojanazwa.github.io/teoria-test-github-classroom",`
"scripts": {   
	"deploy": "USE_SSH=true docusaurus deploy",   
	"build": "docusaurus build",  
	"start": "docusaurus start" }
```


działający z `mobile`
```json

"scripts": {
    "docusaurus": "docusaurus",
    "start": "docusaurus start",
    "build": "docusaurus build",
    "swizzle": "docusaurus swizzle",
    "deploy": "USE_SSH=true DEPLOYMENT_BRANCH=gh-pages GIT_USER=jarekstrzele docusaurus deploy",
    "clear": "docusaurus clear",
    "serve": "docusaurus serve",
    "write-translations": "docusaurus write-translations",
    "write-heading-ids": "docusaurus write-heading-ids",
    "typecheck": "tsc"
  },


---
```



## 🔐 5. Skonfiguruj `git` z repozytorium GitHub



```
git init 
git remote add origin git@github.com:twojanazwa/teoria-test-github-classroom.git`
```

Zamień `twojanazwa` na Twoją nazwę użytkownika lub organizacji.

🛡️ **Upewnij się, że używasz SSH, nie HTTPS**.



---

## 🚀 6. Pierwszy deploy

W terminalu:

```bash
git add . 
git commit -m "Initial commit" 
git push -u origin master`
```

Potem:

`GIT_USER=twojanazwa npm run deploy`

_lub po dodaniu `USE_SSH=true` w `package.json`, wystarczy:_


`npm run deploy`

---

## 🌍 7. Skonfiguruj GitHub Pages

Na GitHubie:

- Wejdź w **Settings → Pages**
    
- Wybierz:
    
    - **Branch**: `gh-pages`
        
    - **Folder**: `/ (root)`
        
- Zapisz
    

---

## ✅ 8. Gotowe! Strona dostępna pod:


`https://twojanazwa.github.io/teoria-test-github-classroom/`

---

## 🧠 Co dalej?

- Lekcje umieszczaj w `docs/`
    
- Sidebar generuje się automatycznie lub przez `sidebars.js`
    
- Po każdej zmianie:
    
    bash
    
    CopyEdit
    
    `git add . && git commit -m "nowa lekcja" git push npm run deploy`














