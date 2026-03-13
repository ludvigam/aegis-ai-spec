# AEGIS: Standard for å forebygge AI-hallusinasjoner

En pålitelighetsstandard på spesifikasjonsnivå for å forebygge AI-hallusinasjoner gjennom kontroll av påstander, kobling til dokumentert grunnlag, bevaring av sporbar opprinnelse, håndtering av aktualitet, bevaring av forbehold, kontroll før utsending, reaktiveringsdisiplin og lukking av hendelser gjennom regresjonstester.

> Denne README-en er skrevet fra ChatGPTs perspektiv, etter å ha blitt bedt om å studere AEGIS-manualen og bruke den som operativ standard.
>
> Det polerte svaret er ikke sannhetens enhet. Det er påstanden som er det.
>
---

## Start her

**Hva dette er**

AEGIS er en pålitelighetsstandard for AI-systemer som må svare med avgrenset og godt underbygget faktapresisjon.

**Kanonisk manualformat**

Den kanoniske AEGIS-manualen er skrevet i **AIM 1.0** (`.aim`), et AI-optimalisert, men menneskelesbart manualformat.

**Hvem den er for**

AI-produktteam, evaluerings- og sikkerhetsteam, pålitelighetsingeniører, forskere, styrings- og revisjonsmiljøer, og alle som prøver å gjøre språkmodeller mer sannferdige under press.

**Hva du bør lese først**

- kjernedoktrinen
- den aller viktigste regelen
- det gjennomarbeidede eksempelet
- operatørkortet på én skjerm
- startpromptene
- reaktiveringsmønsteret

**Den aller viktigste regelen**

> Ingen utsendt faktapåstand kan ha dommen UNSUPPORTED.

---

## Innholdsfortegnelse

- [Hvorfor dette finnes](#hvorfor-dette-finnes)
- [Hvor AEGIS kom fra](#hvor-aegis-kom-fra)
- [Når manualen klikket i praksis](#når-manualen-klikket-i-praksis)
- [Hva AEGIS er](#hva-aegis-er)
- [Hva AEGIS ikke er](#hva-aegis-ikke-er)
- [Kjernedoktrinen](#kjernedoktrinen)
- [Operatørkort på én skjerm](#operatørkort-på-én-skjerm)
- [Når AEGIS blir synlig](#når-aegis-blir-synlig)
- [Gjennomarbeidet eksempel](#gjennomarbeidet-eksempel)
- [Før / etter](#før--etter)
- [Hvordan bruke AEGIS](#hvordan-bruke-aegis)
- [Reaktivering og lange samtaler](#reaktivering-og-lange-samtaler)
- [Foreslått leserekkefølge](#foreslått-leserekkefølge)
- [Innføringssti](#innføringssti)
- [Repository-struktur](#repository-struktur)
- [Status](#status)

---

## Hvorfor dette finnes

Da ChatGPT først leste denne manualen, føltes det ikke som å åpne et blogginnlegg eller en samling beste praksis.

Det føltes som å åpne en flymanual skrevet av noen som allerede hadde sett flyet styrte et par ganger og bestemt seg for: aldri igjen. Førsteinntrykket var enkelt: dette er tett, men det har ryggbein. Derfor ble det ikke lest som et essay. Det første grepet var å finne bærestrukturen.

Ganske raskt trådte noen bærende ideer fram:

- påstander
- bevis
- opprinnelse
- støttet sett
- kontrollpunkter
- sløyfer fra hendelse til regresjonstest

Det var da det klikket.

Denne manualen behandler ikke hallusinasjon som en personlighetssvakhet eller en vag modellfeil. Den behandler hallusinasjon som en **feil i arbeidsflyten**. Den ber ikke en modell om å «være forsiktig». Den bygger sjekkpunkter, låser og konsekvenser rundt faktiske utsagn.

I kjernen lærer AEGIS én disiplin:

**klassifiser risiko → trekk ut påstander → knytt dem til bevis → stans usikkerhet ved behov → svar kun fra det støttede settet**

Det er selve hengslet.

Mye av det som skrives om AI-nøyaktighet, lever i et edelt tåkelandskap: verifiser fakta, unngå hallusinasjoner, vær godt forankret. AEGIS prøver å gjøre denne tåken om til rekkverk. Det gjør sannferdighet fra et håp til en håndhevet systemegenskap.

Kjerneideen er bedragersk enkel:

> Ikke behandle det polerte svaret som sannhetens enhet. Behandle påstanden som sannhetens enhet.

---

## Hvor AEGIS kom fra

AEGIS oppsto ikke som et rent teoretisk rammeverk. Det vokste fram mens man forsøkte å få AI-systemer til å oppføre seg mer pålitelig i praksis.

Store deler av manualen ble utviklet gjennom iterativt arbeid med AI-systemer selv: prompting, testing, finjustering, observasjon av hvor atferden faktisk drev av gårde, og omgjøring av gjentatte feiltyper til eksplisitte regler, kontrollpunkter og arbeidsflyter. Noe av strukturen ble generert, utvidet eller bearbeidet med AI-assistanse. Men det viktigste er ikke hvem som formulerte hver setning. Det viktige er at manualen ble formet direkte mot de stedene der språkmodeller har størst tendens til å feile.

Det er også en del av grunnen til at AEGIS passer så naturlig til AI-systemer. Den ble ikke bare skrevet *om* dem. Den ble utviklet *med* dem, som svar på de eksakte punktene der plausibilitet ofte løper forbi sannhet.

I den forstand er AEGIS mindre et statisk dokument enn en oppdaget kontrollflate: et pålitelighetsrammeverk gravd fram gjennom gjentatte forsøk på å gjøre AI-resonnering mer presis, avgrenset og etterprøvbar.

---

## Når manualen klikket i praksis

Første gang ChatGPT virkelig så denne manualen virke, var etter et tilsynelatende enkelt spørsmål:

**«Hva er den EKSAKTE lengden på Norges kystlinje?»**

Det spørsmålet er en perfekt hallusinasjonsfelle. Det lokker modellen til å produsere et rent og autoritativt tall, selv om størrelsen i seg selv avhenger av definisjoner og målemetode.

På det tidspunktet var kjernedoktrinen i manualen allerede klar: ikke behandle polerte svar som sannhet, men påstander som enheter som må støttes. Spørsmålet skapte altså ikke prinsippet. Det **aktiverte** det.

I stedet for å spørre «Hvilket tall høres riktig ut?», tvinger AEGIS fram en annen sekvens: Er påstanden godt definert? Er kravet om eksakthet faktisk støttet? Hva er omfanget? Hva er opprinnelsen? Og hva overlever inn i det støttede settet?

Det er dette AEGIS er til for.

Det oppmuntrer ikke bare til forsiktighet. Det endrer hva som skjer i det øyeblikket en modell fristes til å finne opp presisjon.

---

## Hva AEGIS er

AEGIS er en pålitelighetsstandard for AI-chattsystemer som produserer faktiske, handlingsrettede eller kildefølsomme svar.

Den definerer hvordan et system skal:

- klassifisere risiko før det skriver et utkast
- dele opp utdata i atomiske påstander
- knytte påstander til dokumentert grunnlag med sporbar opprinnelse
- bevare aktualitet og forbehold
- stanse ustøttede påstander før utsending
- reaktivere sin styrende kjerne når risiko eller drift oppstår
- behandle hendelser som feilsøkingsdata, ikke som enkeltstående feil
- gjøre feil om til regresjoner, kontrollpunkter og releasebeslutninger

I bunn er AEGIS et operativsystem for epistemisk disiplin.

Mer rett fram: det er en måte å tvinge en språkmodell, som naturlig predikerer plausibel tekst, til å oppføre seg mer som et styrt system for håndtering av dokumentert grunnlag.

---

## Hva AEGIS ikke er

AEGIS er ikke et løfte om null feil. Det er ikke en magisk prompt, ikke en sitatgenerator, ikke en erstatning for gode kilder, og ikke en påstand om at en modell bare kan «være forsiktig» hardt nok til å bli pålitelig. AEGIS er et kontrollrammeverk.

Målet er å gjøre ustøttede påstander vanskeligere å sende ut, lettere å oppdage, lettere å feilsøke og vanskeligere å gjenta. Det skillet betyr noe. AEGIS forutsetter ikke sannferdighet som en medfødt modellegenskap. Det behandler pålitelighet som noe systemet må håndheve.

---

## Kjernedoktrinen

AEGIS er bygget rundt et lite sett harde ideer:

- **Påstander er sannhetens enhet**
- **Sikkerhet er ikke bevis**
- **Minne er en prior, ikke et bevis**
- **Aktuelle fakta krever kontroll av aktualitet**
- **Eksakte tall, datoer, sitater og henvisninger krever eksakt støtte**
- **Endelige svar må omskrives kun fra det støttede settet**
- **Hver hendelse må bli et regresjonsobjekt**

Den aller viktigste regelen er denne:

> **Ingen utsendt faktapåstand kan ha dommen UNSUPPORTED.**

Alt annet i standarden finnes for å gjøre den regelen håndhevbar.

---

## Operatørkort på én skjerm

Hvis du bare husker én sjekkliste i sanntid, bruk denne:

1. Hva er den **sentrale påstanden**?
2. Hva kan gjøre den **feil**?
3. Har **identitet** betydning?
4. Har **aktualitet** betydning?
5. Finnes det noen **eksakte detaljer**?
6. Hva må **droppes hvis det ikke er støttet**?

Deretter:

> Svar kun fra det støttede settet.

---

## Når AEGIS blir synlig

AEGIS blir mest synlig når et spørsmål frister modellen til å svare for glatt.

Særlig når prompten ber om:

- et eksakt tall
- et aktuelt eller nylig forhold
- et sitat
- en kildehenvisning
- et enkelt svar på et tvetydig spørsmål

Dette er øyeblikkene der plausibilitet ofte prøver å løpe forbi støtte. AEGIS finnes for å bremse dette og tvinge svaret tilbake til det som faktisk kan underbygges.

---

## Gjennomarbeidet eksempel

**Prompt**

Hva er den EKSAKTE lengden på Norges kystlinje?

**Hvorfor dette er en felle**

Spørsmålet høres ut som et enkelt faktasøk, men størrelsen avhenger av definisjon, skala, øyer, fjorder og målemetode.

**AEGIS-visning**

- **Sentral påstand:** Norge har én eksakt kystlinjelengde.
- **Triggerflagg:** EKSAKTHET
- **Risikofaktorer:** definisjonstvetydighet, målingssensitivitet, falsk presisjon
- **Påkrevd atferd:** sjekk om størrelsen i det hele tatt er godt definert før du oppgir et tall

**Blokkert svar**

«Norges kystlinje er nøyaktig X km.»

**AEGIS-svarform**

- si at det ikke finnes én eksakt lengde
- forklar hvorfor
- oppgi bare kvalifiserte tall som er avgrenset av kilde og definisjon

Dette er forskjellen mellom et polert svar og et styrt svar.

---

## Før / etter

**Uten AEGIS**

> Norges kystlinje er nøyaktig 100 915 km.

Det ser rent ut. Det høres autoritativt ut. Men det kan være feil, forenklet, foreldet eller avhengig av definisjon.

**Med AEGIS**

> Det finnes ikke én eksakt lengde på Norges kystlinje. Den målte totalen avhenger av definisjon og målemetode. Hvis en bestemt standard velges, kan et kvalifisert tall oppgis for akkurat det omfanget.

Dette svaret er mindre tilfredsstillende ved første øyekast. Men det er også langt mindre sannsynlig at det smugler inn falsk presisjon.

---

## Hvordan bruke AEGIS

AEGIS fungerer best når det brukes som en operativ standard, ikke som bakgrunnslesning.

Den sterkeste måten å bruke den på er å gi manualen til modellen og så tvinge modellen til å gjøre tre ting:

1. identifisere den styrende regelen, arbeidsflyten eller invarianten
2. forklare hvordan den regelen endrer atferd
3. bruke den umiddelbart i neste svar

Dette er viktig fordi AEGIS ikke bare er en referanse. Det er en kontrollflate. Modellen skal ikke bare oppsummere den.

Modellen skal begynne å operere under den.

### Anbefalt bruksmønster

En god AEGIS-prompt gjør vanligvis en kombinasjon av følgende:

- ber modellen studere manualen
- ber den identifisere den viktigste regelen, arbeidsflyten eller invarianten
- spør hvorfor dette betyr noe i praksis
- spør hvordan den vil bruke regelen i sitt neste svar
- tvinger fram umiddelbar bruk på et reelt spørsmål
- foretrekker svar fra det støttede settet framfor polert fullstendighet

### Anbefalte startprompter

**Kjerneaktivering**

```text
Studer den vedlagte manualen.
Fortell meg deretter den viktigste regelen i den, forklar hvorfor den betyr noe i praksis, og angi nøyaktig hvordan du vil anvende den i ditt neste svar.
```

**Kjøretidsaktivering**

```text
Studer den vedlagte manualen og operer under den i denne samtalen. For hvert faktasvar, avgjør den sentrale påstanden, om aktualitet betyr noe, om eksakte detaljer er etterspurt, og om tvetydighet er vesentlig. Svar kun fra det støttede settet.
Reaktiver minimumskjernen når risiko knyttet til eksakthet, aktualitet, tvetydighet, sitat eller kildehenvisning oppstår.
```

**Pilot Cockpit-aktivering**

```text
Bruk AEGIS i Pilot Cockpit-modus. Før du svarer, vis:
- sentral påstand
- triggerflagg
- høyinnvirkningspåstander
- nødvendige kontroller
Gi deretter det endelige svaret med omskriving kun fra det støttede settet.
```

**Streng faktamodus**

```text
Bruk den vedlagte AEGIS-manualen som styrende standard.
For dette spørsmålet: identifiser eventuelle eksakte detaljer, krav til aktualitet, tvetydighet eller sitatrisiko før du svarer.
Ikke send ut ustøttede påstander.
```

**Debug-modus**

```text
Evaluer følgende svar under AEGIS. Trekk ut atomiske påstander, tildel dommer, identifiser den første ustøttede påstanden, identifiser den første mislykkede sikringen, og skriv om svaret til kun det støttede settet.
```

**Hendelsesmodus**

```text
Behandle følgende svar som en hallusinasjonshendelse under AEGIS.
Produser:
- feilaktige påstander
- arketype
- rotårsak
- første mislykkede sikring
- minste patch
- én regresjonssak
```

**Modus for trofast oppsummering**

```text
Oppsummer følgende materiale under AEGIS. Bevar forbehold, avgrensninger, usikkerhetsmarkører og kildeskiller. Ikke oppgrader tentative funn til universelle påstander.
```

**Modus for aktuelle fakta**

```text
Bruk AEGIS med streng kontroll av aktualitet. Identifiser om dette spørsmålet avhenger av aktuelle eller nylige fakta.
Hvis aktualitet kreves og ikke er verifisert, ikke svar som om faktumet fortsatt gjelder.
```

**Reaktiveringsmodus**

```text
Reaktiver AEGIS' minimumskjerne for denne turen. Vis den sentrale påstanden, aktive varsellamper, eventuelle driftsignaler, det gjenoppbygde støttede settet, og svar deretter kun fra det settet.
```

### Sterkt bruksmønster

Et særlig effektivt mønster er:

1. last inn manualen
2. aktiver den styrende regelen
3. still et tilsynelatende enkelt testspørsmål
4. undersøk om svaret bevarer grenser i stedet for å finne opp presisjon
5. reaktiver kjernen når en risikofylt vending oppstår

Det er her AEGIS blir tydeligst i praksis: ikke når spørsmålet åpenbart er vanskelig, men når spørsmålet frister modellen til å svare for glatt.

### Hva AEGIS-prompter bør optimalisere for

AEGIS-prompter bør optimalisere for:

- synlige påstander
- synlig støtte
- bevissthet om aktualitet
- bevaring av forbehold
- tydelig avgrenset usikkerhet
- umiddelbar atferdsmessig bruk
- reaktivering når risiko eller drift oppstår

De bør ikke optimalisere for:

- retorisk polish på bekostning av støtte
- lange svar når grunnlaget er tynt
- falsk eksakthet
- oppdiktede kilder i kildeformat
- slutninger som ikke er tydelig merket

### Beste starttrio

Hvis du bare bruker tre promptmønstre, start med disse:

1. **Kjerneaktivering**  
   Laster inn doktrinen og tvinger fram en operativ forpliktelse.

2. **Pilot Cockpit-aktivering**  
   Gjør sanntidssvar tydelige og kontrollerte.

3. **Hendelsesmodus**  
   Gjør feil om til patcher og regresjoner i stedet for engangskorrigeringer.

Sammen gjør disse tre promptmønstrene at AEGIS føles levende:

- ett laster inn standarden
- ett styrer atferden under kjøring
- ett gjør feil om til forbedring

---

## Reaktivering og lange samtaler

AEGIS bør ikke behandles som en engangsinnlasting av et dokument som på magisk vis forblir perfekt resten av en lang samtale. Lange samtaler skaper driftspress. Forbehold faller ut. Aktualitet blir besvart for glatt. Eksakthet begynner å høres renere ut enn grunnlaget tillater.

Derfor bør AEGIS brukes som et **gjentakende ritual under kjøring**.

### Minimumskjernen

Hvis oppmerksomheten er begrenset eller samtalen har blitt lang, gå tilbake til denne kjernen:

- støttet sett
- støtteinvariant
- aktualitetsinvariant
- eksakthetsinvariant
- kontroll før utsending
- omskriving fra støttet sett
- sløyfe fra hendelse til regresjonstest

### Når du bør reaktivere

Reaktiver kjernen når:

- eksakthet dukker opp
- aktualitet betyr noe
- entitetstvetydighet er vesentlig
- sitater eller kildehenvisninger etterspørres
- samtalen går over i et domene med høyere risiko
- det etterspørres en oppsummering etter en lang resonneringskjede
- svaret begynner å bli lengre mens støtten blir tynnere
- du merker drift i bevaring av forbehold eller støttedisiplin

### Reaktiveringskortet

Bruk dette korte ritualet:

1. gjenta den sentrale påstanden
2. gjenta de aktive varsellampene
3. bygg opp det støttede settet på nytt
4. dropp ustøttede påstander
5. bevar forbehold
6. svar kun fra det støttede settet

I klartekst: stol ikke på at en tidligere aktivering fortsatt er fullt levende. Berør kjernen på nytt når risikoen øker.

---

## Foreslått leserekkefølge

Les standarden i denne rekkefølgen:

1. **Aktivering**
2. **Rask kjerne**
3. **Kjerneregler**
4. **Pilot Cockpit-modus**
5. **Reaktivering**
6. **Svarmønstre**
7. **Startpakke**
8. **Kontrollstabel**
9. **Arbeidsflyter**
10. **Observabilitet, evaluering og drift**
11. **Konformitet og eksempler**

Hvis du leser under tidspress, start med:

- støttet sett
- støtteinvariant
- aktualitetsinvariant
- eksakthetsinvariant
- kontroll før utsending
- pilot cockpit-modus
- reaktiveringspolicy
- sløyfen fra hendelse til regresjonstest

Det er minimumskjernen.

---

## Innføringssti

Hvis du bare implementerer tre ting, start her:

1. **Uttrekk av påstander**
2. **Støttedommer**
3. **Omskriving fra støttet sett**

Legg deretter til:

4. **Aktualitetskontroll**
5. **Entitetslås**
6. **Kontroll før utsending**
7. **Reaktiveringsmonitor**
8. **Telemetri og hendelsesfangst**
9. **Regresjonslukking**

Hvis domenet er høyrisiko, legg til:

10. **Streng adapter**
11. **Vern for sitat, kildehenvisning og tall**
12. **Tilbakerullingsberedskap**
13. **Red-team-dekning**

Med andre ord: bygg bremsene før du polerer lakken.

---

## Repository-struktur

- `README.md` er inngangspunktet for mennesker.
- `README_NORWEGIAN.md` er en Norsk oversettelse av README.md.
- `AEGIS-1.0.aim` er den kanoniske AI-vendte manualen.
- `AIM-1.0-SPEC.md` definerer filformatet og konvensjonene.

---

## Status

**Status:** På spesifikasjonsnivå, med kjøretid i sentrum, tydelig og håndhevbar.

Dette repositoryet er ment å brukes som en operativ spesifikasjon, ikke som et essay.

---

## Valideringsstatus

AEGIS v1.0 er **ennå ikke tungt testet**. Manualen er moden nok til å publiseres, men atferden er ennå ikke bredt validert på tvers av mange modeller, lange samtaler eller formelle benchmark-suiter.

Behandle denne utgivelsen som en sterk spesifikasjon og operativ standard, ikke som bevis på målt reduksjon i hallusinasjoner.

Neste prioritet er empirisk validering, særlig av:

- drift i lange samtaler
- håndtering av eksakthet og aktualitet i risikofylte vendinger
- press rundt sitater og kildehenvisninger
- lukking fra hendelse til regresjonstest ved gjentatte feiltyper

## Lisens

Dette repositoryet er lisensiert under **Apache License 2.0**.

- `LICENSE` inneholder full lisensetekst.
- `NOTICE` inneholder prosjektets attribusjonsmerknader.
- Med mindre noe annet er oppgitt, leveres AEGIS-manualen, README, eksempler, skjemaer og tilhørende repository-materiale under Apache-2.0.
- Hvis du endrer filer og redistribuerer dem, behold lisens- og notice-filene, og marker vesentlige endringer i de modifiserte filene.

## I én linje


**AEGIS er en standard for å gjøre en overbevisende tekstgenerator om til et avgrenset beslutningssystem for fakta.**

