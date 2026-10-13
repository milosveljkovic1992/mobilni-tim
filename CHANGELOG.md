# Izmene

Sve značajne izmene igre Mobilni tim beleže se u ovom fajlu. Brojevi verzija prate pravila opisana u odeljku „Verzionisanje“ u README.md.

## [Neobjavljeno]

### Dodato
- Link „← Sve igre“ iznad zaglavlja, ka krovnoj aplikaciji Izborni dan (https://izborni-dan.netlify.app/).
- Ikonica u tabu pregledača (favicon): ruta obilaska, ugrađena u `index.html` kao SVG.
- Slika za deljenje na društvenim mrežama (`og-image.png`, 1200 × 630) i Open Graph i Twitter meta tagovi.

### Promenjeno
- Naslov za deljenje (`og:title`, `twitter:title`): „Mobilni tim – znaš li kada da reaguješ?“.
- Slika za deljenje se u `og:image` i `twitter:image` navodi punom adresom (https://mobilni-tim.netlify.app/og-image.png), a dodat je i `og:url`.
- Meta opis stranice: „Sa kolegom obilaziš devet biračkih mesta. Kroz 21 situaciju, od plana obilaska do izveštaja, odluči šta da proveriš, zabeležiš i javiš.“

### Ispravljeno
- Slovna greška u situaciji sa kombijima ispred biračkog mesta 1: „prozivka“ umesto „proziva“.

## [1.0.0] - 2026-10-13

### Dodato
- Igra sa 21 situacijom tokom izbornog dana, iz uloge člana mobilnog tima posmatrača, od plana obilaska do završnog izveštaja.
- Tri merača: bezbednost tima, proverene informacije i nepristrasnost.
- Lokacija tima u zaglavlju koja se menja sa svakom situacijom.
- Objašnjenje i pravilo posle svake odluke, izveštaj tima i ocena na kraju igre.
- Mešanje redosleda opcija u svakoj partiji.
- Podešavanja za objavu na Netlify (`netlify.toml`) sa bezbednosnim zaglavljima.
- Oznaka verzije u `<meta name="version">`.
