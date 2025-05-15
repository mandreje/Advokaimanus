# Guide for API-nøkler og overføring til Mac

## Innholdsfortegnelse
1. [Innhenting av API-nøkler](#innhenting-av-api-nøkler)
   - [Supabase](#supabase)
   - [OpenAI](#openai)
   - [Lovdata](#lovdata)
   - [Riksdagen API](#riksdagen-api)
   - [Retsinformation.dk](#retsinformationdk)
   - [EUR-Lex](#eur-lex)
   - [Brønnøysundregistrene (BRREG)](#brønnøysundregistrene-brreg)
   - [NAV](#nav)
   - [Skatteverket](#skatteverket)
   - [Criipto](#criipto)
2. [Overføring av appen til Mac](#overføring-av-appen-til-mac)
   - [Forberedelser på Mac](#forberedelser-på-mac)
   - [Klone prosjektet fra GitHub](#klone-prosjektet-fra-github)
   - [Alternativ: Manuell overføring](#alternativ-manuell-overføring)
3. [Konfigurering av miljøvariabler](#konfigurering-av-miljøvariabler)
4. [Kjøring av appen på Mac](#kjøring-av-appen-på-mac)

## Innhenting av API-nøkler

### Supabase

1. Gå til [Supabase](https://supabase.com/) og opprett en konto
2. Klikk på "New Project" for å opprette et nytt prosjekt
3. Fyll inn prosjektnavn, passord og velg region (helst EU for GDPR-samsvar)
4. Vent til prosjektet er opprettet (kan ta noen minutter)
5. Gå til "Settings" > "API" i sidemenyen
6. Under "Project API keys", finn og kopier:
   - URL: `https://[project-id].supabase.co`
   - `anon` public key
   - `service_role` secret key (kun for backend)

### OpenAI

1. Gå til [OpenAI API](https://platform.openai.com/) og opprett en konto
2. Logg inn og gå til "API Keys" i sidemenyen
3. Klikk på "Create new secret key"
4. Gi nøkkelen et beskrivende navn (f.eks. "AdvoKAI App")
5. Kopier API-nøkkelen (den vises kun én gang)
6. Merk: Du må ha betalingsmetode registrert for å bruke API-et

### Lovdata

1. Gå til [Lovdata Pro](https://lovdata.no/pro) og opprett en konto
2. Kontakt Lovdata direkte via e-post (post@lovdata.no) eller telefon for å få tilgang til API-et
3. Spesifiser at du trenger API-tilgang for en juridisk app
4. Når du har fått tilgang, logg inn på Lovdata Pro
5. Gå til "Min side" > "API-tilgang"
6. Kopier API-nøkkelen

### Riksdagen API

1. Gå til [Sveriges Riksdag API](https://data.riksdagen.se/dokumentation/)
2. Registrer deg for API-tilgang ved å fylle ut skjemaet
3. Du vil motta en e-post med API-nøkkel og instruksjoner
4. Merk: Noen deler av API-et er åpent og krever ikke nøkkel

### Retsinformation.dk

1. Gå til [Retsinformation.dk](https://www.retsinformation.dk/)
2. Kontakt dem via kontaktskjemaet for å få API-tilgang
3. Spesifiser at du trenger tilgang for en juridisk app
4. Følg instruksjonene du mottar på e-post

### EUR-Lex

1. Gå til [EUR-Lex SPARQL](https://data.europa.eu/euodp/en/data/dataset/sparql-cellar-of-the-publications-office)
2. Registrer deg for API-tilgang
3. Følg instruksjonene for å få API-nøkkel
4. Merk: Noen deler av API-et er åpent og krever ikke nøkkel

### Brønnøysundregistrene (BRREG)

1. Gå til [BRREG Data API](https://www.brreg.no/produkter-og-tjenester/apne-data/)
2. For grunnleggende data kan du bruke det åpne API-et uten nøkkel
3. For mer omfattende data, registrer deg via [Brønnøysundregistrene API-portal](https://data.brreg.no/enhetsregisteret/api/docs/index.html)
4. Følg instruksjonene for å få API-nøkkel

### NAV

1. Gå til [NAV API-portal](https://navikt.github.io/datadeling/)
2. Registrer deg for API-tilgang
3. Følg instruksjonene for å få API-nøkkel
4. Merk: Noen deler av API-et er åpent og krever ikke nøkkel

### Skatteverket

1. Gå til [Skatteverket API](https://www.skatteverket.se/omoss/apierochoppnadata.4.3f4496fd16549fa1e38571.html)
2. Registrer deg for API-tilgang
3. Følg instruksjonene for å få API-nøkkel

### Criipto

1. Gå til [Criipto](https://www.criipto.com/) og opprett en konto
2. Velg "Sign up" og følg registreringsprosessen
3. Etter registrering, gå til "Dashboard"
4. Opprett en ny applikasjon ved å klikke på "Create application"
5. Fyll inn applikasjonsnavn og velg "BankID" som autentiseringsmetode
6. Konfigurer redirect URIs for din app
7. Under "Credentials", finn og kopier:
   - Client ID
   - Client Secret

## Overføring av appen til Mac

### Forberedelser på Mac

1. Installer [Node.js](https://nodejs.org/) (versjon 16 eller nyere)
   ```bash
   brew install node
   ```

2. Installer [Git](https://git-scm.com/)
   ```bash
   brew install git
   ```

3. Installer [Xcode](https://apps.apple.com/us/app/xcode/id497799835) fra App Store (for iOS-utvikling)

4. Installer [Homebrew](https://brew.sh/) hvis du ikke allerede har det
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```

5. Installer Expo CLI
   ```bash
   npm install -g expo-cli
   npm install -g eas-cli
   ```

### Klone prosjektet fra GitHub

Hvis du har lastet opp prosjektet til GitHub:

1. Opprett et GitHub-repository for prosjektet
   - Gå til [GitHub](https://github.com/)
   - Klikk på "New repository"
   - Gi det et navn (f.eks. "advokai")
   - Velg "Private" for å holde det privat
   - Klikk "Create repository"

2. Push koden til GitHub fra utviklingsmiljøet
   ```bash
   cd /home/ubuntu/AdvoKAI
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/yourusername/advokai.git
   git push -u origin main
   ```

3. Klone prosjektet til din Mac
   ```bash
   cd ~/Documents
   git clone https://github.com/yourusername/advokai.git
   cd advokai
   ```

### Alternativ: Manuell overføring

Hvis du ikke ønsker å bruke GitHub:

1. Komprimer prosjektmappen
   ```bash
   cd /home/ubuntu
   zip -r AdvoKAI.zip AdvoKAI
   ```

2. Last ned ZIP-filen til din Mac
   - Du kan bruke scp, rsync, eller en fildelingstjeneste som Dropbox eller Google Drive
   - Eksempel med scp (kjør på din Mac):
     ```bash
     scp username@server-ip:/home/ubuntu/AdvoKAI.zip ~/Downloads/
     ```

3. Pakk ut ZIP-filen på din Mac
   ```bash
   cd ~/Documents
   unzip ~/Downloads/AdvoKAI.zip
   ```

## Konfigurering av miljøvariabler

1. Opprett miljøvariabelfiler på din Mac

   For backend:
   ```bash
   cd ~/Documents/AdvoKAI/backend
   cp .env.example .env
   ```

   For frontend:
   ```bash
   cd ~/Documents/AdvoKAI/frontend/advokai-app
   cp .env.example .env
   ```

2. Rediger `.env`-filene og legg inn API-nøklene du har innhentet

   Backend `.env`:
   ```
   SUPABASE_URL=din_supabase_url
   SUPABASE_KEY=din_supabase_anon_key
   SUPABASE_SERVICE_KEY=din_supabase_service_key
   OPENAI_API_KEY=din_openai_api_key
   LOVDATA_API_KEY=din_lovdata_api_key
   RIKSDAGEN_API_KEY=din_riksdagen_api_key
   RETSINFORMATION_API_KEY=din_retsinformation_api_key
   EURLEX_API_KEY=din_eurlex_api_key
   BRREG_API_KEY=din_brreg_api_key
   NAV_API_KEY=din_nav_api_key
   SKATTEVERKET_API_KEY=din_skatteverket_api_key
   CRIIPTO_CLIENT_ID=din_criipto_client_id
   CRIIPTO_CLIENT_SECRET=din_criipto_client_secret
   PORT=3000
   ```

   Frontend `.env`:
   ```
   EXPO_PUBLIC_SUPABASE_URL=din_supabase_url
   EXPO_PUBLIC_SUPABASE_ANON_KEY=din_supabase_anon_key
   EXPO_PUBLIC_API_URL=http://localhost:3000/api
   ```

## Kjøring av appen på Mac

### Installere avhengigheter

1. Installer backend-avhengigheter
   ```bash
   cd ~/Documents/AdvoKAI/backend
   npm install
   ```

2. Installer frontend-avhengigheter
   ```bash
   cd ~/Documents/AdvoKAI/frontend/advokai-app
   npm install
   ```

### Kjøre backend

```bash
cd ~/Documents/AdvoKAI/backend
npm start
```

Backend-serveren vil nå kjøre på `http://localhost:3000`.

### Kjøre frontend

```bash
cd ~/Documents/AdvoKAI/frontend/advokai-app
expo start
```

Dette vil åpne Expo Developer Tools i nettleseren din. Herfra kan du:

- Kjøre appen i iOS-simulator (krever Xcode)
- Kjøre appen på en fysisk enhet ved å skanne QR-koden med Expo Go-appen

#### For iOS-simulator:
Trykk på "Run on iOS simulator" i Expo Developer Tools, eller trykk `i` i terminalen.

#### For fysisk enhet:
1. Last ned Expo Go-appen fra App Store (iOS)
2. Sørg for at Mac og iPhone er på samme WiFi-nettverk
3. Skann QR-koden som vises i Expo Developer Tools eller terminalen
4. Appen vil åpnes i Expo Go

### Bygge appen for distribusjon

Når du er klar til å distribuere appen:

1. Konfigurer eas-cli
   ```bash
   cd ~/Documents/AdvoKAI/frontend/advokai-app
   eas login
   eas build:configure
   ```

2. Bygg for iOS
   ```bash
   eas build --platform ios
   ```

3. Følg instruksjonene for å laste opp til App Store Connect

## Feilsøking

### Vanlige problemer og løsninger

#### Problem: "Cannot connect to Supabase"
- Sjekk at Supabase-URL og -nøkkel er korrekte
- Sjekk at Supabase-prosjektet er aktivt
- Sjekk at IP-adressen din ikke er blokkert av Supabase

#### Problem: "API key not valid" for eksterne tjenester
- Sjekk at API-nøklene i `.env`-filen er korrekte
- Sjekk at API-nøklene ikke har utløpt
- Sjekk at du har tilgang til de aktuelle API-ene

#### Problem: "Error: listen EADDRINUSE: address already in use :::3000"
- En annen prosess bruker allerede port 3000
- Endre PORT i `.env`-filen eller avslutt den andre prosessen

#### Problem: "Cannot find module"
- Sjekk at alle avhengigheter er installert
- Prøv å kjøre `npm install` igjen

#### Problem: "Expo command not found"
- Sjekk at Expo CLI er installert globalt
- Prøv å installere på nytt: `npm install -g expo-cli`
