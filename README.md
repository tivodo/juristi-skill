# Suomalaisen lainsäädännön ja lakikielen skill-tiedosto tekoälylle

**Opeta tekoäly työskentelemään suomalaisen lainsäädännön ja juridisten dokumenttien kanssa.** Tämä skill-tiedosto antaa tekoälylle kattavat ohjeet säädösten rakenteesta, pykäläviittausten oikeasta muodosta, lakikielen kirjoitussäännöistä, sopimusten laatimisesta ja oikeuslähteiden käytöstä.

Toimii Claude Coden, Codexin ja minkä tahansa muun skillejä tukevan tekoälyagentin kanssa.

---

## Miksi tekoäly tarvitsee tätä skilliä?

Tekoäly tekee juridisessa suomen kielessä systemaattisia virheitä, jotka vaikuttavat lopputuloksen uskottavuuteen ja oikeellisuuteen:

- **Pykäläviittaukset väärin**: "pykälässä 2" eikä *2 §:ssä*, taivutusmuodot pielessä, säädösnumerot puuttuvat
- **Yhdyssanat erikseen**: "oikeus turva" eikä *oikeusturva*, "hallinto päätös" eikä *hallintopäätös*
- **Lakikielen tyyli pielessä**: mahtipontista amerikkalaista lakiretoriikkaa suomalaisen asiatyylin sijaan
- **Rakenne hakusessa**: pykälien, momenttien ja kohtien hierarkia sekaisin, johdantokappaleiden ja kohtien virkerakenne rikki
- **Viittaukset epätarkkoja**: kumottuihin lakeihin viittaaminen, säädösnumeroiden puuttuminen, oikeuskäytännön tunnusmuodot väärin

Tämä skill ei tee tekoälystä täydellistä, mutta se auttaa ehkäisemään näitä virheet ja ohjaa tekoälyn tuottamaan ammattitasoista juridista tekstiä tekoälyn parhailla kyvykkyyksillä.

## Asennusohjeet – ks. vaihtoehdot 4–5 jos et ole tekninen ihminen

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

### Vaihtoehto 4: Asenna tekoälyllä

Anna tekoälylle (Claude Code, Codex tai muu skillejä tukeva agentti) tämän repon osoite ja pyydä sitä asentamaan skill:

```
Asenna tämä skill: https://github.com/akunikkola/juristi-skill
```

### Vaihtoehto 5: Lataa .skill-tiedosto

Lataa valmis skill-paketti ja lisää se suoraan Claudeen:

[Lataa juristi.skill (Google Drive)](https://drive.google.com/file/d/1RIkvqLBgoaOLUV3LXtX8o2SGaWYeM2jy/view?usp=sharing)

Lisää ladattu tiedosto Claudeen raahaamalla se Claude Code -ikkunaan tai tuomalla se skillinä asetuksista.

## Mitä juristi-skill kattaa?

| Osa-alue | Referenssitiedosto | Sisältö |
|---|---|---|
| Säädösten rakenne | `references/rakenne.md` | Säädöshierarkia, pykälien numerointi, momentit, luvut ja otsikot |
| Pykäläviittaukset | `references/viittaukset.md` | Viittausten oikea muoto, taivutus, pykälävälit, a-pykälät, säädösnumerot |
| Lakikieli | `references/lakikieli.md` | 3-3-3-sääntö, numerot, välimerkit, lyhenteet, passiivi ja aktiivi |
| Sopimukset | `references/sopimukset.md` | Sopimusrakenne, osapuolten yksilöinti, esimerkkiklausuulit |
| Lähteet | `references/lahteet.md` | Finlex, oikeuskäytäntö, hallituksen esitykset, viittausmuodot |
| Suomen kieli | `references/suomen-kieli.md` | Yhdyssanat, pilkutus, alkukirjaimet, anglismit ja tyyli juridisessa kontekstissa |

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

- [Finlex](https://finlex.fi/) – Suomen valtion virallinen säädöstietopankki (viitattu 19.6.2026)
- [Kielitoimiston ohjepankki](https://kielitoimistonohjepankki.fi/) – suomen kielen kirjoitusohjeet (viitattu 19.6.2026)
- [Lainkirjoittajan opas](http://lainkirjoittaja.finlex.fi/) – oikeusministeriön ohjeistus säädösten laatimiseen (viitattu 19.6.2026)
- Hallituksen esitysten laatimisohjeet (HELO)

## Lisenssi

MIT
