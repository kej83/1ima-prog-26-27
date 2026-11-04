# JavaScript 4: OG og ELLER – elevhefte

**Nytt i dette heftet: `&&` og `||`**

| Tegn | Les det som | Hele uttrykket er sant når ... | Eksempel fra timen |
| --- | --- | --- | --- |
| `&&` | OG | **begge** delene er sanne | `bruker == riktigBruker && passord == riktigPass` |
| <code>&#124;&#124;</code> | ELLER | **minst én** av delene er sann | <code>alder &lt; 12 &#124;&#124; alder &gt;= 67</code> |

**Hvor er tegnene på tastaturet?**

- `&` : Shift + 6
- `|` : Windows: tasten til venstre for 1. Mac: Alt + 7.

Du skriver alltid **to** tegn: `&&` og `||`.

> **Vanlige feil – se opp!**
>
> - ❌ `time >= 10 && < 20` ✅ `time >= 10 && time < 20` – du må skrive variabelen i **begge** delene.
> - ❌ `svar == "ja" || "Ja"` ✅ `svar == "ja" || svar == "Ja"` – samme regel her.
> - ❌ `if (alder = 10)` ✅ `if (alder == 10)` – ett likhetstegn gir en verdi, to likhetstegn sammenligner.

<!-- side -->

## Eksempel 1: Er butikken åpen?

<div class="side-by-side">
<div>

Butikken er åpen fra kl. 10 til kl. 20. Du skriver hva klokka er, og siden svarer om butikken er åpen eller stengt.

Lag filen `butikk.html`.

**Slik skal siden se ut** ►

</div>
<div>

```text
+--------------------------------------------+
|             Er butikken åpen?              |
|     Åpningstider: kl. 10–20 hver dag       |
|  Hva er klokka? Skriv bare timetallet.     |
|            [  14  ]   [Sjekk]              |
|   Klokka er 14. Butikken er åpen!          |
+--------------------------------------------+
```

</div>
</div>

### Steg 1 – Skjelettet og CSS-en

Skriv `!` og trykk Tab. Endre `<title>` til `Er butikken åpen?`, og skriv denne CSS-en i et `<style>`-element rett over `</head>`:

<div class="cols">

```css
body {
  font-family: Arial, sans-serif;
  text-align: center;
  background-color: #f0f4f8;
}
input {
  font-size: 20px;
  padding: 10px;
  width: 100px;
  text-align: center;
  border: 2px solid #1f3a5c;
  border-radius: 10px;
}
```

```css
button {
  font-size: 20px;
  padding: 10px 20px;
  border: none;
  border-radius: 10px;
  background-color: #1f3a5c;
  color: white;
}
button:hover {
  background-color: #3d6a9e;
}
#txtSvar {
  font-size: 24px;
  font-weight: bold;
}
```

</div>

### Steg 2 – HTML-en

Skriv dette inni `<body>`:

```html
  <h1>Er butikken åpen?</h1>
  <p>Åpningstider: kl. 10–20 hver dag</p>
  <p>Hva er klokka? Skriv bare timetallet (0–23).</p>

  <input type="number" id="inpTime">
  <button onclick="sjekk()">Sjekk</button>

  <p id="txtSvar"></p>
```

### Steg 3 – Åpent eller stengt? (`&&`)

Skriv en `<script>`-blokk nederst i `<body>`, rett over `</body>`:

```html
  <script>
    let apner = 10;
    let stenger = 20;

    function sjekk() {
      let time = Number(inpTime.value);

      if (time >= apner && time < stenger) {
        txtSvar.textContent = `Klokka er ${time}. Butikken er åpen!`;
      } else {
        txtSvar.textContent = `Klokka er ${time}. Butikken er stengt.`;
      }
    }
  </script>
```

Les `if`-linjen høyt: «Hvis time er **minst 10 OG** time er **mindre enn 20** ...». Butikken er bare åpen når **begge** delene er sanne. Det er derfor vi bruker `&&`.

- Vi skriver `time < stenger` og ikke `time <= stenger`, fordi butikken er **stengt** når klokka er 20.
- `apner` og `stenger` står utenfor funksjonen. Da er det lett å endre åpningstidene senere.

**Forutsi:** Fyll ut tabellen før du tester. Skriv *sant* eller *usant*. Den første raden er gjort for deg.

| Klokka er | `time >= 10` | `time < 20` | Åpen? |
| --- | --- | --- | --- |
| `14` | sant | sant | Ja |
| `8` |  |  |  |
| `20` |  |  |  |
| `23` |  |  |  |

Test siden med tallene i tabellen. Stemte det du skrev?

**Undersøk:** Bytt `&&` med `||` i `if`-linjen, og test med `3` og `23`. Hva skjer? Hvorfor? Bytt tilbake etterpå.

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### Steg 4 – Klokkeslett som ikke finnes (`||`)

Prøv å skrive `30` eller `-5`. Siden sier at butikken er stengt – men klokka kan jo ikke være 30! Endre `if`-en slik at den ser sånn ut:

```javascript
      if (time < 0 || time > 23) {
        txtSvar.textContent = `${time} er ikke et klokkeslett!`;
      } else if (time >= apner && time < stenger) {
        txtSvar.textContent = `Klokka er ${time}. Butikken er åpen!`;
      } else {
        txtSvar.textContent = `Klokka er ${time}. Butikken er stengt.`;
      }
```

Her bruker vi `||`, fordi det **holder at én av delene er sann**. Et tall er feil hvis det er for lite **eller** for stort. Det kan ikke være begge deler samtidig.

> **Huskeregel:**
>
> - **Innenfor** to grenser → `&&`: `time >= 10 && time < 20`
> - **Utenfor** to grenser → `||`: `time < 0 || time > 23`

**Forutsi:** Hva står det på siden?

| Du skriver | Hva står på siden? |
| --- | --- |
| `-3` |  |
| `30` |  |
| `15` |  |
| `0` |  |

### Oppgaver til Er butikken åpen?

**★ 1. Nye åpningstider.** Butikken skal nå være åpen fra kl. 9 til kl. 21. Gjør endringen, og husk å oppdatere teksten i HTML-en også. Hvorfor var det lurt å bruke variablene `apner` og `stenger`?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**★ 2. Når åpner dere?** Når butikken er stengt, skal det stå når den åpner igjen, for eksempel «Stengt. Vi åpner igjen kl. 10.» Bruk variabelen `apner` i teksten med `${ }`, slik at teksten blir riktig selv om åpningstidene endres.

**★ 3. Snart stengt!** Når klokka er 19 (én time før stengetid), skal det stå «Åpent – men vi stenger snart!». Lag en ny `else if`. Hint: `time == stenger - 1`. Tenk over **hvor** i `if`-kjeden den nye delen må stå. Hva skjer hvis du setter den etter «åpen»-delen?

**★★ 4. Nattkiosken.** Ved siden av butikken ligger en kiosk som er åpen om natta, fra kl. 22 til kl. 6. Lag et nytt avsnitt `<p id="txtKiosk"></p>`, og vis om kiosken er åpen når du trykker «Sjekk».
Tenk først: Kan klokka være **både** 22 eller mer **og** mindre enn 6 samtidig? Hvilket tegn må du da bruke?

| Klokka er | Butikken | Kiosken |
| --- | --- | --- |
| `23` |  |  |
| `3` |  |  |
| `12` |  |  |

**★★ 5. Helgeåpent.** Legg til et nytt input-felt `inpDag` der du skriver hvilken dag det er (1 = mandag, 7 = søndag). Nye åpningstider:

| Dag | Åpent |
| --- | --- |
| Mandag–fredag (1–5) | kl. 10–20 |
| Lørdag (6) | kl. 10–16 |
| Søndag (7) | stengt |

Hint: Et uttrykk kan ha mer enn to deler: `dag <= 5 && time >= 10 && time < 20`. Alle delene må være sanne. Test minst én gang for hver dagtype.

<!-- side -->

## Eksempel 2: Berg-og-dalbanen «Lynet»

<div class="side-by-side">
<div>

Fornøyelsesparken har en ny berg-og-dalbane. Du skriver høyde, alder og om en voksen er med. Siden svarer om du får kjøre.

**Reglene:**

1. Du må være minst 120 cm høy.
2. Du må være minst 10 år – men er du yngre, får du kjøre hvis en voksen er med.

Lag filen `berg-og-dalbane.html`.

</div>
<div>

```text
+------------------------------------------+
|        Berg-og-dalbanen «Lynet»          |
|                                          |
|  Høyde (cm):                [ 135 ]      |
|  Alder:                     [  8  ]      |
|  Er en voksen med? (ja/nei) [ ja  ]      |
|                                          |
|            [Får jeg kjøre?]              |
|    Ja! Spenn fast beltet og god tur!     |
+------------------------------------------+
```

</div>
</div>

### Steg 1 – Skjelettet og CSS-en

Lag skjelettet med `!` og Tab, og endre `<title>` til `Berg-og-dalbanen`. Kopier hele `<style>`-elementet fra `butikk.html`. Du trenger samme CSS.

### Steg 2 – HTML-en

```html
  <h1>Berg-og-dalbanen «Lynet»</h1>
  <p>Du må være minst 120 cm høy og minst 10 år.<br>
     Er du under 10 år, må du ha med en voksen.</p>

  <label for="inpHoyde">Høyde (cm):</label><br>
  <input type="number" id="inpHoyde"><br>

  <label for="inpAlder">Alder:</label><br>
  <input type="number" id="inpAlder"><br>

  <label for="inpVoksen">Er en voksen med? (ja/nei)</label><br>
  <input type="text" id="inpVoksen"><br><br>

  <button onclick="sjekk()">Får jeg kjøre?</button>
  <p id="txtSvar"></p>
```

Legg merke til at `inpVoksen` har `type="text"`. Der skriver du et ord, ikke et tall.

### Steg 3 – Høyde OG alder

Skriv `<script>`-blokken rett over `</body>`:

```html
  <script>
    function sjekk() {
      let hoyde = Number(inpHoyde.value);
      let alder = Number(inpAlder.value);
      let voksen = inpVoksen.value;

      if (hoyde >= 120 && alder >= 10) {
        txtSvar.textContent = "Ja! Spenn fast beltet og god tur!";
      } else {
        txtSvar.textContent = "Beklager, du får ikke kjøre.";
      }
    }
  </script>
```

- `hoyde` og `alder` er tall, så de hentes med `Number()`.
- `voksen` er tekst (`"ja"` eller `"nei"`), så den hentes **uten** `Number()`.

Test med høyde `135`, alder `12`. Test så med høyde `135`, alder `8` og `ja` i voksen-feltet. Barnet har med seg en voksen, men får likevel ikke kjøre. Det skal vi fikse!

### Steg 4 – Vi prøver å legge til voksen

Vi prøver først det enkleste: Vi legger til «ELLER en voksen er med» på slutten. Endre `if`-linjen til:

```javascript
      if (hoyde >= 120 && alder >= 10 || voksen == "ja") {
```

**Forutsi:** Hvem får kjøre nå? Fyll ut siste kolonne, og test etterpå.

| Høyde | Alder | Voksen med? | Burde få kjøre? | Får kjøre? |
| --- | --- | --- | --- | --- |
| `135` | `12` | `nei` | Ja |  |
| `135` | `8` | `ja` | Ja |  |
| `95` | `4` | `ja` | **Nei!** |  |

Den lille fireåringen på 95 cm slipper inn! Hvorfor?

**Forklaring:** JavaScript regner ut `&&` **før** `||`, akkurat som du regner ut ganging før pluss i matte. Datamaskinen leser derfor linjen slik:

> **(** høyde minst 120 **OG** alder minst 10 **)** **ELLER** voksen er med

Med denne regelen får **alle** som har med seg en voksen, kjøre – uansett hvor små de er.

### Steg 5 – Parenteser redder dagen

I matte skriver du `2 * (3 + 4)` når du vil regne ut plusset først. Vi gjør det samme her. Endre `if`-linjen til:

```javascript
      if (hoyde >= 120 && (alder >= 10 || voksen == "ja")) {
```

Les den høyt: «Hvis høyden er minst 120, **OG** (alderen er minst 10 **ELLER** en voksen er med) ...»

Test de tre personene i tabellen over på nytt. Får nå alle riktig svar?

> **Regel:** Når du blander `&&` og `||` i samme `if`, bruker du **alltid** parenteser. Da ser både du og datamaskinen hva som hører sammen.

### Steg 6 – Fortell hvorfor

«Beklager, du får ikke kjøre» er ikke et godt svar. Er du for lav, eller mangler du en voksen? Bytt ut hele `if`/`else`-en med dette:

```javascript
      if (hoyde < 120) {
        txtSvar.textContent = "Beklager, du er for lav. Du må være minst 120 cm.";
      } else if (alder >= 10 || voksen == "ja") {
        txtSvar.textContent = "Ja! Spenn fast beltet og god tur!";
      } else {
        txtSvar.textContent = "Du er under 10 år. Du må ha med en voksen.";
      }
```

**Undersøk:** I `else if`-linjen sjekker vi ikke høyden. Hvorfor trenger vi ikke det her?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### Oppgaver til Berg-og-dalbanen

**★ 1. Høydekrav i en variabel.** Lag `let minHoyde = 120;` utenfor funksjonen. Bruk variabelen både i `if`-en og i teksten «Du må være minst ... cm». Endre så kravet til 130 cm, og test.

**★ 2. For høy!** Setene passer ikke for folk som er over 195 cm. Lag en ny `else if` rett etter «for lav»-delen, med teksten «Beklager, du er for høy for setene.»
Prøv så å samle «for lav» og «for høy» i **én** `if` med `||` og teksten «Du har feil høyde for Lynet.» Hvilken løsning liker du best? Hvorfor?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**★★ 3. «Ja», «JA» eller «ja»?** Test med høyde `130`, alder `7` og `Ja` med stor J. Barnet blir avvist! Fiks programmet slik at `ja`, `Ja` og `JA` alle blir godtatt.
Hint: Du må skrive `voksen ==` tre ganger. Og husk parentesene!

**★★ 4. Billettpris.** Når du får kjøre, skal det også stå hva turen koster i et nytt avsnitt `<p id="txtPris"></p>`. Barn under 10 år og pensjonister fra 67 år betaler 50 kr. Alle andre betaler 90 kr. Lag variabler for prisene utenfor funksjonen.

| Alder | Pris |
| --- | --- |
| `8` |  |
| `30` |  |
| `67` |  |

**★★★ 5. Vognen er full.** Vognen har bare 12 plasser. Lag variabelen `let antall = 0;` utenfor funksjonen, og øk den med `++` hver gang noen får kjøre. Når 12 personer har fått kjøre, skal det stå «Vognen er full! Vent til neste tur.», og ingen flere skal få plass.
Lag også en knapp «Neste tur» som setter `antall` tilbake til 0. Vis hele tiden hvor mange ledige plasser det er.
Tenk over: Skal du sjekke om vognen er full **før** eller **etter** at du sjekker høyden?

<!-- side -->

## Lag selv – uten kodehjelp

Nå får du ingen ferdig kode. Se på eksemplene i heftet, og planlegg før du koder. Fyll ut **Hent – Regn – Vis** for hver oppgave:

- Hent: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
- Regn: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
- Vis: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## Oppgave A ★ Fri frakt

En nettbutikk gir fri frakt hvis du handler for **minst 500 kr**, **eller** hvis du er **medlem**. Alle andre betaler 79 kr i frakt. Lag filen `oppgave-a-frakt.html`.

```text
+--------------------------------------------------+
|                   Nettbutikken                   |
|  Handlet for (kr):           [ 350 ]             |
|  Er du medlem? (ja/nei)      [ nei ]             |
|                [Regn ut]                         |
|  Frakt: 79 kr. Totalt å betale: 429 kr.          |
+--------------------------------------------------+
```

**Krav – kryss av når du er ferdig**

- [ ] Siden har ett input-felt for sum og ett for medlem.
- [ ] Knappen «Regn ut» kjører en funksjon.
- [ ] Du får fri frakt hvis summen er minst 500 kr **eller** du er medlem.
- [ ] Siden viser frakten og totalprisen.
- [ ] Fraktprisen (79) og grensen (500) ligger i variabler.

| Sum | Medlem? | Frakt | Totalt |
| --- | --- | --- | --- |
| `650` | `nei` |  |  |
| `200` | `ja` |  |  |
| `499` | `nei` |  |  |
| `500` | `nei` |  |  |

**Ekstra:** Står summen mellom 400 og 499 kr, skal det også stå hvor mye mer du må handle for å få fri frakt.

<!-- side -->

## Oppgave B ★★ Karakterkalkulator

Læreren har rettet en prøve med 100 poeng. Du skriver poengene, og siden viser karakteren. Lag filen `oppgave-b-karakter.html`.

```text
+--------------------------------------------------+
|                Karakterkalkulator                |
|  Antall poeng (0–100):  [ 73 ]  [Finn karakter]  |
|              73 poeng gir karakter 4             |
+--------------------------------------------------+
```

| Poeng | Karakter |
| --- | --- |
| 0–19 | 1 |
| 20–39 | 2 |
| 40–59 | 3 |
| 60–79 | 4 |
| 80–89 | 5 |
| 90–100 | 6 |

**Krav – kryss av når du er ferdig**

- [ ] Du skriver poengene i et input-felt og trykker på en knapp.
- [ ] Siden viser riktig karakter.
- [ ] Hver karakter sjekkes med `&&` og **både** nedre og øvre grense. Et eksempel med ord: «poeng er minst 40 OG poeng er mindre enn 60».
- [ ] Poeng under 0 eller over 100 gir meldingen «Ugyldig poengsum». Bruk `||`.

**Test grensene!** Feil skjer oftest akkurat på grensen.

| Poeng | Karakter | Poeng | Karakter |
| --- | --- | --- | --- |
| `0` |  | `79` |  |
| `19` |  | `80` |  |
| `20` |  | `90` |  |
| `59` |  | `100` |  |
| `60` |  | `101` |  |

**Ekstra**

- Får du 5 eller 6, skal det også stå «Kjempebra!».
- Lag et input-felt for maks poeng, slik at prøven kan ha for eksempel 50 eller 80 poeng. Hint: Regn om til prosent først.

<!-- side -->

## Oppgave C ★★★ Terningspillet «Dobbel»

Du kaster **to** terninger per kast og får poeng etter tabellen. Du har 10 kast på deg til å samle 15 poeng. Lag filen `oppgave-c-dobbel.html`.

```text
+--------------------------------------------------+
|                Terningspillet Dobbel             |
|                     [Kast!]                      |
|          Du kastet 4 og 4. Par! +3 poeng         |
|          Poeng: 9        Kast igjen: 4           |
|                   [Nytt spill]                   |
+--------------------------------------------------+
```

| Du kaster | Poeng |
| --- | --- |
| To seksere | 5 |
| To like (par) | 3 |
| Summen er 7 **eller** 11 | 1 |
| Alt annet | 0 |

**Krav – kryss av når du er ferdig**

- [ ] Knappen «Kast!» lager to tilfeldige tall fra 1 til 6.
- [ ] Siden viser begge terningene og hvor mange poeng kastet gav.
- [ ] Siden viser hele tiden totalt antall poeng og hvor mange kast du har igjen.
- [ ] Når du har 15 poeng eller mer, står det «Du vant!».
- [ ] Har du brukt opp alle 10 kastene **og** har under 15 poeng, står det «Du tapte!».
- [ ] Når spillet er ferdig, skal det ikke gå an å kaste mer.
- [ ] Knappen «Nytt spill» nullstiller alt.

**Tips (uten kode)**

- Hvilke variabler må huskes mellom hvert kast? Hvor må de stå?
- Rekkefølgen i `if`-kjeden betyr noe: To seksere er **også** et par!
- Spillet er ferdig hvis du har nådd 15 poeng **eller** har brukt alle kastene.

**Test smart.** Bruk jukselinjer rett etter kastene, for eksempel at begge terningene blir 6. Fyll ut tabellen, og slett jukselinjene etterpå.

| Terning 1 | Terning 2 | Poeng |
| --- | --- | --- |
| `6` | `6` |  |
| `4` | `4` |  |
| `3` | `4` |  |
| `5` | `6` |  |
| `1` | `2` |  |

**Ekstra**

- Vis terningsymboler i stedet for tall: ⚀ ⚁ ⚂ ⚃ ⚄ ⚅.
- Husk rekorden: Hvor få kast trengte du for å vinne?

**Husk:** `&&` = **begge** må være sanne. `||` = **minst én** må være sann. Blander du dem, bruker du parenteser. Og test etter hvert steg!