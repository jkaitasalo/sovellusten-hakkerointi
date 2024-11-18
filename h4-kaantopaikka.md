## [h4](https://terokarvinen.com/application-hacking/#:~:text=tai%20kirjaston%20toteutusta.-,h4,-K%C3%A4%C3%A4nt%C3%B6paikka) Kääntöpaikka


#### x) Lue/katso/kuuntele ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)
- Hammond 2022: Ghidra for Reverse Engineering [(PicoCTF 2022 #42 'bbbloat')](https://www.youtube.com/watch?v=oTD_ki86c9I)
  - Ghidra on NSA:n kehittämä ilmainen avoimen lähdekoodin "reverse engineering" (käänteismallinnus) työkalu
  - Parhaansa mukaan kääntää ohjelmalle annetun binäärin C++ -kielelle
  - Binäärin avausvaiheessa ohjelma antaa yhteenvedon binääristä
  - Ohjelma kysyy tahtooko käyttäjä analysoida binääriä (tässä yleisesti oletusvaihtoehdot ovat riittävät)
  - Ohjelmassa funktiot ja niiden osat voi halutessaan nimetä helpottamaan koodin arviointia ja lukua
  - Lähes jokainen ohjelman osa decompilerissa ja binäärin listingissä on linkitetty siten, että voi hyppiä eri yhteyksien välillä ja tarkastella niitä
- Vapaaehtoinen: € Eagle and Nancy 2020: The Ghidra Book: 2. Reversing And Disassembly Tools



#### a) Asenna Ghidra.

Asensin viimeviikon tehtävien yhteydessä Ghidran virtuaalikoneeseeni. Käytän Debian 12-bookwormia, joten minun piti ensin asentaa openjdk, jonka jälkeen asensin Ghidran sen omilta sivuilta [GitHubista](https://github.com/NationalSecurityAgency/ghidra/releases). Tämän jälkeen minun piti vielä erikseen määrittää openjdk:lle `~PATH` muuttuja, jonka tein Ghidran asennusohjeen mukaisesti:

![image](https://github.com/user-attachments/assets/151b0142-fbe5-4a58-a55f-fd9afed388d1)

Näiden vaiheiden jälkeen oli Ghidra asennettu.



#### b) rever-C. Käänteismallinna packd-binääri C-kielelle Ghidralla. Etsi pääohjelma. Anna muuttujielle kuvaavat nimet. Selitä ohjelman toiminta. Ratkaise tehtävä binääristä, ilman alkuperäistä lähdekoodia. ezbin-challenges.zip



#### c) Jos väärinpäin. Muokkaa passtr-ohjelman binääriä (ilman alkuperäistä lähdekoodia) niin, että se hyväksyy kaikki salasanat paitsi oikean. Osoita testein, että ohjelma toimii. ezbin-challenges.zip

Ghidra tuo binäärin suoraan "Executable and Linking Format (ELF)" muodossa.

![image](https://github.com/user-attachments/assets/e21debad-44ed-449b-a349-ae37e903da3b)


Muutetaan se siten, että saadaan raa'assa binäärimudossa:

![image](https://github.com/user-attachments/assets/e86413ee-2ae2-4a99-b866-1937c91fca6f)

Käytin Ghidran hakutoimintoa (pikanäppäin s), jolla hain Stringejä ja käytin hakusanaa "password" ja kaksoisklikkaamalla hakutulosta pääsin kohtaan jossa se sijaitsi.

![image](https://github.com/user-attachments/assets/fd880fb4-373a-489c-870c-2d80107a58d6)

Pienen verran jouduin skrollaamaan, jotta löysin funktion ruudultani, mutta se kuitenkin löytyi

![image](https://github.com/user-attachments/assets/ee72c713-d7e4-4bc6-b0d9-4365e6f54ba7)

Avasin ohjelman yläpalkista "Display Function Graph", joka näyttää funktion ikäänkuin taulukkomuodossa. Tuosta näkymästä pystyy myös napauttamaan viittauksia ja hyppäämään niiden kohtiin, joten hyppäsin kohtaan jossa funktio siirtyy ohjelman ajossa vastauksen antamiseen. Tuo kohta on funktiossa JNZ, "Jump Not Zero"

![image](https://github.com/user-attachments/assets/2505f8c7-0e50-4eac-b661-3b636bc30648)

Muutin (Patch Instruction Ctrl+Shift+G) JNZ -> JZ, jolloin ohjelma hyppäisi tavallaan päinvastoin sen normaalitoimintaa.

![image](https://github.com/user-attachments/assets/882ae9c3-c8ef-4dcc-aaf2-018c68e3dd4a)

Tämän jälkeen exporttasin ohjelman työkansioon (pikanäppäin o) Original File muodossa.

![image](https://github.com/user-attachments/assets/81448844-3fce-4183-b670-25c9f0c4b8f7)

Seuraavaksi navigoin terminaalilla työkansioon testatakseni ohjelman toimivuutta. Tässä kohtaa ohjelma näkyi terminaalissa valkoisena, joka ymmärtääkseni tarkoittaa sitä, että sitä ei voi lähtökohtaisesti tästä ajaa. `chmod +x ./passtr_bin` komennolla muutin tiedoston ajettavaksi, jonka jälkeen sitä pääsi testaamaan.

![image](https://github.com/user-attachments/assets/5c115f0e-e705-4bfd-ae08-909d17260963)

Kuten huomata saattaa, sovellus toimii käänteisesti, kuten oli tarkoitus!


#### d) Nora CrackMe: Käännä binääreiksi Tindall 2023: NoraCodes / crackmes. Lue README.md: älä katso lähdekoodeja, ellet tarvitse niitä apupyöriksi. Näissä tehtävissä binäärejä käänteismallinnetaan. Binäärejä ei muokata, koska muutenhan jokaisen tehtävän ratkaisu olisi vaihtaa palautusarvoksi "return 0".



#### e) Nora crackme01. Ratkaise binääri.

#### e) Nora crackme01e. Ratkaise binääri.

#### f) Nora crackme02. Nimeä pääohjelman muuttujat käänteismallinnetusta binääristä ja selitä ohjelman toiminta. Ratkaise binääri.



#### g) Vapaaehtoinen: Ja sen yli. Crackme01 on useampia ratkaisuja. Montako löydät? Miksi?

#### h) Vapaaehtoinen: Pyytämättäkin. Crackme02 on kaksi ratkaisua. Löydätkö molemmat?

#### i) Vapaaehtoinen, hieman haastavampi: A ray. Nora crackme02e. Ratkaise binääri.



---
## Lähteet:

- GHIDRA for Reverse Engineering (PicoCTF 2022 #42 'bbbloat') [YouTube video](https://www.youtube.com/watch?v=oTD_ki86c9I) käyttäjältä John Hammond
- Ghidra [GitHub](https://github.com/NationalSecurityAgency/ghidra/releases)
- Ghidra [asennusohje](https://htmlpreview.github.io/?https://github.com/NationalSecurityAgency/ghidra/blob/stable/GhidraDocs/InstallationGuide.html)
