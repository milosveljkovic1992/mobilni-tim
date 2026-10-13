# Mobilni tim

Tekstualna igra u kojoj si član mobilnog tima organizacije koja posmatra izbore u Srbiji. Sa kolegom obilaziš devet biračkih mesta u izmišljenoj opštini, proveravaš prijave i sve javljaš koordinacionom centru. Kroz izborni dan, od plana obilaska u 06:15 do završnog izveštaja u 23:00, rešavaš 21 situaciju.

Posle svake odluke igra pokazuje da li je odluka ispravna, delimično ispravna ili pogrešna, zašto je tako i koje pravilo važi.

Igra je deo serije sa igrama Kontrolor (član biračkog odbora) i Posmatrač (stalni posmatrač na biračkom mestu).

## Kako se igra

- Svaka situacija ima četiri opcije. Izabrana opcija se „zaokruži“ kao na glasačkom listiću.
- Tri merača prate rad tima: **bezbednost tima**, **proverene informacije** i **nepristrasnost**.
- Zaglavlje pokazuje vreme i gde se tim trenutno nalazi.
- Na kraju dobijaš izveštaj tima sa svim odlukama, brojem ispravnih odluka i ocenom.
- Redosled opcija se meša u svakoj partiji.

Situacije obuhvataju, između ostalog: plan obilaska, kašnjenje sa otvaranjem biračkog mesta, proveru prijava, evidentiranje birača ispred biračkog mesta, odbijanje ulaska, kratku posetu po obrascu, udaljenog stalnog posmatrača, organizovani prevoz birača, pretnje timu, medije, dezinformacije, nepristrasnost unutar tima, iskaz birača o kupovini glasa, koordinaciju sa centrom, „bugarski voz“ viđen spolja, nestanak struje tokom brojanja, predaju materijala i završni izveštaj.

## Struktura projekta

```
index.html     cela aplikacija (HTML, CSS i JavaScript u jednom fajlu)
og-image.png   slika za deljenje na društvenim mrežama (1200 × 630)
netlify.toml   podešavanja za Netlify (objava i bezbednosna zaglavlja)
CHANGELOG.md   spisak izmena po verzijama
README.md      ovaj fajl
```

Nema zavisnosti ni build koraka. Jedini spoljni resursi su fontovi sa Google Fonts (Bitter, Source Serif 4, IBM Plex Mono).

## Lokalno pokretanje

Otvori `index.html` direktno u pregledaču, ili pokreni lokalni server:

```sh
python3 -m http.server 8000
```

pa otvori http://localhost:8000.

## Objava na Netlify

**Preko Git repozitorijuma (preporučeno)**

1. Postavi projekat na GitHub, GitLab ili Bitbucket.
2. Na Netlify izaberi **Add new site → Import an existing project** i poveži repozitorijum.
3. Build command ostavi prazno, a publish directory je `.`. Ova podešavanja se čitaju iz `netlify.toml`.
4. Pokreni **Deploy**. Svaki novi push na glavnu granu automatski objavljuje novu verziju.

Ako je projekat podfolder većeg repozitorijuma, u podešavanjima sajta na Netlify postavi **Base directory** na putanju do ovog foldera.

**Preko Netlify CLI**

```sh
npm install -g netlify-cli
netlify login
netlify deploy          # probna objava
netlify deploy --prod   # produkcija
```

**Bez naloga za Git:** prevuci folder projekta na https://app.netlify.com/drop.

## Izmena sadržaja

Sve situacije su u nizu `S` unutar `<script>` bloka u `index.html`. Svaka situacija ima ovaj oblik:

```js
{ t: "08:20",                       // vreme na satu
  loc: "BM 5 · Dom kulture",        // lokacija tima u zaglavlju
  title: "Čovek sa spiskom",
  text: "Opis situacije…",
  opts: [
    { x: "Tekst opcije", v: "ok" },                 // ok | part | bad
    { x: "Tekst opcije", v: "bad", f: "Kratko objašnjenje zašto",
      fx: [-8, -10, -8] },                          // opciono: promena merača
    …
  ],
  why: "Pravilo koje se prikazuje posle odgovora." }
```

Ako opcija nema `fx`, koriste se podrazumevane promene merača iz objekta `DEF` (redom: bezbednost tima, proverene informacije, nepristrasnost). Ocene na kraju igre zavise od broja bodova i definisane su u funkciji `renderEnd`.

## Verzionisanje

Trenutna verzija je upisana na jednom mestu, u `index.html`:

```html
<meta name="version" content="1.0.0">
```

Broj verzije ima oblik `GLAVNI.SPOREDNI.ISPRAVKA`:

| Izmena | Primer | Nova verzija |
|---|---|---|
| Ispravka teksta, pravila ili greške u kodu | pogrešan broj telefona u objašnjenju | 1.0.0 → 1.0.1 |
| Nove ili izmenjene situacije, nova funkcija | dodata situacija o praćenju vozila sa materijalom | 1.0.1 → 1.1.0 |
| Veća promena igre ili usklađivanje sa novim pravilima | igra za lokalne izbore, novi sistem bodovanja | 1.1.0 → 2.0.0 |

Postupak za novu verziju:

1. Promeni `content` u `<meta name="version">`.
2. U `CHANGELOG.md` premesti stavke iz „Neobjavljeno“ pod novi naslov sa brojem verzije i datumom.
3. Napravi commit i Git tag, pa pošalji oba:

```sh
git commit -am "Verzija 1.0.1"
git tag -a v1.0.1 -m "Verzija 1.0.1"
git push && git push --tags
```

## Napomena o tačnosti

Igra je edukativna simulacija sa izmišljenim mestima i situacijama. Pravila su pojednostavljena prema Zakonu o izboru narodnih poslanika, uputstvima Republičke izborne komisije i uobičajenim pravilima ponašanja organizacija koje posmatraju izbore. Nisu pravni savet. Većina pravila za mobilne timove (trajanje posete, javljanje centru, postupanje pri pretnjama, izjave medijima) dolazi iz prakse organizacija i razlikuje se od jedne do druge. Pravo mobilnih timova da uđu na biračko mesto treba proveriti u važećem zakonu i uputstvu RIK. Pre korišćenja igre na obukama uskladi pravila sa uputstvom svoje organizacije.
