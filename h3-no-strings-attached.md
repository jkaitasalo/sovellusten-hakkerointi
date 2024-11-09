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

#### c) Packd. Aja 'packd' paketista ezbin-challenges.zip. Mikä on salasana? Mikä on lippu? (Tämä tehtävä on hieman haastavampi. Kirjaa ylös kokeilemasi lähestymistavat ja keksimäsi hypoteesit. Toivottavasti pääset itse maaliin, mutta jos et, läpikävely paljastuu tunnilla...)

#### d) Vapaaehtoinen bonus: Cryptopals. Crypto Challenge Set 1. Tätä voi tehdä useamman viikon bonuksena. Jos saat ratkaistua kohdat 1 .. "4. Detect single-character XOR", olet jo astunut salakirjoituksen maailmaan.


## Lähteet:

- Tehtävänanto: [https://terokarvinen.com/application-hacking/](https://terokarvinen.com/application-hacking/#:~:text=katsotaan%20yhdess%C3%A4%20lis%C3%A4%C3%A4.-,h3%20No%20strings%20attached,-Tiesitk%C3%B6%2C%20ett%C3%A4%20bin%C3%A4%C3%A4reist%C3%A4)
- [How to Use the strings Command on Linux](https://www.howtogeek.com/427805/how-to-use-the-strings-command-on-linux/)
