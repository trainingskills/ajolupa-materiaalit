# Oma Opetuslupa — launch-sivusto

Staattinen, riippuvuudeton launch-sivusto (yksi sivu). Kaikki assetit ovat mukana — ei CDN:iä, ei build-vaihetta. Toimii avaamalla `index.html` selaimessa.

## Rakenne
```
website/
├── index.html        # koko sivu (semantic HTML, FI)
├── styles.css        # design system (peilaa app/src/App.css tokenit) + light/dark + responsive
├── script.js         # teema-toggle, mobiilivalikko, scroll-reveal
├── robots.txt        # hakukonebotit + sitemap-osoite
├── sitemap.xml       # sivuston indeksointikartta
├── humans.txt        # tekijatiedot ihmisille ja boteille
├── ai-context.json   # tiivistetty LLM-konteksti sisallosta
├── README.md
└── assets/
    ├── logo.svg      # brändimerkki (ratti + reitti)
    └── og-image.svg  # Open Graph / some-jakokuva (1200×630)
```

## Esikatselu paikallisesti
```bash
# mikä tahansa staattinen palvelin, esim:
npx serve website
# tai
python3 -m http.server -d website 8080
```
Avaa sitten `http://localhost:8080`.

## Ominaisuudet
- **Light/dark** — kunnioittaa järjestelmän teemaa + manuaalinen toggle (muistetaan `localStorage`).
- **Responsiivinen** — mobiili → työpöytä; hero, bento-ruudukko ja footer mukautuvat.
- **Saavutettava** — skip-linkki, `focus-visible`, aria-tilat toggleissa/valikossa, `prefers-reduced-motion`, kontrasti AA.
- **Nopea** — ei ulkoisia fontteja/skriptejä; inline-SVG-ikonit.
- **SEO/OG** — kuvaus, Open Graph + Twitter card, `og-image.svg`.

## Sisältö ankkuroitu
Kaikki tekstit ja väitteet on johdettu markkinoinnin totuuden lähteestä
[`../marketing/messaging-positioning.md`](../marketing/messaging-positioning.md) ja tuotefaktoista
[`../shared_intent.md`](../shared_intent.md). "Tulossa"-ominaisuudet on merkitty rehellisesti.

## Jonotuslista
Sivulla on yksi yhteinen `mailto`-jonotuslista kaikille alustoille.
- Osoite: `oma.opetuslupa.4h@gmail.com`
- CTA avaa valmiin sähköpostipohjan ja lisää käyttäjän jonotuslistalle viestin perusteella.

## LLM + SEO -signaalit
- `robots.txt` + `sitemap.xml` hakuroboteille
- JSON-LD (`LearningResource`, `FAQPage`, `Organization`) suoraan `index.html`-headissa
- `ai-context.json` nopeaksi konekontekstiksi
- `humans.txt` ylläpitotiedot luotettavuussignaaliksi
- sivulla näkyvä "Päivitetty viimeksi" -merkintä

## Julkaisu (deploy)
Vedä `website/`-kansio mihin tahansa staattiseen hostiin:
- **Netlify / Cloudflare Pages / Vercel:** publish directory = `website`, ei build-komentoa.
- **GitHub Pages:** julkaise `website/`-alihakemisto tai kopioi juureen.

## Ennen tuotantoon vientiä (TODO)
- [x] Yhteyssahkoposti on yhtenaistetty: `oma.opetuslupa.4h@gmail.com` (CTA + footer).
- [x] Yksi yhteinen jonotuslista `mailto`-CTA:lla (ei iOS/Android-erottelua).
- [x] LLM-löydettävyys: robots, sitemap, JSON-LD, ai-context, humans.
- [ ] (Valinnainen) renderöi `og-image.svg` PNG:ksi laajimman some-yhteensopivuuden vuoksi.
