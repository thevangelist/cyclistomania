# Cyclistomania

Yhden tiedoston, selaimessa pyörivä **Across / Elasto Mania** -henkinen
fysiikkapeli. Fysiikan hoitaa [Matter.js](https://brm.io/matter-js/), piirto on
käsin canvasilla (kamera, zoom, parallaksi). Ei buildiä, ei riippuvuuksia.

## Pelaa

Avaa `index.html` selaimessa (vaatii nettiyhteyden Matter.js-CDN:ää varten):

```sh
open index.html        # macOS
```

## Kontrollit

Elasto Mania -tyyliset kontrollit, mutta eteenpäin **poljetaan hiiren rullalla**.
Jokainen rullan naksahdus on yksi poljinveto (kammet ja jalat pyörivät tahdissa,
kuuluu naksahdus). Mitä nopeammin rullaat, sitä kovempaa polje. Pyörässä on
**vapaaratas**: poljin vain kiihdyttää — pitkä ja vauhdikas rullaus antaa vauhtia
jolla pyörä rullaa vapaasti useita sekunteja.

| Ohjain | Toiminto |
|---|---|
| 🖱️ Hiiren rulla | Polje (eteenpäin liike) |
| `↓` | Jarru |
| `←` `→` | Pyöritä runkoa / pyörää ilmassa |
| `Space` | Suunnanvaihto |
| `R` | Alusta taso |
| `M` | Äänet päälle/pois |

Kräsy tulee **vain kuskin pään osumisesta maahan** — runko ja renkaat saavat
hipoa maata vapaasti. Pääset maaliin (ruutulippu) kun pidät pään pystyssä.
Paras aika tallentuu selaimen `localStorage`iin.

## Radan osiot

Rata vaihtelee tunnelmasta toiseen pehmein siirtymin: tasainen **kaupunki** →
sileä **maantie** → karheampi **gravel** → kumpuileva **metsä** → jyrkkä
**haastava** mäkiosuus → maantie → maali. Jokaisella osiolla on oma pinta
(asfaltti / sora / multapolku / kallio) ja tienvarsikoristeet — liikennemerkkejä
(nopeusrajoitus, STOP, varoituskolmiot, hirvivaroitus), liikennevaloja,
lamppuja, puita ja kiviä. Osiot määritellään `ZONES`-taulukossa tiedoston alussa.

## Säätö

Tuntumaan vaikuttavat arvot ovat `index.html`-tiedoston alun `CFG`-objektissa:

- `pedalKick` — yhden rullaveton sysäys (poljennan napakkuus)
- `pedalMax` — huippunopeus polkien
- `airDrag` — ilmanvastus; **pienennä jos haluat pidemmän vapaan rullauksen**
- `crankRate` — poljinkampien pyörimisnopeus (visuaali)
- `brake`, `lean`, `suspStiff`, `suspDamp`, `gravity`, `seg` (maaston tarkkuus)

Radan osiot ja niiden karheus määritellään `ZONES`-taulukossa (`hill` = loivat
kukkulat, `low` = keskimuodot, `rough`/`rf` = pinnan karheus ja sen taajuus).
