# GitHub Actions – CI/CD Pipeline med Node.js

![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat&logo=githubactions&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white)
![CSS](https://img.shields.io/badge/CSS-1572B6?style=flat&logo=css3&logoColor=white)

> **Lärdomsprojekt** – Implementering av en komplett CI/CD-pipeline med GitHub Actions för en Node.js-applikation. Byggd under DevOps Engineer-utbildningen vid Lernia Yrkeshögskola.

---

## 📋 Om projektet

Det här projektet demonstrerar hur man bygger och automatiserar en CI/CD-pipeline med GitHub Actions. Fokus ligger på att förstå hur automatiserade arbetsflöden fungerar i praktiken – från kodändring till automatisk deploy.

### Vad det gör

- Triggar automatiskt ett bygge vid varje `push` till `main`-branchen
- Kör tester och validerar Node.js-applikationen
- Deployar applikationen automatiskt vid godkänt bygge
- Demonstrerar hur GitHub Actions integreras i ett verkligt utvecklingsflöde

---

## 🏗️ Arkitektur

```
Developer pushes code
        │
        ▼
┌─────────────────┐
│  GitHub Actions │  ← Triggas automatiskt
│    Workflow     │
└────────┬────────┘
         │
    ┌────▼────┐
    │  Build  │  ← Installerar beroenden, kompilerar
    └────┬────┘
         │
    ┌────▼────┐
    │  Test   │  ← Kör automatiska tester
    └────┬────┘
         │
    ┌────▼────┐
    │ Deploy  │  ← Publicerar applikationen
    └─────────┘
```

---

## ⚙️ CI/CD-pipeline

Workflow-filen finns i `.github/workflows/` och definierar hela pipelinen:

```yaml
name: CI/CD Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - run: npm ci
      - run: npm run build
      - run: npm test
```

---

## 🚀 Kom igång

### Förutsättningar

- Node.js 18+
- npm
- GitHub-konto

### Kör lokalt

```bash
# Klona repot
git clone https://github.com/arash00009/First-Github-actions-test.git
cd First-Github-actions-test

# Installera beroenden
npm install

# Starta applikationen
npm run dev
```

### Se pipelinen köra

1. Forka eller klona repot
2. Gör en ändring i koden
3. Pusha till `main`
4. Gå till **Actions**-fliken och se pipelinen köra live

---

## 📚 Vad jag lärde mig

| Koncept | Beskrivning |
|---------|-------------|
| **Workflows** | Hur man definierar automatiserade arbetsflöden i YAML |
| **Triggers** | `push`, `pull_request` och manuella triggers |
| **Jobs & Steps** | Strukturering av pipeline i parallella och sekventiella steg |
| **Runners** | GitHub-hostade runners (`ubuntu-latest`) |
| **Actions** | Återanvändbara actions från GitHub Marketplace |
| **Secrets** | Hantering av känsliga variabler i GitHub Secrets |

---

## 🔗 Relaterade projekt

- [Cloudist IDP – GitOps med FluxCD](https://github.com/arash00009) ← Mer avancerad CI/CD i produktion
- [Portfolio](https://arash00009.github.io)

---

## 👤 Författare

**Arash Rahimi** – DevOps Engineer Student  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-arash--rahimi92-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/arash-rahimi92/)
[![Portfolio](https://img.shields.io/badge/Portfolio-arash00009.github.io-4A9EFF?style=flat&logo=githubpages&logoColor=white)](https://arash00009.github.io)

---

## 📄 Licens

MIT License – se [LICENSE.txt](LICENSE.txt)
