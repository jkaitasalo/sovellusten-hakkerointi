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
  - Planeetamme ikä = 10^9 (2^30) vuotta
  - Atomien lukumäärä auringossa = 10^57 (2^190)
  - jne...



- Karvinen 2024: [Python Basics for Hackers](https://terokarvinen.com/python-for-hackers/)
- historia, ylänuolella
- tab completion, tabulaattorilla. 2x Tab -> antaa vaihtoehtoja
- ? symbolin perässä antaa "reference documentation"
- ?? antaa lähdekoodin
- 2x Ctrl+D poistuu ohjelmasta
- Micro koodieditorilla F5 compile. Nopeampaa, kuin koodin kirjoitus editorilla ja sen jälkeen valmiin koodin ajo terminaalista.
  - toimii parhaiten lyhyissä ohjelmissa
```
$ sudo apt-get update
$ sudo apt-get -y install micro
$ micro --plugin install runit
```
- Python tukee suoraan erilaisia funktioita, joten matematiikkaa on helppo tehdä sen avulla
- Modulus (jakojäännös) on yleinen obfuskaatiossa käytetty metodi `(13 % 12 = 1)`
- char 0 =/= num 0
  - ord("T") = 84
  - chr(84) = 'T'
- hex(84) = '0x54'
- bin(84) = '0b1010100'
- oct(84) = '0o124'
- f-string `print(f"See you at {var}"`
- f-string `print(f"See you at {2+2} pm"`
```
for planet in ['Mercury', 'Venus', 'Earth', 'Mars']:
print(planet)
```
Itselleni muistiin tämä:
```
>>> ord("R")
82
>>> ord("R")+1
83
>>> chr(ord("R")+1)
'S'
```
- print debugging
  - "ylimääräisten" print kutsujen käyttö, jolla voidaan seurata esim. muuttujien arvojen muuttumista ohjelman suorituksen eri vaiheissa
  - vaikeimmissa jutuissa kannattaa käyttää oikeaa debuggeria ja breakpoint() kutsua
- .split() jakaa stringin listaksi
- list(enumerate([])) antaa listan olioiden indexit
- type(esim) antaa esim tyypin esim. str
- XOR totuustaulukko:

| a   | b   | a XOR b | Comment                       |
| --- | --- | ------- | ----------------------------- |
| 0   | 0   | 0       |                               |
| 1   | 0   | 1       |                               |
| 1   | 1   | 0       | Here XOR is different from OR |
| 0   | 1   | 1       |                               |

- yleisimmät kirjaimet:
  - ETAOIN SHRDLU (englanti)
  - AINTE SLOUK (suomi)


---
- Vapaaehtoinen: Karvinen 2024: [Get Started Micro Editor](https://terokarvinen.com/get-started-micro-editor/)
- Vapaaehtoinen: Karvinen 2024: [Getting Started with Cryptopals using Python](https://terokarvinen.com/getting-started-python-cryptopals/)
  - Mutta ei tietenkään niitä "click to expand" alle piilotettuja vinkkejä, niitä kannattaa katsoa vain tarvittaessa. Osa ei tarvitse niitä ollenkaan.

---
#### Ratkaise [CryptoPals Set 1](https://cryptopals.com/sets/1) -haasteet. Tehtävät saa ratkaista millä vain ohjelmointikielellä ja käyttää mitä tahansa tekstieditoria tai IDE:ä. Tehtäviä ei kannata ratkaista tekoälyllä, koska se vain kopioi malliratkaisun suoraan koulutusmateriaalistaan.

- a) 1. Convert hex to base64.

Tehtävän "ratkaisuun" löytyi netistä nopeasti aikalailla suora vastaus:

![image](https://github.com/user-attachments/assets/08710773-162b-46ba-b0fd-13d694263617)

![image](https://github.com/user-attachments/assets/5881a97d-e4ab-4fef-b29d-d68a5e145ce5)

Tämä oli aika tylsää, mutta tuon vastauksen alta löytyi linkkejä pythonin dokumentaatioon. Tuolta sai vähän paremmin kiinni, miten tuota voi lähteä myös purkamaan.

![image](https://github.com/user-attachments/assets/d9a400db-1b29-4474-bc28-5ed41fff651f)

![image](https://github.com/user-attachments/assets/5a6893f5-7e0a-4383-815d-9bfddc738160)

Hexan takaa löytyi hassu tekstin pätkä `"I'm killing your brain like a poisonous mushroom"`

![image](https://github.com/user-attachments/assets/c7527dcc-4e89-4eb9-af59-ae6a03c1942d)

![image](https://github.com/user-attachments/assets/e49766d0-3774-4344-9649-73544af4e03e)


- b) 2. Fixed XOR.
- c) 3. Single-byte XOR cipher.
- d) 4. Detect single-character XOR.
  - Tämän tehtävän ratkaiseminen yleensä ilahduttaa.
  - 
---
- e) Vapaaehtoinen, suositeltava: 5. Implement repeating-key XOR.
- g) Vapaaehtoinen: 6. Break repeating-key XOR.
- h) Vapaaehtoinen: 7. AES in ECB mode.
- i) Vapaaehtoinen: 8. Detect AES in ECB mode.

---
## Lähteet:
- [Tero Karvinen: Python For Hackers](https://terokarvinen.com/python-for-hackers/)
- [O'Reilly](https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/08_chap01.html#chap01-sec001)
- https://docs.python.org/3/library/stdtypes.html#bytes.fromhex
- https://docs.python.org/3/library/base64.html#base64.b64encode
