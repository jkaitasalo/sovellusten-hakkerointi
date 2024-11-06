## h2 Break & unbreak

Nyt hakkeroidaan! Ja koodataan!
Opit etsimään ja korjaamaan haavoittuvuuksia.
Muista systemaattinen työtapa ja raportoi tehdessä. Kannattaa myös reflektoida: Missä tämä haava voisi olla yleinen? Miten tämän virheen voisi välttää? Mitä tästä opin?

---
#### x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

- OWASP: OWASP Top 10: [A01 Broken Access Control](https://owasp.org/Top10/A01_2021-Broken_Access_Control/)
  - Pääsyvalvonnan heikko toteutuminen mahdollistaa pahantahtoisten toimijoiden pääsyn tietoon, sen muokkaamiseen ja tuhoamiseen ilman oikeaa valtuutusta.
  - Yleisiä heikkouksia on mm:
    - admin oikeuksien käytön, ilman varsinaisia oikeuksia
    - sisällön katsomisen/muokkaamisen ilman asiaankuuluvia oikeuksia, tai yksilöllisen tunnisteen kanssa
    - autentikoiduille sivuille pääsy ilman autentikointia
  - Pääsynvalvonta toimii parhaiten, kun hyökkääjä ei pysty muuttamaan itse pääsynvalvonnan tarkistuksia. Hyviä käytänteitä:
    - Estää verkkopalvelimen hakemistolistaus, estää herkät tiedostot julkisilta alueilta, lokittaa pääsynhallinnan epäonnistumiset ja rajoittaa API-kutsuja.
    - Session tunnisteet tulee mitätöidä kirjautumisen jälkeen.
    - Lyhytikäisten JWT-tokenien käyttö on suositeltavaa

- Karvinen 2023: [Find Hidden Web Directories - Fuzz URLs with ffuf](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/)
  - Verkkohakemistoissa on usein "salaisia" endpointeja (esim. /admin, /salaisuus)
  - FUFF on verkko fuzzer, joka "fuzzaa" piilotettuja hakemistoja ja jopa muita osia (headerit, POST parametrit yms.) verkkosivuilta
  - FUFF kanssa voi käyttää hyväksi sanalistaa, jolla voi etukäteen määritettyjä esim. yleisiä hakemistoja hakea todella nopeasti
  - filttereillä voidaan sulkea tuloksista ulos yleisimmät vastaukset ja keskittyä poikkeamiin. Esimerkkejä filttereistä:
    - `-fs`  size
    - `-fc`  status
    - `-fw`  words
    - `-fl`  lines
    - `-ft`  duration (ms)

- PortSwigger: [Access control vulnerabilities and privilege escalation](https://portswigger.net/web-security/access-control)
  - Pääsynvalvonta koostuu kolmesta osasta:
    - Authentication (autentikaatio) varmistaa käyttäjän olevan kuka se väittää olevan
    - Session management (sessionhallinta) tunnistaa, että autentikaatiota seuraavat pyynnöt ovat samalta käyttäjältä
    - Access control (pääsynvalvonta) varmistaa onko käyttäjällä ylipäätään pääsy/oikeudet osaan sivustoa/toimintoja
  - Virhe tai bugi pääsynvalvonnassa on kriittinen vaara verkkosivuston/ohjelmiston turvallisuudelle
  - Vertical access controls (vertikaaliset pääsyvalvonnan kontrollit)
    - pääosin käyttäjäpohjaiset kontrollit
    - esim Admin ja perus käyttäjän oikeudet ovat todella eri
  - Horizontal access controls (horisontaaliset pääsyvalvonnan kontrollit)
    - käyttäjillä on samantasoiset oikeudet resurssiin mutta eri osaan siitä
    - esimerkiksi käyttäjällä on pääsy ja oikeus siirtää omalta tililtään rahaa, mutta ei muiden käyttäjien tileiltä
  - Context-dependent access controls (kontekstiriippuvaiset pääsyvalvonnan kontrollit)
    - säätää käyttäjän oikeuksia riippuen siitä minkä vaiheen kanssa käyttäjä on tekemisissä applikaatiossa
    - esimerkiksi käyttäjä ei voi muuttaa ostoskorin sisältöä maksun jälkeen
  - Pääsynvalvonnan heikko eheys luo vaaroja ja haavoittuvuksia, joita mahdollinen hyökkääjä pystyy hyväksikäyttämään
  - horisontaalinen ja vertikaalinen pääsynvalvonta ja sen eheys on tärkeää, sillä niiden välillä on mahdollista joissain tapauksissa siirtyä

- Karvinen 2006: [Raportin kirjoittaminen](https://terokarvinen.com/2006/raportin-kirjoittaminen-4/)
  - Raportoinnin rakenne on tärkeää, jotta se on:
    - Toistettava
      - vain raportin ohjeiden mukaisesti joku muu päätyy samoihin tuloksiin
    - Täsmällinen
      - mikä komento?
      - mitä klikattu?
      - kellonajat?
      - onnistuiko?
      - eri viat?
      - menneen aikamuodon käyttö
    - Helppolukuinen
      - otsikointi
      - kielioppi
      - kanavaan sopiva kieliasu
      - tiivistelmä plussaa
    - Viittaa lähteisiin
      - yleisesti hyvä tapa ja akateeminen käytäntö vaatii sitä
  - Pahoja mokia:
    - selittely / valehtelu
    - plagiointi
    - kuvien luvaton käyttö (tekijänoikeudet)

- Vapaaehtoinen: PortSwigger 2020: [What is SQL injection? - Web Security Academy](https://www.youtube.com/watch?v=wX6tszfgYp4) (noin 10 min video)

---
---
palautus keskeneräisenä ja myöhässä

---
---
#### a) Murtaudu 010-staff-only. Ks. Karvinen 2024: [Hack'n Fix](https://terokarvinen.com/hack-n-fix/)
- Latasin Teron haasteympäristön [teros_challenges.zip](https://terokarvinen.com/hack-n-fix/)
  - Jotta ympäristön sai pyörimään piti minun asentaa:
    - python3 flask `sudo apt-get install python3-flask`
    - ja python3 flask sqlalchemy `sudo apt-get install python3-flask-sqlalchemy`
- Tämän jälkeen käynnistin ympäristön `010-staff-only/staff-only.py`

![image](https://github.com/user-attachments/assets/9332d1a8-02c1-4c27-9114-de278ab807c1)

- Syötin kenttään 123, jolloin ohjelma antoi osoiteriville päätteen `?pin=123` ja näytti sivulla salasanani `Somedude`

![image](https://github.com/user-attachments/assets/7fc0ef01-9f6e-42e8-bcd2-84e8f053726d)

- Tämän jälkeen yritin kirjoittaa SQL injektiota suoraan tekstikenttään, mutta kenttä suostui vastaanottamaan vain numeroita. Sivun lähdekoodia tutkimalla Firefoxin inspect-työkalulla löysin kentän kohdan koodista ja muutin input-kentän tyypin "number" -> "text", joka mahdollistaa ei-numeroiden syöttämisen ja lähettämisen.

![image](https://github.com/user-attachments/assets/0ab5baf8-423f-4988-9cb2-6da1154a97b7)

- Komennolla `' OR 1=1; --` ohjelma palautti salasanan `foo`

![image](https://github.com/user-attachments/assets/0c009ead-5889-4dac-a938-2a04a00e977a)

- Jonkun aikaa materiaaleja pläräiltyäni löysin W3Schoolsista `LIMIT` komennon SQL:ään. Komennon pitäisi tulostaa annettuun arvoon asti taulukosta rivejä, mutta sivusto ei anna kuin yhden vastauksen.
- Päätin pyytää ChatGPT:tä selittämään komennon käyttöä paremmin. Sain vastauksena pitkän listan eri käyttötapauksia, joista yksi osui silmääni, joka vaikutti tapauksen ratkomiseen sopivalta.

![image](https://github.com/user-attachments/assets/45ce362b-f4b6-4200-8533-85448d34d0d9)

- Tällä selityksellä, lähdin kokeilemaan eri arvopareja ja lopulta osuinkin oikean kohdalle komennolla: <br> `'OR 1=1 LIMIT 2,1; --`

![image](https://github.com/user-attachments/assets/428ec360-7553-446c-8147-3bd1a013d6dc)



#### b) Korjaa 010-staff-only haavoittuvuus lähdekoodista. Osoita testillä, että ratkaisusi toimii.


#### c) Ratkaise dirfuzt-1 artikkelista Karvinen 2023: [Find Hidden Web Directories - Fuzz URLs with ffuf.](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/) Tämä auttaa 020-your-eyes-only ratkaisemisessa.
- Ensitöikseni asensin virtuaalikoneeseen [fuff](https://github.com/ffuf/ffuf/releases):n uusimman version Linuxin Amd64 arkkitehtuurille (ffuf_2.1.0_linux_amd64)
- Tämän jälkeen latasin itselleni kopion [Daniel Miesslerin](https://raw.githubusercontent.com/danielmiessler/SecLists/master/Discovery/Web-Content/common.txt) sanalistasta `common.txt`, joka sisältää "yleisimmät" hakemistot
- Seuraavaksi latasin haaste-binäärin dirfuzt-1 [terokarvinen.com:sta](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/) (sivun lopussa) `wget`:llä
- Tämän jälkeen kasaus ja käynnistys komennoilla `chmod u+x dirfuzt-1` ja `./dirfuzt-1`, jolloin kohde lähti pyörimään:

![image](https://github.com/user-attachments/assets/9a8636e3-9d2f-4ebd-9dee-2de88d116eb6)

- Annoin ffuf:lla komennon `./ffuf -w common.txt -u http://127.0.0.2:8000/FUZZ`
  - `-w common.txt` -w parametri antaa sanalistan, tässä tapauksessa `common.txt`, jota ajetaan asetettua FUZZ avainsanan paikkaa vastaan
  - `-u` parametri antaa kohdeosoitteen, jossa `FUZZ` antaa paikan osoiterivillä, johon ajetaan sanalistaa
  
![image](https://github.com/user-attachments/assets/59631a5c-5d76-423d-b424-c596cc4ec082)

- Tällä komennolla ffuf ajoi koko sanalistan läpi, eli n. 4700 sanaa ja ruutu täyttyikin tuloksista, joista suurin osa oli koon 154 omaavia osumia
- Koetin uudestaan antamalla lisäparametrinä filtterin `-fs 154`, joka filtteröi koon perusteella kaikki koot 154 pois.

![image](https://github.com/user-attachments/assets/7c90e091-ca83-4c6f-9098-6bb4d270db33)

- Tällä haulla löytyi muutama osuma ja päätin navigoida osoiteriviltä `http://127.0.0.2:8000/wp-admin`, ja ruudulle ilmestyikin lippu!
  - Osoitteeseen olisi toki voinut kurkata komennolla `curl http://127.0.0.2:8000/wp-admin`
  - `wp-admin` löytyi yksi lippu ja toinen lippu löytyi `.git` alkuisista hakemistoista


#### d) Murtaudu 020-your-eyes-only. Ks. Karvinen 2024: [Hack'n Fix](https://terokarvinen.com/hack-n-fix/)


#### e) Korjaa 020-your-eyes-only haavoittuvuus. Osoita testillä, että ratkaisusi toimii.

---
#### g) Vapaaehtoinen. Johdantotehtävä, joka auttaa 010-staff-only ratkaisemisessa. Ratkaise Portswigger Academyn "Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data".

#### h) Vapaaehtoinen. Johdantotehtävä, joka auttaa 010-staff-only ratkaisemisessa. Ratkaise Portswigger Academyn "Lab: SQL injection vulnerability allowing login bypass"
