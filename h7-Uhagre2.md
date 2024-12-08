## [h7](https://terokarvinen.com/application-hacking/#:~:text=githubissa%20olevaa%20koodia.-,h7,-Uhagre2) Uhagre2

"Monet heikkoudet salauksessa ovat aivan tavallisia ohjelmointivirheitä. Siksi voimme murtaa salakirjoituksia ilman matematiikan tutkintoa. Mukana kaksi suosikkiani: Schneier on suosikkioppikirjani salakirjoituksesta, ja Cryptopals on suosikkiharjoitukseni salausten murtamisesta."

#### x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

- € Schneier 2015: Applied Cryptography, 20ed: [Chapter 1: Foundations](https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/08_chap01.html#chap01-sec001):

1.1 Terminology ("Historical Terms" loppuun)
```
  - plaintext = viestin sisältö
  - ciphertext = salattu viesti
  - encryption = viestin salaaminen (encipher)
  - decryption = salauksen purku (decipher)
  - cryptography, cryptographer = viestien salaamisen tekniikka ja niiden harjoittaja
  - cryptanalysis, cryptanalyst = viestien purkutekniikka ja sen harjoittaja
  - cryptology, cryptologist = matematiikan haara ja matemaatikko, joka tarkastelee molempia ylempiä kategorioita
  - authentication = vastaanottajan tulisi pystyä varmentamaan viestin alkuperä
  - integrity = vastaanottajan tulisi pystyä varmistamaan, ettei viestin sisältö ole muuttunut lähetyksen jälkeen
  - nonrepudiation = lähettäjän ei pitäisi pystyä kieltämään lähettäneensä viestin
  - cryptographic algorithm, cipher = matemaattinen funktio, jota käytetään viestin salaukseen ja purkuun
  - key = salauksessa voidaan käyttää avainta, ja tarvitaan spesifisti juuri se avain jolla salaus on tehty
  - public-key algorithms = avainpari, jossa cipher avain voi olla julkisesti nähtävissä
```
- algoritmit:
  - stream, viestin salaus bitti tai tavu kerrallaan
  - block, viestin salaus blokki kerrallaan, esim nykytietokoneiden 64-bit
- hyökkäyksiä:
  - Ciphertext-only attack
  - Known-plaintext attack
  - Chosen-plaintext attack
  - Adaptive-chosen-plaintext attack
  - Chosen-ciphertext attack
  - Chosen-key attack
  - Rubber-hose cryptanalysis
- hyökkäyksen suorittamisen verrannollinen haasteellisuus:
  - Data complexity = kuinka paljon dataa pitää syöttää
  - Processing complexity = kuinka paljon aikaa tarvitaan
  - Storage requirements = kuinka paljon muistia tarvitaan
- CODE ja CIPHER ero:
  - koodikieli on spesifien asioiden korvaaminen toisella esim. "haluan omenan" omena=päärynä
  - koodin käyttä on hyvinkin spesifiä ja hyödyllistä vain siihen tarkoitetuissa tilanteissa
  - cipherit ovat hyödyllisiä ja käytettäviä mihin tahansa vain


1.4 Simple XOR
- XOR = exclusive-or operation
- hyvin huono turvallisuus
- datan XOR:aus tuottaa salatun tekstin, mutta tämä cipher XOR:attuna uudestaan tuottaa plaintextin XOR luonteen takia
- vaikka XOR salauksessa käyttää avainta, sen murtaminen on nykytietokoneilla erittäin nopeaa
  - Index of Coincidence


1.7 Large Numbers
- cryptografiassa ilmeisesti pyöritellään massiivisia lukuja, sillä Large Numbers kappaleessa listalla on mm:
  - Todennäköisyys kuolla salamaniskuun (per päivä) = 1 : 9 000 000 000 (2^33)
  - Todennäköisyys voittaa pääpotti lotossa (yhdysvallat) = 1 : 4 000 000 (2^22)
  - Todennäköisyys, että molemmat yllä olevat tapahtuvat sinulle samana päivänä = 1 : 2^55


- Karvinen 2024: [Python Basics for Hackers](https://terokarvinen.com/python-for-hackers/)


- Vapaaehtoinen: Karvinen 2024: [Get Started Micro Editor](https://terokarvinen.com/get-started-micro-editor/)
- Vapaaehtoinen: Karvinen 2024: [Getting Started with Cryptopals using Python](https://terokarvinen.com/getting-started-python-cryptopals/)
  - Mutta ei tietenkään niitä "click to expand" alle piilotettuja vinkkejä, niitä kannattaa katsoa vain tarvittaessa. Osa ei tarvitse niitä ollenkaan.


#### Ratkaise [CryptoPals Set 1](https://cryptopals.com/sets/1) -haasteet. Tehtävät saa ratkaista millä vain ohjelmointikielellä ja käyttää mitä tahansa tekstieditoria tai IDE:ä. Tehtäviä ei kannata ratkaista tekoälyllä, koska se vain kopioi malliratkaisun suoraan koulutusmateriaalistaan.

- a) 1. Convert hex to base64.
- b) 2. Fixed XOR.
- c) 3. Single-byte XOR cipher.
- d) 4. Detect single-character XOR.
  - Tämän tehtävän ratkaiseminen yleensä ilahduttaa.

- e) Vapaaehtoinen, suositeltava: 5. Implement repeating-key XOR.
- g) Vapaaehtoinen: 6. Break repeating-key XOR.
- h) Vapaaehtoinen: 7. AES in ECB mode.
- i) Vapaaehtoinen: 8. Detect AES in ECB mode.

---
## Lähteet:
- 
