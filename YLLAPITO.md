# Ylläpito-ohje — Oma Opetuslupa -materiaalit (julkinen repo)

Tämä on **julkinen** materiaalirepo. Sovellus lataa täältä tuntien mediaa
(podcastit, slidet) ja julkista dataa. **Kuka tahansa voi ladata sisällön.**

## Mitä TÄNNE saa lisätä

- **Audio:** `tunti-NN/podcast.mp3` tai `tunti-NN/podcast.m4a`
- **Slidet:** `tunti-NN/slidet.pdf` tai `tunti-NN/slidet.docx`
- **Julkinen data:** uutiset / FAQ ym. sovelluksen lukemat JSON-tiedostot
- **Launch-sivusto:** `docs/` (GitHub Pages)

Sovellus näyttää vain tiedostot joiden **koko > 0**. Tyhjä (0-tavuinen)
paikanvaraaja piilotetaan automaattisesti — voit jättää placeholderin kunnes
oikea tiedosto on valmis.

## Mitä TÄNNE EI SAA lisätä

- ❌ **Oppituntien MD-teksti** (`tunti-NN/README.md`, `quiz.md` tms.) — ne kuuluvat
  vain yksityiseen `ajolupa`-repoon ja niputetaan sovellukseen buildissa.
- ❌ **Mikä tahansa muu markdown** paitsi sallitut (ks. alla). CI kaataa pushin.
- ❌ **PRO-/maksullinen media.** Tämä repo on julkinen → älä laita tänne mitään,
  minkä pitää olla vain maksaneiden saatavilla. PRO-sisältö pysyy yksityisessä.
- ❌ Sovelluskoodi, arkkitehtuuri, markkinointistrategia, hinnoittelu.

## Markdown-portti (CI)

Workflow `.github/workflows/esta-md-oppitunnit.yml` estää MD-oppituntien
päätymisen tänne: jokainen push/PR kaatuu, jos repossa on `.md`-tiedosto joka ei
ole sallittujen listalla. Sallitut tällä hetkellä:

- `docs/README.md` (launch-sivuston README)
- `YLLAPITO.md` (tämä ohje)

Jos aidosti tarvitset uuden ei-oppituntimarkdownin, lisää sen polku workflown
`ALLOW`-listaan — harkiten.

## Isot mediatiedostot (Git LFS)

Suuret audiotiedostot (esim. `.m4a`) ovat Git LFS -seurannassa (`.gitattributes`).
Varmista että LFS on asennettu ennen kuin lisäät ison tiedoston:

```sh
git lfs install
git add tunti-01/podcast.m4a
git commit -m "tunti-01: lisää podcast"
git push
```

## Kirjoitusoikeus

Sisällöntuottajille annetaan kirjoitusoikeus **vain tähän repoon** — ei
yksityiseen `ajolupa`-repoon. Näin media päivittyy näkemättä koodia tai
oppituntien tekstiä.
