# AdvoKAI Installasjonsveiledning for MacBook Pro M1

Denne veiledningen beskriver hvordan du setter opp og kjører AdvoKAI-applikasjonen på en MacBook Pro M1.

## Innholdsfortegnelse
1.  [Systemkrav](#systemkrav)
2.  [Forberedelser](#forberedelser)
    *   [Installer Homebrew](#installer-homebrew)
    *   [Installer Node.js og npm](#installer-nodejs-og-npm)
    *   [Installer Git](#installer-git)
    *   [Installer Watchman](#installer-watchman) (Anbefalt for React Native)
    *   [Installer Xcode og Command Line Tools](#installer-xcode-og-command-line-tools)
    *   [Installer CocoaPods](#installer-cocoapods)
    *   [Installer Expo CLI](#installer-expo-cli)
3.  [Last ned AdvoKAI-prosjektet](#last-ned-advokai-prosjektet)
4.  [Konfigurasjon](#konfigurasjon)
    *   [API-nøkler og Miljøvariabler](#api-nøkler-og-miljøvariabler)
5.  [Kjøre Backend](#kjøre-backend)
6.  [Kjøre Frontend (React Native Expo)](#kjøre-frontend-react-native-expo)
    *   [Installere avhengigheter](#installere-avhengigheter)
    *   [Starte Expo-appen](#starte-expo-appen)
    *   [Kjøre på iOS Simulator](#kjøre-på-ios-simulator)
    *   [Kjøre på Android Emulator/Enhet](#kjøre-på-android-emulatorenhet)
7.  [Feilsøking](#feilsøking)

## 1. Systemkrav
*   MacBook Pro med Apple M1-brikke (eller nyere).
*   macOS Monterey (12.0) eller nyere.
*   Minst 16 GB RAM anbefales.
*   Minst 50 GB ledig lagringsplass.

## 2. Forberedelser

Før du kan sette opp AdvoKAI, må du installere noen nødvendige verktøy.

### Installer Homebrew
Homebrew er en pakkebehandler for macOS. Hvis du ikke har det installert, åpne Terminal og kjør:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
Følg instruksjonene på skjermen. Det kan hende du må legge Homebrew til i PATH-en din:
```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

### Installer Node.js og npm
AdvoKAI bruker Node.js for både backend og frontend-utvikling. `npm` (Node Package Manager) følger med Node.js.
```bash
brew install node
```
Sjekk installasjonen:
```bash
node -v
npm -v
```

### Installer Git
Git brukes for versjonskontroll. macOS kommer vanligvis med Git, men det er lurt å ha den nyeste versjonen via Homebrew.
```bash
brew install git
```

### Installer Watchman (Anbefalt for React Native)
Watchman er et verktøy fra Facebook for å se etter filendringer. Det kan forbedre ytelsen for React Native.
```bash
brew install watchman
```

### Installer Xcode og Command Line Tools
Xcode er nødvendig for iOS-utvikling. Installer det fra Mac App Store. Etter installasjon, åpne Xcode og godta lisensavtalen. Installer også Command Line Tools:
```bash
xcode-select --install
```
Åpne Xcode, gå til `Xcode > Settings... > Locations` og sørg for at `Command Line Tools` er satt til den installerte versjonen.

### Installer CocoaPods
CocoaPods brukes for å håndtere avhengigheter i iOS-prosjekter.
```bash
sudo gem install cocoapods
```
For M1 Macs kan det være bedre å installere via Homebrew:
```bash
brew install cocoapods
```

### Installer Expo CLI
Expo CLI brukes for å bygge og kjøre React Native-appen.
```bash
npm install -g expo-cli
```
Sjekk installasjonen:
```bash
expo --version
```

## 3. Last ned AdvoKAI-prosjektet

Du har mottatt AdvoKAI-prosjektet som en ZIP-fil (f.eks. `AdvoKAI_project_updated.zip`).
1.  Pakk ut ZIP-filen til en passende mappe på din Mac (f.eks. `~/Projects/AdvoKAI`).
2.  Naviger til prosjektmappen i Terminal:
    ```bash
    cd ~/Projects/AdvoKAI
    ```

## 4. Konfigurasjon

### API-nøkler og Miljøvariabler
Applikasjonen krever API-nøkler for ulike tjenester (Supabase, OpenAI, Criipto, etc.). Se dokumentet `api_keys_and_transfer_guide.md` for detaljerte instruksjoner om hvordan du skaffer disse nøklene.

**Backend Konfigurasjon:**
1.  Naviger til backend-mappen:
    ```bash
    cd backend
    ```
2.  Opprett en `.env`-fil ved å kopiere `.env.example` (hvis den finnes) eller lage en ny:
    ```bash
    cp .env.example .env # Hvis .env.example finnes
    # eller
    touch .env
    ```
3.  Åpne `.env`-filen i en teksteditor og legg inn dine API-nøkler og andre konfigurasjonsverdier. Eksempel:
    ```env
    SUPABASE_URL=din_supabase_url
    SUPABASE_ANON_KEY=din_supabase_anon_key
    SUPABASE_SERVICE_ROLE_KEY=din_supabase_service_role_key # Brukes forsiktig, kun for backend
    OPENAI_API_KEY=din_openai_api_nøkkel
    CRIIPTO_CLIENT_ID=din_criipto_client_id
    CRIIPTO_CLIENT_SECRET=din_criipto_client_secret
    CRIIPTO_REDIRECT_URI=din_app_redirect_uri_for_criipto # F.eks. http://localhost:3000/api/auth/criipto/callback
    APP_URL=http://localhost:19006 # URL for frontend-appen (Expo)
    # Andre nødvendige variabler...
    ```

**Frontend Konfigurasjon:**
1.  Naviger til frontend-mappen:
    ```bash
    cd ../frontend/advokai-app
    ```
2.  Opprett en `.env`-fil (eller konfigurer direkte i koden der det er relevant, f.eks. for Supabase-klienten i `src/utils/supabase.js`). For Supabase i frontend, brukes vanligvis `SUPABASE_URL` og `SUPABASE_ANON_KEY`.
    ```javascript
    // In src/utils/supabase.js (eller tilsvarende konfigurasjonsfil)
    import { createClient } from '@supabase/supabase-js';

    const supabaseUrl = 'din_supabase_url'; // Erstatt med din Supabase URL
    const supabaseAnonKey = 'din_supabase_anon_key'; // Erstatt med din Supabase Anon Key

    export const supabase = createClient(supabaseUrl, supabaseAnonKey, {
      // auth: { ... } // Eventuelle tilleggsinnstillinger for auth
    });
    ```
    Sørg for at disse verdiene er korrekte.

## 5. Kjøre Backend

Backend-serveren er en Node.js Express-applikasjon.
1.  Naviger til backend-mappen hvis du ikke allerede er der:
    ```bash
    cd AdvoKAI/backend
    ```
2.  Installer avhengigheter:
    ```bash
    npm install
    ```
3.  Start backend-serveren:
    ```bash
    npm start
    ```
    Serveren vil vanligvis kjøre på `http://localhost:3000` (eller en annen port spesifisert i koden/konfigurasjonen).

## 6. Kjøre Frontend (React Native Expo)

### Installere avhengigheter
1.  Naviger til frontend-mappen:
    ```bash
    cd AdvoKAI/frontend/advokai-app
    ```
2.  Installer avhengigheter:
    ```bash
    npm install
    ```
3.  Installer iOS-pods (nødvendig for native moduler):
    ```bash
    npx pod-install # Eller: cd ios && pod install && cd ..
    ```

### Starte Expo-appen
1.  Start Expo Metro Bundler:
    ```bash
    npm start
    # ELLER
    expo start
    ```
    Dette vil åpne en ny fane i nettleseren din med Expo Developer Tools. Herfra kan du velge hvordan du vil kjøre appen.

### Kjøre på iOS Simulator
1.  Sørg for at Xcode er installert og at du har minst én iOS Simulator satt opp.
2.  I Expo Developer Tools (nettleserfanen), klikk på "Run on iOS simulator".
3.  Alternativt, i terminalen der Metro Bundler kjører, trykk `i`.

### Kjøre på Android Emulator/Enhet
1.  Sørg for at Android Studio er installert og at du har en Android Emulator satt opp, eller en fysisk Android-enhet koblet til med USB-feilsøking aktivert.
2.  I Expo Developer Tools, klikk på "Run on Android device/emulator".
3.  Alternativt, i terminalen der Metro Bundler kjører, trykk `a`.

## 7. Feilsøking

*   **M1-spesifikke problemer:**
    *   **CocoaPods:** Hvis `sudo gem install cocoapods` feiler eller gir problemer, prøv `brew install cocoapods`. Sørg for at `pod` kommandoen peker til Homebrew-versjonen.
    *   **Node.js-versjoner:** Noen ganger kan det være konflikter med Node-versjoner installert via `nvm` (Node Version Manager) og Homebrew. Sørg for konsistens.
    *   **Rosetta 2:** For eldre verktøy som ikke har native M1-støtte, kan macOS automatisk bruke Rosetta 2. Hvis du støter på uventede feil med native moduler, sjekk om det er kjente M1-kompatibilitetsproblemer for de spesifikke bibliotekene.
*   **`Error: EMFILE: too many open files`:** Dette kan skje med Metro Bundler. Installer Watchman (se Forberedelser) eller øk grensen for åpne filer på systemet ditt.
*   **Pod-installasjon feiler:** Sørg for at Xcode Command Line Tools er riktig satt opp. Prøv `cd ios && pod install --repo-update && cd ..`.
*   **Nettverksproblemer:** Sørg for at backend-serveren kjører og er tilgjengelig på den konfigurerte adressen (vanligvis `http://localhost:3000`) fra frontend-appen.
*   **API-nøkler:** Dobbeltsjekk at alle API-nøkler er korrekte og lagt inn i de riktige `.env`-filene eller konfigurasjonsfilene.

--- 
Lykke til med AdvoKAI!
