# Flexbox – elevhefte

Oct 14, 2026 · @Mufasa

## Slik bruker du heftet

I dette heftet lærer du flexbox ved å skrive koden selv. Du bygger fire små nettsider steg for steg, og til slutt løser du to oppgaver på egen hånd.

**Før du begynner**

1. Lag en ny mappe som heter `flexbox`.
2. Lag en ny fil i mappen for hver øvelse, for eksempel `ovelse1.html`.
3. Skriv av startkoden nøyaktig. Ikke kopier – du lærer mer av å skrive selv.
4. Lagre filen (Ctrl+S) og åpne den i nettleseren.
5. For hvert steg: skriv inn den nye koden, lagre, og oppdater nettleseren (F5).
6. Skriv ned hva som skjer i tabellene og på svarlinjene.

**Det viktigste å huske**

Flexbox har alltid en **forelder** og **barn**. Forelderen er boksen rundt. Barna er elementene rett inni. Du skriver `display: flex;` på **forelderen**, og da bestemmer forelderen hvor barna skal stå.

```html
<div class="beholder">      <!-- forelder -->
  <div class="boks">1</div>  <!-- barn -->
  <div class="boks">2</div>  <!-- barn -->
  <div class="boks">3</div>  <!-- barn -->
</div>
```

**Tips:** Den stiplede rammen i øvelsene viser hvor forelderen er. Den har ingenting med flexbox å gjøre, men gjør det lettere å se hva som skjer.

## Øvelse 1: Boksene på rad

I denne øvelsen lærer du `display: flex`, `justify-content` og `gap`. Du får tre bokser til å stå på rad og flytter dem bortover.

**Steg 1 – Skriv av startkoden.** Lag filen `ovelse1.html`.

```html
<!DOCTYPE html>
<html lang="no">
<head>
  <meta charset="UTF-8">
  <title>Øvelse 1</title>
  <style>
    .beholder {
      border: 2px dashed black;
    }
    .boks {
      width: 80px;
      padding: 20px;
      background: lightblue;
      border: 1px solid black;
    }
  </style>
</head>
<body>
  <div class="beholder">
    <div class="boks">1</div>
    <div class="boks">2</div>
    <div class="boks">3</div>
  </div>
</body>
</html>
```

Lagre og åpne filen i nettleseren. Hvordan står boksene?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 2 – Slå på flexbox.** Skriv inn denne linjen i `.beholder`, under `border`:

```css
    display: flex;
```

Lagre og oppdater. Hva skjedde med boksene?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 3 – Flytt boksene bortover.** Legg til denne linjen i `.beholder`:

```css
    justify-content: center;
```

Bytt ut `center` med verdiene i tabellen én etter én. Lagre og oppdater hver gang, og skriv hva som skjer.

| Verdi | Hva skjer med boksene? |
| --- | --- |
| `flex-start` |  |
| `center` |  |
| `flex-end` |  |
| `space-between` |  |
| `space-around` |  |
| `space-evenly` |  |

**Steg 4 – Mellomrom mellom boksene.** Sett `justify-content` tilbake til `flex-start`. Legg til:

```css
    gap: 20px;
```

Prøv også `5px` og `60px`. Hva gjør `gap`?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 5 – Utvid koden.**

1. Legg til boks 4 og boks 5 i HTML-en.
2. Gi boksene ulike farger. Legg til en ny klasse, for eksempel `<div class="boks rosa">4</div>`, og lag regelen `.rosa { background: pink; }` i CSS-en.
3. Endre `width: 80px` til `width: 200px` i `.boks`. Hva skjer når boksene ikke får plass?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 6 – Utforsk.** Flytt `display: flex;` fra `.beholder` til `.boks`. Hva skjer? Hvorfor?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## Øvelse 2: Opp, ned og i kolonne

I denne øvelsen lærer du `align-items` og `flex-direction`. Forelderen er nå 300px høy, så boksene har plass til å flytte seg opp og ned. Boksene er også ulikt høye, så du ser tydelig hva som skjer.

**Steg 1 – Skriv av startkoden.** Lag filen `ovelse2.html`.

```html
<!DOCTYPE html>
<html lang="no">
<head>
  <meta charset="UTF-8">
  <title>Øvelse 2</title>
  <style>
    .beholder {
      border: 2px dashed black;
      height: 300px;
      display: flex;
      gap: 10px;
    }
    .boks {
      width: 80px;
      padding: 20px;
      background: lightblue;
      border: 1px solid black;
    }
  </style>
</head>
<body>
  <div class="beholder">
    <div class="boks">1</div>
    <div class="boks">2<br>2</div>
    <div class="boks">3<br>3<br>3</div>
  </div>
</body>
</html>
```

Lagre og åpne filen. Boksene er like høye som beholderen, selv om de har ulikt innhold. Det er fordi `align-items: stretch` er standard.

**Steg 2 – Flytt boksene opp og ned.** Legg til denne linjen i `.beholder`:

```css
    align-items: center;
```

Prøv verdiene i tabellen og skriv hva som skjer.

| Verdi | Hva skjer med boksene? |
| --- | --- |
| `flex-start` |  |
| `center` |  |
| `flex-end` |  |
| `stretch` |  |

**Steg 3 – Perfekt sentrering.** Sett `align-items` til `center` og legg til:

```css
    justify-content: center;
```

Nå står alle boksene midt i beholderen, både bortover og nedover.

**Steg 4 – Bytt retning.** Legg til:

```css
    flex-direction: column;
```

Hvordan står boksene nå?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 5 – Hvem styrer hva?** Med `flex-direction: column` bytter `justify-content` og `align-items` jobb. Test begge retningene og fyll ut tabellen med «bortover» eller «opp og ned».

|  | `flex-direction: row` | `flex-direction: column` |
| --- | --- | --- |
| `justify-content` flytter boksene |  |  |
| `align-items` flytter boksene |  |  |

**Steg 6 – Utvid koden.**

1. Behold `flex-direction: column`. Sett `justify-content: space-between;`. Hva skjer?
2. Prøv `flex-direction: row-reverse;` og `flex-direction: column-reverse;`. Hva gjør `-reverse`?
3. Legg til boks 4 og 5. Endre `height` i `.beholder` til `150px` mens du har `column`. Hva skjer?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## Øvelse 3: Meny og søkefelt

I denne øvelsen bruker du flexbox på noe ekte: en meny øverst på en nettside. Du lærer også at et element kan være forelder og barn samtidig, og at `flex: 1` fyller ledig plass.

**Steg 1 – Skriv av startkoden.** Lag filen `ovelse3.html`.

```html
<!DOCTYPE html>
<html lang="no">
<head>
  <meta charset="UTF-8">
  <title>Øvelse 3</title>
  <style>
    header {
      background: #333;
      color: white;
      padding: 10px;
    }
    a {
      color: white;
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">Min side</div>
    <ul class="meny">
      <li><a href="#">Hjem</a></li>
      <li><a href="#">Bilder</a></li>
      <li><a href="#">Kontakt</a></li>
    </ul>
  </header>
</body>
</html>
```

Lagre og åpne filen. Ligner dette på en meny?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 2 – Menypunktene på rad.** Her er `<ul>` forelderen, og `<li>` er barna. Legg til en ny regel i CSS-en:

```css
    .meny {
      display: flex;
      gap: 20px;
      list-style: none;
      padding: 0;
    }
```

Hva gjør `list-style: none;`? Prøv å fjerne den.

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 3 – Logo og meny ved siden av hverandre.** Nå skal `<header>` også bli en forelder. Barna er logoen og menyen. Legg til i `header`:

```css
      display: flex;
```

**Steg 4 – Logo til venstre, meny til høyre.** Legg til i `header`:

```css
      justify-content: space-between;
      align-items: center;
```

Hvorfor trenger vi `align-items: center;` her? Prøv å fjerne den og sammenlign.

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 5 – Et søkefelt.** Skriv denne HTML-en under `</header>`:

```html
  <div class="sok">
    <input type="text" placeholder="Søk ...">
    <button>Søk</button>
  </div>
```

Og denne CSS-en:

```css
    .sok {
      display: flex;
      gap: 10px;
      margin-top: 20px;
    }
    .sok input {
      flex: 1;
    }
```

Hva gjør `flex: 1;` med søkefeltet? Prøv å fjerne linjen.

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 6 – Utvid og utforsk.**

1. Legg til to nye menypunkter.
2. Bytt `space-between` i `header` til `center`, deretter til `space-around`.
3. Endre knappeteksten til «Søk på hele nettstedet». Hva skjer med søkefeltet?
4. Gi også knappen `flex: 1;`. Hva skjer? Prøv så `flex: 3;` på input og `flex: 1;` på knappen.
5. Gjør nettleservinduet smalt og bredt. Hva skjer med søkefeltet?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## Øvelse 4: Kort og galleri

I denne øvelsen lager du kort, slik du ser på nettbutikker og nyhetssider. Du lærer å gjøre kortene like høye, å sette knappen nederst, og å la kortene gå over flere linjer med `flex-wrap`.

**Steg 1 – Skriv av startkoden.** Lag filen `ovelse4.html`.

```html
<!DOCTYPE html>
<html lang="no">
<head>
  <meta charset="UTF-8">
  <title>Øvelse 4</title>
  <style>
    .kort {
      border: 1px solid black;
      padding: 10px;
    }
  </style>
</head>
<body>
  <div class="kortrad">
    <div class="kort">
      <h3>Katt</h3>
      <p>Liker å sove.</p>
      <button>Les mer</button>
    </div>
    <div class="kort">
      <h3>Hund</h3>
      <p>Liker å gå tur, leke med ball og hilse på alle den møter.</p>
      <button>Les mer</button>
    </div>
    <div class="kort">
      <h3>Kanin</h3>
      <p>Liker gulrøtter.</p>
      <button>Les mer</button>
    </div>
  </div>
</body>
</html>
```

Lagre og åpne filen. Hvordan står kortene?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 2 – Kortene på rad.** Legg til en regel for forelderen:

```css
    .kortrad {
      display: flex;
      gap: 10px;
    }
```

Se på høyden til kortene. Hva legger du merke til?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 3 – Like brede kort.** Legg til i `.kort`:

```css
      flex: 1;
```

Hva skjedde med bredden?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 4 – Knappen nederst.** Knappene står i ulik høyde. For å fikse det gjør vi hvert kort til en forelder, med barna under hverandre. Legg til i `.kort`:

```css
      display: flex;
      flex-direction: column;
```

Lag så en ny regel for knappen:

```css
    .kort button {
      margin-top: auto;
    }
```

`margin-top: auto` betyr «ta all ledig plass over meg». Hvor havner knappene nå?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 5 – Mange kort.** Skriv tre nye kort i `.kortrad`: Hamster, Papegøye og Gullfisk. Hva skjer når det blir seks kort på én rad?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Steg 6 – Galleri som brytes.** Legg til i `.kortrad`:

```css
      flex-wrap: wrap;
```

Endre `flex: 1;` i `.kort` til:

```css
      flex: 1 1 200px;
```

Det betyr: start på 200px, bli bredere hvis det er plass, og smalere hvis det trengs. Gjør nettleservinduet smalt og bredt. Fyll ut tabellen.

| Vindusbredde | Antall kort per rad |
| --- | --- |
| Helt bredt |  |
| Halvt |  |
| Smalt som en mobil |  |

**Steg 7 – Utforsk.**

1. Endre `200px` til `300px`. Hva skjer?
2. Endre `flex: 1 1 200px;` til `flex: 0 1 200px;`. Hva gjør det første tallet?
3. Slett `margin-top: auto;`. Hva skjer med knappene?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

## Oppgave A: Profilkort

Lag et profilkort om deg selv som står midt på siden. Nå får du ingen ferdig kode – du bestemmer selv hvordan du løser det. Lag filen `oppgave-a.html`.

**Slik skal det se ut**

```text
+--------------------------------------------------+
|                                                  |
|         +------------------------------+         |
|         |             ( )              |         |
|         |                              |         |
|         |         Ola Nordmann         |         |
|         |          Elev i 9B           |         |
|         |                              |         |
|         | [Spill]  [Musikk]  [Fotball] |         |
|         +------------------------------+         |
|                                                  |
+--------------------------------------------------+
```

**Krav – kryss av når du er ferdig**

- [ ] Kortet står midt på siden, både bortover og nedover.
- [ ] Bildet, navnet og teksten står under hverandre og er midtstilt i kortet.
- [ ] Det er tre knapper med hobbyene dine på rad, med mellomrom mellom.
- [ ] Kortet har en ramme og litt luft inni (`border` og `padding`).

**Hjelp til å komme i gang**

- Lag en forelder rundt kortet, for eksempel `<div class="side">`. Gi den `height: 100vh;` så den blir like høy som nettleservinduet.
- Bildet kan være en farget sirkel. Bruk denne koden:

```css
    .bilde {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      background: orange;
    }
```

- Du trenger tre flexbokser: én for siden, én for kortet og én for knappene.
- Se tilbake på øvelse 2 (sentrering og `flex-direction`) og øvelse 3 (meny på rad).

**Ekstra utfordring**

- Lag to profilkort ved siden av hverandre, midt på siden.
- Bytt den oransje sirkelen med et ekte bilde: `<img src="bilde.jpg" class="bilde">`.

## Oppgave B: Min egen nettside

Lag en liten nettside om et tema du liker, for eksempel en hobby, favorittdyr eller et fotballag. Siden skal ha en header, en samling kort og en footer. Lag filen `oppgave-b.html`.

**Slik skal det se ut**

```text
+--------------------------------------------------+
| LOGO                       Hjem   Om   Kontakt   |
+--------------------------------------------------+
|  +------------+  +------------+  +------------+  |
|  | Kort 1     |  | Kort 2     |  | Kort 3     |  |
|  | Tekst ...  |  | Tekst ...  |  | Tekst ...  |  |
|  |            |  | ...        |  |            |  |
|  | [Les mer]  |  | [Les mer]  |  | [Les mer]  |  |
|  +------------+  +------------+  +------------+  |
|  +------------+                                  |
|  | Kort 4     |                                  |
|  +------------+                                  |
+--------------------------------------------------+
| (c) 2026 Ditt navn             Laget med flexbox |
+--------------------------------------------------+
```

**Krav – kryss av når du er ferdig**

- [ ] Headeren har logoen til venstre og menyen til høyre, på linje i høyden.
- [ ] Menypunktene står på rad med mellomrom, uten kulepunkter.
- [ ] Det er minst fire kort med ulik mengde tekst.
- [ ] Kortene er like høye, og knappen står nederst i alle kortene.
- [ ] Kortene går over på en ny linje når nettleservinduet blir smalt.
- [ ] Footeren har én tekst til venstre og én til høyre.

**Hjelp til å komme i gang**

Du kan bruke denne strukturen som start:

```html
<body>
  <header>
    <!-- logo og meny -->
  </header>

  <main class="galleri">
    <!-- kortene -->
  </main>

  <footer>
    <!-- to tekster -->
  </footer>
</body>
```

- Headeren løser du som i øvelse 3.
- Kortene løser du som i øvelse 4.
- Footeren ligner på headeren. Hvilken `justify-content` trenger du?

**Ekstra utfordring**

- Når det er lite innhold, havner footeren midt på siden. Få den til å alltid stå nederst. Hint: `<body>` kan også være en flexbox med `flex-direction: column;` og `min-height: 100vh;`. Hva skjer om du gir `main` `flex: 1;`?
- Legg til et søkefelt under headeren som fyller hele bredden.

## Huskeliste

De fleste flex-egenskapene skrives på forelderen. Bare `flex` og `margin-top: auto` skrives på barna.

| Egenskap | Skrives på | Hva den gjør |
| --- | --- | --- |
| `display: flex` | forelder | Gjør elementet til en flexbox. Barna legger seg på rad. |
| `justify-content` | forelder | Plasserer barna langs raden: `flex-start`, `center`, `flex-end`, `space-between`, `space-around`, `space-evenly`. |
| `align-items` | forelder | Plasserer barna på tvers av raden: `flex-start`, `center`, `flex-end`, `stretch`. |
| `gap` | forelder | Mellomrom mellom barna. |
| `flex-direction` | forelder | Retningen: `row` (rad), `column` (kolonne), `row-reverse`, `column-reverse`. |
| `flex-wrap: wrap` | forelder | Barna får gå over flere linjer. |
| `flex: 1` | barn | Barnet tar all ledig plass. |
| `flex: 1 1 200px` | barn | Start på 200px, voks og krymp ved behov. |
| `margin-top: auto` | barn | Skyver barnet så langt ned som mulig. |

**Husk:** Med `flex-direction: column` bytter `justify-content` og `align-items` jobb.
