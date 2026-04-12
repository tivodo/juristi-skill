# Suomalaisen lainsäädännön ja lakikielen skill tekoälylle

**Opeta tekoäly työskentelemään suomalaisen lainsäädännön ja juridisten dokumenttien kanssa.** Tämä skill antaa tekoälylle kattavat ohjeet säädösten rakenteesta, pykäläviittausten oikeasta muodosta, lakikielen kirjoitussäännöistä, sopimusten laatimisesta ja oikeuslähteiden käytöstä.

Toimii Claude Coden, Codexin ja minkä tahansa muun skillejä tukevan tekoälyagentin kanssa.

---

## Miksi tämä on tehty

Tekoäly tekee juridisessa suomen kielessä systemaattisia virheitä:

- **Pykäläviittaukset väärin**: "pykälässä 2" eikä *2 §:ssä*, taivutusmuodot pielessä, säädösnumerot puuttuvat
- **Yhdyssanat erikseen**: "oikeus turva" eikä *oikeusturva*, "hallinto päätös" eikä *hallintopäätös*
- **Lakikielen tyyli pielessä**: mahtipontista amerikkalaista yritysretoriikkaa suomalaisen asiatyylin sijaan
- **Rakenne hakusessa**: pykälien, momenttien ja kohtien hierarkia sekaisin, johdantokappaleiden ja kohtien virkerakenne rikki
- **Viittaukset epätarkkoja**: kumottuihin lakeihin viittaaminen, säädösnumeroiden puuttuminen, oikeuskäytännön tunnusmuodot väärin

Tämä skill ehkäisee nämä virheet ja ohjaa tekoälyn tuottamaan ammattitasoista juridista tekstiä.

## Asennus

### Vaihtoehto 1: Projektitasoinen asennus (suositeltu)

```bash
# Luo skills-hakemisto, jos sitä ei ole
mkdir -p .claude/skills/juristi/references

# Kopioi skill-tiedostot
cp SKILL.md .claude/skills/juristi/SKILL.md
cp references/*.md .claude/skills/juristi/references/
```

### Vaihtoehto 2: Globaali asennus (kaikki projektit)

```bash
mkdir -p ~/.claude/skills/juristi/references
cp SKILL.md ~/.claude/skills/juristi/SKILL.md
cp references/*.md ~/.claude/skills/juristi/references/
```

### Vaihtoehto 3: Suora asennus GitHubista

```bash
# Projektitasoinen
mkdir -p .claude/skills/juristi/references && \
curl -sL https://raw.githubusercontent.com/akunikkola/juristi-skill/main/SKILL.md -o .claude/skills/juristi/SKILL.md && \
for f in lahteet lakikieli rakenne sopimukset viittaukset; do \
  curl -sL "https://raw.githubusercontent.com/akunikkola/juristi-skill/main/references/${f}.md" -o ".claude/skills/juristi/references/${f}.md"; \
done

# Globaali
mkdir -p ~/.claude/skills/juristi/references && \
curl -sL https://raw.githubusercontent.com/akunikkola/juristi-skill/main/SKILL.md -o ~/.claude/skills/juristi/SKILL.md && \
for f in lahteet lakikieli rakenne sopimukset viittaukset; do \
  curl -sL "https://raw.githubusercontent.com/akunikkola/juristi-skill/main/references/${f}.md" -o "$HOME/.claude/skills/juristi/references/${f}.md"; \
done
```

## Mitä skill kattaa

| Osa-alue | Referenssitiedosto | Sisältö |
|---|---|---|
| Säädösten rakenne | `references/rakenne.md` | Säädöshierarkia, pykälien numerointi, momentit, luvut ja otsikot |
| Pykäläviittaukset | `references/viittaukset.md` | Viittausten oikea muoto, taivutus, pykälävälit, a-pykälät, säädösnumerot |
| Lakikieli | `references/lakikieli.md` | 3-3-3-sääntö, numerot, välimerkit, lyhenteet, passiivi ja aktiivi |
| Sopimukset | `references/sopimukset.md` | Sopimusrakenne, osapuolten yksilöinti, esimerkkiklausuulit |
| Lähteet | `references/lahteet.md` | Finlex, oikeuskäytäntö, hallituksen esitykset, viittausmuodot |

Lisäksi SKILL.md sisältää ydinsäännöt ja tarkistuslistan, joka on aina käytettävissä ilman referenssitiedostoja.

## Käyttö

Skill aktivoituu automaattisesti, kun:

- Työskentelet lakien, pykälien tai säädösten kanssa
- Laadit tai tarkistat sopimuksia tai muita juridisia asiakirjoja
- Muotoilet pykäläviittauksia
- Kirjoitat tai tarkistat lakikieltä
- Haluat ymmärtää tai tulkita säädöstekstiä

Voit myös kutsua skillin manuaalisesti:

```
/juristi
```

## Lähteet

Skill perustuu seuraaviin virallisiin lähteisiin:

- [Finlex](https://finlex.fi/) — Suomen valtion virallinen säädöstietopankki
- [Kielitoimiston ohjepankki](https://kielitoimistonohjepankki.fi/) — suomen kielen kirjoitusohjeet
- [Lainkirjoittajan opas](http://lainkirjoittaja.finlex.fi/) — oikeusministeriön ohjeistus säädösten laatimiseen
- Hallituksen esitysten laatimisohjeet (HELO)

## Lisenssi

MIT
