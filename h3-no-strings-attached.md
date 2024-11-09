## h3 No strings attached

Tiesitkö, että binääreistä saa tietoa jo ennen kuin ne ajaa? Tässä astutaan ensi viikon staattisen analyysin maailmaan.

Staattisen analyysin kruunaamaton kuningas 'strings' tervehtii meitä!

---
#### a) Strings. Lataa ezbin-challenges.zip Aja 'passtr'. Selvitä oikea salasana 'strings' avulla. Selvitä myös lippu. (Ensisijaisesti katsomatta sorsia, jos osaat.)

- Latasin tehtävänannosta `ezbin-challenges.zip`. Purin tiedoston ja käyttämällä `unzip` -komentoa. Tämän jälkeen navigoin tiedoston sisälle tehtävään `challenges/passtr`.
- Keulin ja ajoin `strings passtr`, joka palautti liudan rivejä, joiden seasta bongasin rivit `What's the password?`, `sala-hakkeri-321` ja lipun:

![image](https://github.com/user-attachments/assets/ff4ed167-50af-4a5f-9977-252f9a7d70bf)

- Tämän jälkeen luin README.md tiedoston käyttämällä `cat README.md` -komentoa. Ajoin ohjelman komennolla `./passtr`, jolloin ohjelma pyysi salasanaa, jonka annettuani palautti ohjelma minulle lipun!

![image](https://github.com/user-attachments/assets/f6f59675-b2c2-4a00-b346-b6b7e2f68822)


#### b) Tee passtr.c -ohjelmasta uusi versio, jossa salasana ei näy suoraan sellaisenaan binääristä. Osoita testillä, että salasana ei näy. (Obfuskointi riittää.)

- Kysyin tekoälyltä tekniikoita, joilla on mahdollista obfuskoida C -koodia. Sain vastaukseksi todella paljon erilaisia kikkoja ja tekniikoita mm. XOR-salaus, joka salaa jokaisen merkin salasanasta asetetulla avaimella ja takaisin plaintextiksi ajon aikana, sekä Base64 Encoding/Decoding, joka ei niinkään ole varsinainen salausmenetelmä, mutta hankaloittaa salasanan lukemisen koodista.
- Lopulta päädyin käyttämään suhteellisen yksinkertaista tapaa. Käytin `micro passtr.c` ja muutin lähdekoodia seuraavanlaiseksi:

![image](https://github.com/user-attachments/assets/0947e27e-83e7-4483-9432-83b221ea9ef2)

- Tässä olen muuttanut koodia siten, että salasana on pilkottu useampaan kappaleeseen, jolloin se on vaikeampi löytää binäärin seasta.
- Tämä vaihtoehto oli sieltä helpoimmasta päästä, mutta ainakin itselleni helpoin ymmärtää ja jokseenkin osaltaan myös avasi miten nuo edistyneemmät menetelmät toimivat.


- Tämän lisäksi muutin `Makefile` tiedostoa seuraavanlaisesti: <br>`gcc -O2 -fvisibility=hidden -fno-inline -fomit-frame-pointer -s -o passtr.c`
  - `-02` säätää optimoinnin tasoa poistamalla turhia osia koodista. Mahdollisesti tekee käännetystä ohjelmasta vaikeammin ymmärrettävää.
  - `-fvisibility=hidden` piilottaa symbolit, jotka eivät ole julkisesti (export) määriteltyjä.
  - `-fno-inline` estää kääntäjän "inlining" ominaisuuden, jossa funktioiden koodi kopioidaan suoraan sen kutsukohtiin.
  - `-fomit-frame-pointer` poistaa kehyspisteen tiedot, jotka auttavat riippuvuuksien jäljittämisessä.
  - `-s` strip, poistaa kaikki ylimääräiset virheenkorjaustiedot ja symbolitaulukot.

- Näiden askelien lopputulos näytti `strings passtr` -komennon ajon jälkeen tältä:

![image](https://github.com/user-attachments/assets/355c247f-e962-4584-8fe6-4e5aba400b16)


#### c) Packd. Aja 'packd' paketista ezbin-challenges.zip. Mikä on salasana? Mikä on lippu? (Tämä tehtävä on hieman haastavampi. Kirjaa ylös kokeilemasi lähestymistavat ja keksimäsi hypoteesit. Toivottavasti pääset itse maaliin, mutta jos et, läpikävely paljastuu tunnilla...)

- Lähdin toteuttamaan tehtävää aikaisemmin tutulla `strings packd`, joka ei kuitenkaan tuottanut juurikaan selkeää tulosta.
- Tämän jälkeen ajattelin lähteä tunnilla aikaisemmin mainitun Ghidran kanssa räpeltämään, mutta ei siitäkään oikein tahtonut mitään tulla.
  - Käyttöliittymää tarkastellessani uskoakseni huomasin salasanan pyyntöön liittyvää logiikkaa, mutta se oli kaikki hyvinkin salattua:
 
![image](https://github.com/user-attachments/assets/036a2458-3970-4ce1-8b05-8a7e6cf1af94)
![image](https://github.com/user-attachments/assets/16fbcab1-676d-44f0-b40d-3ae02b54896e)


#### d) Vapaaehtoinen bonus: Cryptopals. Crypto Challenge Set 1. Tätä voi tehdä useamman viikon bonuksena. Jos saat ratkaistua kohdat 1 .. "4. Detect single-character XOR", olet jo astunut salakirjoituksen maailmaan.


## Lähteet:

- Tehtävänanto [https://terokarvinen.com/application-hacking/](https://terokarvinen.com/application-hacking/#:~:text=katsotaan%20yhdess%C3%A4%20lis%C3%A4%C3%A4.-,h3%20No%20strings%20attached,-Tiesitk%C3%B6%2C%20ett%C3%A4%20bin%C3%A4%C3%A4reist%C3%A4)
- [How to Use the strings Command on Linux](https://www.howtogeek.com/427805/how-to-use-the-strings-command-on-linux/)
- [GCC Documentation](https://gcc.gnu.org/onlinedocs/)
- [ChatGPT](https://chatgpt.com)
- [Ghidra dokumentaatio (asennus)](https://ghidra-sre.org/InstallationGuide.html#Requirements)
