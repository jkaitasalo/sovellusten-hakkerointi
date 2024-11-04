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
  - filttereillä voidaan sulkea tuloksista ulos yleisimmät vastaukset ja keskittyä poikkeamiin
  - esimerkkejä filttereistä:
    - `-fs`  size
    - `-fc`  status
    - `-fw`  words
    - `-fl`  lines
    - `-ft`  duration (ms)

- PortSwigger: [Access control vulnerabilities and privilege escalation](https://portswigger.net/web-security/access-control)
- Karvinen 2006: [Raportin kirjoittaminen](https://terokarvinen.com/2006/raportin-kirjoittaminen-4/)
- Vapaaehtoinen: PortSwigger 2020: [What is SQL injection? - Web Security Academy](https://www.youtube.com/watch?v=wX6tszfgYp4) (noin 10 min video)


#### a) Murtaudu 010-staff-only. Ks. Karvinen 2024: [Hack'n Fix](https://terokarvinen.com/hack-n-fix/)


#### b) Korjaa 010-staff-only haavoittuvuus lähdekoodista. Osoita testillä, että ratkaisusi toimii.


#### c) Ratkaise dirfuzt-1 artikkelista Karvinen 2023: [Find Hidden Web Directories - Fuzz URLs with ffuf.](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/) Tämä auttaa 020-your-eyes-only ratkaisemisessa.


#### d) Murtaudu 020-your-eyes-only. Ks. Karvinen 2024: [Hack'n Fix](https://terokarvinen.com/hack-n-fix/)


#### e) Korjaa 020-your-eyes-only haavoittuvuus. Osoita testillä, että ratkaisusi toimii.

---
#### g) Vapaaehtoinen. Johdantotehtävä, joka auttaa 010-staff-only ratkaisemisessa. Ratkaise Portswigger Academyn "Lab: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data".

#### h) Vapaaehtoinen. Johdantotehtävä, joka auttaa 010-staff-only ratkaisemisessa. Ratkaise Portswigger Academyn "Lab: SQL injection vulnerability allowing login bypass"
