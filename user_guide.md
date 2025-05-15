# AdvoKAI Brukerveiledning

Velkommen til AdvoKAI! Denne veiledningen hjelper deg med å komme i gang og bruke de ulike funksjonene i applikasjonen.

## Innholdsfortegnelse
1.  [Introduksjon](#introduksjon)
2.  [Komme i gang](#komme-i-gang)
    *   [Registrering og Innlogging](#registrering-og-innlogging)
    *   [Velge Språk og Jurisdiksjon](#velge-språk-og-jurisdiksjon)
    *   [Navigasjon i Appen](#navigasjon-i-appen)
3.  [Kjernefunksjoner](#kjernefunksjoner)
    *   [KAI Chat: Din Juridiske AI-Assistent](#kai-chat-din-juridiske-ai-assistent)
    *   [DokGen: Dokumentgenerator](#dokgen-dokumentgenerator)
        *   [Opprette dokument fra mal](#opprette-dokument-fra-mal)
        *   [Opprette dokument fra beskrivelse](#opprette-dokument-fra-beskrivelse)
        *   [Analysere opplastet dokument](#analysere-opplastet-dokument)
        *   [Se og administrere dokumenter](#se-og-administrere-dokumenter)
        *   [Signere dokumenter (BankID)](#signere-dokumenter-bankid)
    *   [KAI Lovsøk: Søk i Lovverk](#kai-lovsøk-søk-i-lovverk)
    *   [KAI Saker: Saksbehandling](#kai-saker-saksbehandling)
4.  [Innstillinger](#innstillinger)
    *   [Profiladministrasjon](#profiladministrasjon)
    *   [Token-system og Kjøp](#token-system-og-kjøp)
    *   [Endre Tema (Lys/Mørk Modus)](#endre-tema-lysmørk-modus)
5.  [Viktige Tilleggsfunksjoner](#viktige-tilleggsfunksjoner)
    *   ["AI Forklar Meg"-knapp](#ai-forklar-meg-knapp)
    *   [Juridisk Ordbok](#juridisk-ordbok) (Fremtidig funksjon)
6.  [Hjelp og Støtte](#hjelp-og-støtte)

## 1. Introduksjon

AdvoKAI er en AI-drevet juridisk app designet for å bistå privatpersoner og små bedrifter med ulike juridiske oppgaver. Appen tilbyr samtalebasert juridisk hjelp, dokumentgenerering og -analyse, søk i lovverk, og enkel saksbehandling.

## 2. Komme i gang

### Registrering og Innlogging
*   **Registrering:** Hvis du er ny bruker, trykk på "Registrer" på startskjermen. Fyll inn nødvendig informasjon (navn, e-post, passord) og følg instruksjonene.
*   **Innlogging:** Hvis du allerede har en konto, trykk på "Logg inn" og skriv inn din e-post og passord.
*   **Glemt Passord:** Bruk "Glemt passord?"-funksjonen hvis du har glemt passordet ditt.

### Velge Språk og Jurisdiksjon
Etter første innlogging, eller via Innstillinger-menyen, kan du velge foretrukket språk og jurisdiksjon.
*   **Språk:** AdvoKAI støtter Norsk (standard), Engelsk, Svensk og Dansk.
*   **Jurisdiksjon:** Velg mellom Norge, Sverige, Danmark, eller EU/Internasjonal. Dette valget påvirker hvilke lovdata, maler og AI-veiledning som er tilgjengelig.
    Valget vises med flagg og fargeindikatorer i appen.

### Navigasjon i Appen
Appen har en hovedmeny (vanligvis en tabb-meny nederst) for enkel tilgang til kjernefunksjonene:
*   **KAI Chat:** For samtalebasert juridisk hjelp.
*   **DokGen:** For alt relatert til dokumenter.
*   **KAI Lovsøk:** For å søke i lover og forskrifter.
*   **KAI Saker:** For å administrere dine juridiske saker.
*   **Innstillinger:** For å administrere din konto, språk, tema, tokens, m.m.

## 3. Kjernefunksjoner

### KAI Chat: Din Juridiske AI-Assistent
*   Start en ny samtale ved å trykke på "Ny samtale"-knappen.
*   Still juridiske spørsmål, be om forklaringer, eller diskuter en sak.
*   KAI Chat bruker OpenAI og en RAG-modell (Retrieval-Augmented Generation) for å gi deg relevante svar basert på gjeldende lovverk for din valgte jurisdiksjon.
*   **Dokument-/Bildediagnostikk:** Du kan laste opp dokumenter eller bilder i chatten. AI-en vil analysere innholdet og gi deg innsikt eller svar relatert til det.
*   Samtaler lagres og kan gjenåpnes. Du kan også slette samtaler og tilknyttede dokumenter.

### DokGen: Dokumentgenerator
Naviger til "DokGen" fra hovedmenyen.

#### Opprette dokument fra mal
1.  Trykk på "Nytt dokument" eller tilsvarende handlingsknapp (ofte en "+"-knapp).
2.  Velg "Maler".
3.  Bla gjennom tilgjengelige maler for din valgte jurisdiksjon.
4.  Velg en mal. Fyll inn de nødvendige variablene i skjemaet.
5.  Dokumentet genereres. Du kan se en sikkerhetsscore og forslag til forbedringer.

#### Opprette dokument fra beskrivelse
1.  Trykk på "Nytt dokument".
2.  Velg "Opprett fra beskrivelse".
3.  Skriv en detaljert beskrivelse av dokumentet du trenger.
4.  AI-en genererer et utkast basert på din beskrivelse og gjeldende lovverk.
5.  Gjennomgå dokumentet, sikkerhetsscore og forslag.

#### Analysere opplastet dokument
1.  Trykk på "Nytt dokument".
2.  Velg "Analyser dokument".
3.  Last opp et eksisterende dokument (f.eks. PDF, DOCX).
4.  AI-en analyserer dokumentet for juridisk innhold, potensiell risiko, og gir en sikkerhetsscore og forslag til forbedringer.

#### Se og administrere dokumenter
*   Alle dine genererte og analyserte dokumenter listes i DokGen-seksjonen.
*   Trykk på et dokument for å se det, redigere (hvis aktuelt), se versjonshistorikk, eller initiere signering.
*   Du kan slette dokumenter du ikke lenger trenger.

#### Signere dokumenter (BankID)
1.  Åpne dokumentet du ønsker å signere.
2.  Trykk på "Signer"-knappen.
3.  Du vil bli guidet til `DocumentSignScreen`.
4.  Signeringsprosessen initieres. For BankID-signering vil du vanligvis bli bedt om å autentisere deg via BankID-appen eller brikke (denne delen avhenger av den spesifikke Criipto-integrasjonen og hvordan den håndteres i appen – enten via en WebView eller omdirigering).
5.  Følg statusen i appen. Du vil se når dokumentet er sendt, når det er signert, eller om noe feilet.
6.  Signerte dokumenter markeres tydelig i dokumentlisten.

### KAI Lovsøk: Søk i Lovverk
*   Naviger til "KAI Lovsøk".
*   Skriv inn søkeord relatert til lover, forskrifter eller juridiske temaer.
*   Søket bruker en RAG-modell for å finne de mest relevante resultatene fra lovdatabasene for din valgte jurisdiksjon (Norge, Sverige, Danmark, EU).
*   **Dynamisk Filtrering:** Filtrer resultatene etter kategori, land (hvis du søker bredt), og relevans.

### KAI Saker: Saksbehandling
*   Naviger til "KAI Saker".
*   Opprett en ny sak ved å trykke på "Ny sak".
*   Følg den interaktive veiledningen for å legge inn detaljer om saken.
*   **Legg ved dokumentasjon:** Last opp relevante dokumenter, bilder eller notater til saken.
*   **Frister og Fremdrift:** Sett opp frister og følg fremdriften i saken. Appen kan sende deg push-varsler for viktige datoer (krever at varsler er aktivert).
*   Hver sak kobles automatisk til relevant AI-veiledning fra KAI Chat og tilknyttede dokumenter fra DokGen.

## 4. Innstillinger

Naviger til "Innstillinger" fra hovedmenyen.

### Profiladministrasjon
*   Se og rediger din brukerprofil (navn, e-post).
*   Endre passord.

### Token-system og Kjøp
*   AdvoKAI bruker et token-system for visse funksjoner (f.eks. avansert dokumentgenerering, omfattende analyser, utvidet chat-bruk etter en gratis terskel).
*   Se din nåværende token-saldo.
*   Kjøp token-pakker eller administrer abonnementet ditt (hvis aktuelt).

### Endre Tema (Lys/Mørk Modus)
*   Velg mellom lyst tema, mørkt tema, eller la appen følge systeminnstillingen på din enhet.

## 5. Viktige Tilleggsfunksjoner

### "AI Forklar Meg"-knapp
*   Denne knappen finnes på ulike steder i appen, spesielt ved komplekse juridiske tekster eller funksjoner.
*   Trykk på den for å få en forenklet forklaring fra KAI om det aktuelle temaet.

### Juridisk Ordbok (Fremtidig funksjon)
*   En integrert ordbok for å slå opp juridiske termer og definisjoner vil bli lagt til i en fremtidig versjon.

## 6. Hjelp og Støtte

*   **Hjelp-seksjon:** I Innstillinger-menyen finner du en "Hjelp"-seksjon med svar på ofte stilte spørsmål (FAQ) og feilsøkingstips.
*   **Brukerskjema for ønsker/tilbakemeldinger:** Vi setter pris på dine tilbakemeldinger! Se etter et skjema eller en lenke i appen for å sende oss dine ønsker og forslag til forbedringer.
*   **Kontakt:** Kontaktinformasjon for kundestøtte finnes også i Innstillinger-menyen.

--- 
Takk for at du bruker AdvoKAI!
