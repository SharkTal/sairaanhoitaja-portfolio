# 🧠 FORLEARNING — Portfolio-Sivusto (v2: HUS Clinical Blue)

## The Big Picture: Arkkitehtuuri

Kuvittele tämä portfolio-sivusto kuin **sairaalan aula**:

- **HTML (`index.html`)** = Aulan suunnittelu. Missä on info-taulu, missä odotustila, missä ohjeet lääkäreille. Rakenne ja järjestys.
- **CSS (`style.css`)** = Sairaalan brändi. HUS:n sininen, puhtaan valkoinen tausta, luottamusta herättävät värit. Design System = brändikirja.
- **JS (`main.js`)** = Automaattiset ovet ja valaistus. Sivuston animaatiot ja navigaation logiikka.

### Tiedostorakenne
```
portfolio/
├── index.html          ← Sisältö ja rakenne
├── style.css           ← HUS Clinical Blue Design System
├── main.js             ← Animaatiot + interaktiot
└── images/
    ├── hero-bg.png     ← Hero-taustakuvan varjo (hyvin haalea)
    ├── profile-photo.jpg ← Oma kuvasi HUS-sairaala-asussa
    ├── hoitoplanner-preview.png
    └── medicineai-preview.png
```

## Technical Decisions: Miksi valittiin X eikä Y?

### 1. Miksi väri vaihdettiin tealista siniseen?
**Ennen:** `#1A5F5A` (tumma teal) + musta tausta → "Koodarin portfolio"  
**Jälkeen:** `#005A9C` (HUS-sininen) + vaalea tausta → "Sairaanhoitajan portfolio"

**Trade-off:** Menetimme "wau, hieno dark mode" -efektin. Mutta saimme **rekrytoijan luottamuksen**. Hoitotyön päällikkö ei etsi visuaalista vaikuttamista — hän etsii puhtautta, ammattimaisuutta ja turvallisuutta. Väritearäpäätös oli **strateginen, ei esteettinen**.

### 2. Miksi vaaleaa taustaa?
Katso suomalaisten terveydenhuollon sivustoja:
- **HUS.fi** → Valkoinen + sininen
- **Terveystalo.com** → Valkoinen + vihreä
- **Mehiläinen.fi** → Valkoinen + violetti

Kaikki käyttävät vaaleaa taustaa, koska terveydenhuollossa vaaleus = puhtaus = luotettavuus. Tumma teema = "hakkeri" tai "pelaaja".

### 3. Miksi "Kliininen kokemus" osio ennen projekteja?
Rekrytoija skannaa sivua 6–10 sekuntia. Jos ensimmäinen sisältö projekteina olevista on "HoitoPlanner (Vanilla JS, Firebase)", hän luulee sinun olevan IT-ammattilainen. Kun ensimmäinen sisältö on "Silmätautien päivystys — Triage ja ABCDE", hän ymmärtää heti: **tämä on hoitaja**.

### 4. Miksi painikkeet ovat erilaiset?
```
[██ Kliininen kokemus ██]  ← Sininen täytetty = TÄMÄ ON TÄRKEINTÄ
[ ⬜ Teknologiaprojektit ]  ← Sininen reunus = lisäbonus
```
Tämä on UX-periaate nimeltä **Visual Hierarchy**. Silmä menee aina ensin vahvimpaan elementtiin.

## The Struggle Log

| Ongelma | Ratkaisu | Opetus |
|---------|----------|--------|
| Kuva ei näkynyt (väärä tiedostomuoto) | Etsittiin .jpg oikeasta kansiosta | Tiedostopäätteet merkitsevät |
| Tumma nav ei toiminut vaalealla pohjalla | Muutettiin kaikki nav-värit: teksti, tausta, hamburger | Teeman vaihto = kaikki koskevat elementit |
| Footer-teksti ei näkynyt | `--text-hero-sub` oli nyt tumma → muutettiin `rgba(255,255,255,0.6)` | CSS-muuttujat periytyvät — muutokset voivat rikkoa muualla |
| Mobiilivalikko läpinäkymätön tumma | `background: rgba(255,255,255,0.98)` + `box-shadow` | Mobile nav on erillinen overlay, vaatii omat tyylit |

## The Engineer's Mindset

### 1. "Design System" -ajattelu pelasti tunteja
Koska käytimme CSS Custom Properties (`:root`-muuttujia), koko värimaailman vaihto vaati vain ~20 muuttujan muokkaamisen. Jos värit olisivat olleet kovakoodattu joka paikkaan, jouduttaisiin muokkaamaan ~200 riviä.

**Opetus:** Aina kun aloitat projektin, määritä design tokens ensin. Se on investointi tulevaisuuteen.

### 2. "Kohderyhmäajattelu" > "Henkilökohtainen maku"
Minä (kehittäjä) rakastan tummia teemoja. Mutta **kohderyhmäni** (hoitotyön esimiehet) luottavat vaaleisiin, puhtaisiin asetteluihin. Tein valinnan kohderyhmän perusteella, en oman makuni.

**Opetus:** Joka kerta kun rakennat jotain, kysy: "Kuka tätä käyttää?" — ei "Mikä on tyylikästä?"

### 3. "Kerroksellinen viestintä" — Strateginen kommunikaatio
Portfolio rakentuu kerroksina kuin hoitotyön prosessi:
1. **Arviointi** (Hero): Kuka olen? → Sairaanhoitaja + koodaaja
2. **Suunnitelma** (Kokemus): Mitä olen tehnyt? → Kolme kliinistä jaksoa
3. **Toteutus** (Projektit): Miten ratkaisin ongelmia? → HoitoPlanner + MedicineAI
4. **Arviointi** (Osaaminen + Yhteystiedot): Mitä osaan? Miten tavoitat minut?

---

## 📝 Test Your Knowledge

### 1. The "Why" — Miksi?
CSS-tiedostossa on muuttuja `--primary-glow: rgba(0, 90, 156, 0.1)`. Miksi käytetään `rgba()`-funktiota eikä suoraan HEX-väriä `#005A9C`? Mitä hyötyä läpinäkyvyydestä on?

### 2. The "What-If" — Entä jos?
Entä jos sinua pyydetään haastatteluun ja rekrytoija sanoo: "Näin portfoliosi — vaikuttava. Mutta miksi olet rakentanut sovelluksia sen sijaan, että keskittyisit 100% hoitotyöhön?" Miten vastaisit niin, että vahvistat asemaasi etkä puolustele?

### 3. The "Debug" Challenge
Navigaatiopalkki käyttää nyt `background: rgba(255, 255, 255, 0.95)` kun scrollataan. Entä jos käyttäjä on sivuston footer-osiossa (tumma tausta) ja scrollaa takaisin ylös — onko mahdollista, että nav-palkki näyttää "kelluvalta" eri tavalla vaalealla vs tummalla taustalla? Miksi/miksi ei?
