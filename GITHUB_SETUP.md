# Návod na nahrání na GitHub

## Krok 1: Vytvoření GitHub repository

1. Přejděte na https://github.com
2. Přihlaste se nebo vytvořte účet
3. Klikněte na tlačítko **"New"** nebo **"+"** → **"New repository"**
4. Vyplňte:
   - **Repository name**: `kdu-csl-web` (nebo jiný název)
   - **Description**: "Webová stránka KDU-ČSL"
   - **Public** (pro GitHub Pages)
   - ❌ NEZAŠKRTÁVEJTE "Add README" (už máme vlastní)
5. Klikněte **"Create repository"**

## Krok 2: Připojení lokálního repository

Po vytvoření repository GitHub zobrazí instrukce. Použijte tento příkaz:

```bash
# Přidání remote repository (nahraďte USERNAME a REPO_NAME)
git remote add origin https://github.com/USERNAME/REPO_NAME.git

# Přejmenování hlavní větve na main (doporučeno)
git branch -M main

# Nahrání kódu na GitHub
git push -u origin main
```

**Příklad:**
```bash
git remote add origin https://github.com/mojeuzivatelskeejmeno/kdu-csl-web.git
git branch -M main
git push -u origin main
```

Při prvním push budete vyzváni k přihlášení.

## Krok 3: Povolení GitHub Pages

1. Na GitHubu přejděte do svého repository
2. Klikněte na **"Settings"** (nastavení)
3. V levém menu najděte **"Pages"**
4. V sekci **"Source"** vyberte:
   - Branch: **main**
   - Folder: **/ (root)**
5. Klikněte **"Save"**

GitHub automaticky začne publikovat web. Za chvíli bude dostupný na:
```
https://USERNAME.github.io/REPO_NAME/
```

## Krok 4: Ověření

- Počkejte 1-2 minuty
- Navštivte URL z předchozího kroku
- Měli byste vidět funkční webovou stránku!

## Příkazy pro budoucí aktualizace

Když změníte soubory:

```bash
# Uložit změny
git add .
git commit -m "Popis změn"
git push

# Změny se automaticky projeví na GitHub Pages
```

## Možné problémy a řešení

### Problém: Obrázky se nezobrazují
**Řešení**: Nahrajte skutečné obrázky do složky `assets/` nebo použijte placeholder služby.

### Problém: 404 chyba na GitHub Pages
**Řešení**: Zkontrolujte, že je GitHub Pages zapnuté v Settings → Pages a že je vybráno `main` branch.

### Problém: Změny se neprojevují
**Řešení**: GitHub Pages může mít cache, zkuste hard refresh (Ctrl+F5) nebo počkejte pár minut.

## Autentizace přes Personal Access Token (doporučeno)

GitHub již nepodporuje hesla pro git operace. Použijte Personal Access Token:

1. GitHub → Settings (váš profil) → Developer settings
2. Personal access tokens → Tokens (classic)
3. Generate new token → Vyberte **repo** scope
4. Zkopírujte token
5. Při git push použijte token místo hesla

## Alternativa: GitHub CLI

Můžete použít GitHub CLI pro jednodušší správu:

```bash
# Instalace gh (GitHub CLI)
# Na Linuxu:
sudo apt install gh

# Přihlášení
gh auth login

# Vytvoření repository přímo z terminálu
gh repo create kdu-csl-web --public --source=. --remote=origin --push
```

## GitHub Pages - Custom doména (volitelné)

Pokud chcete vlastní doménu (např. `www.kdu-csl.cz`):

1. Vytvořte soubor `CNAME` s vaší doménou
2. V DNS nastavení vaší domény přidejte CNAME záznam na `USERNAME.github.io`
3. V GitHub Pages Settings zadejte custom domain

---

**Hotovo! Vaše webová stránka je nyní online. 🎉**
