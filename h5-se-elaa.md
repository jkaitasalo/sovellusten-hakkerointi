## [h5](https://terokarvinen.com/application-hacking/#:~:text=ainakin%20brittil%C3%A4isiss%C3%A4%20yliopistoissa.-,h5,-Se%20el%C3%A4%C3%A4!) Se elää!
Tämä tehtävänanto sisältää pääosin Lari Iso-Anttilan laatimia tehtäviä.


---
#### a) Lab1. Tutkiminen mikä on ohjelmassa vialla ja miten se korjataan. [lab1.zip](https://terokarvinen.com/application-hacking/lab1.zip)

- Latasin tehtävänannosta Lab1.zip tiedoston, jonka purin paikalliseen kansioon
- Tämän jälkeen kurkkasin mitä zipin sisällä oli ollut komennolla `ls` ja tämän jälkeen ajoin GNU-debuggerin käyntiin komennolla `gdb ./gdb_example1`

![image](https://github.com/user-attachments/assets/4aa1e191-85ed-44ef-bc6a-e9a808f287e9)

- Ajattelin, että tässä kohtaa olisi hyvä idea vilkaista mitä koodia tiedosto sisältää käyttämällä komentoa `list`
- Tuota komentoa sai pari kertaa napauttaa, jotta saatiin näkyviin koko koodi.
  - Ohjelma kertoo rivin 20 jälkeen ajetun komennon jälkeen, että lisää koodia ei ole <br>`"Line number 21 out of range; gdb_example1.c has 20 lines."`
  - Uskoisin tuon rivimäärän selviävän jollain toisella Linux komennolla, mutta tähän hätään sitä en tullut ajatelleeksi

![image](https://github.com/user-attachments/assets/3b276772-6d05-4bb6-a3ed-c94b2404887e)

- Ohjelma näyttäisi koostuvan funktiosta `print_scrambled`, jota kutsutaan kahdesti `main()` ajon aikana
  - Funktio ajaa do-while silmukan, joka iteroi annetun stringin jokaisen merkin
  - funktio tulostaa merkit, niiden ascii paikkaa muutettuna i:n arvolla (3), kunnes stringissä ei ole merkkejä jäljellä
- Tässä kohtaa ajoin ohjelman sellaisenaan tutkiakseni havaintoja ja huomasinkin, että ohjelman ajo päättyy virhetilanteeseen ensimmäisen tulostuksen jälkeen.

![image](https://github.com/user-attachments/assets/e29bbcc2-26ce-419f-8010-9937f6ee513a)

- `micro gdb_example.c` pääsin muokkaamaan ohjelman rivin 14 `NULL` tilalle merkkijonon `fixed`, jonka jälkeen ajoin `make` komennolla binäärin uudestaan kasaan.

![image](https://github.com/user-attachments/assets/3038256c-f44f-44f8-8a09-b4f81f43c063)

![image](https://github.com/user-attachments/assets/fc0b092a-8d0a-4738-b50c-457c2a1a8e6e)

- Näyttäisi siltä, että ajatukseni osuivat oikeaan! `Hello, world.` string tulostetaan tuolla ASCII muutoksella, jolloin ensimmäinen tulostettava merkki on kuin onkin `K` jne.


#### b) Lab2. Selvitä salasana ja lippu + kirjoita raportti siitä miten aukesi. [lab2.zip](https://terokarvinen.com/application-hacking/lab2.zip)

- Latasin tehtävänannosta Lab2.zip tiedoston, jonka purin paikalliseen kansioon
- En oikein keksinyt suoraan mitään erikoisempaa lähestymistapaa, joten aloitin vain ohjelman ajamisella hitaasti `break main` ja `nexti` komentojen avulla

![image](https://github.com/user-attachments/assets/a3803555-e77f-4eac-9509-3122f73ec05c)

- Havaitsin, että rekistereihin `$rdi`, `$rbx` ja `$rdi` tallentuu jotain tietoja.
- `$rdi` rekisterissä oleva merkkijono näytti kummalliselta, joten päätin heittää sen arvauksena salasanasta. Väärinhän tuo meni.

![image](https://github.com/user-attachments/assets/2b77c31b-1f5d-470c-9107-88ac60e93ed9)

- Huomasin, että ohjelma käy jonkinlaisen silmukan läpi, todennäköisesti samankaltaisesti, kuin edellisessä tehtävässä.
- Valitettavasti en keksi, kuinka voisin tulkata tuota silmukkaa.
  - Yritin kaivella erinäisten kuperkeikkojen kautta kääntäminen hexaksi ja sieltä selkotekstiksi, mutta käteen jäi aina jotain todella epämääräistä
    - esim `t= ...w...`
    - tai `.........w..y..`
    - ei ainakaan itselle tällä avaudu, eikä nuo erityisemmin vastaa mitään, mitä rekistereiden tarkkailulla osuisi silmään

- Ainoa varma on se, että `$rbx` rekisteriin tallentuu käyttäjän antama salasana.
- `$rdi` rekisteri näyttäisi nappaavan käyttäjälle annettavan tekstin, mutta lopulta se siirtyy rekisteriin `$rsi`

![image](https://github.com/user-attachments/assets/8f362939-c3cb-4e8c-b42b-1cd5c6561a55)





#### c) Lab3. Kokeile Nora Crackmes harjoituksia tehtävä 3 ja 4 ja loput vapaaehtoisia. Tindall 2023: [NoraCodes / crackmes.](https://github.com/NoraCodes/crackmes)


#### d) Lab4. Vapaaehtoinen: Crackmes.one harjoitus. Saatko salasanan selville? lab4.zip Moodlessa.




---
## Lähteet:

- Lari Iso-Anttilan opiskelijoille jakamat kalvot
- W3Schools - [C](https://www.w3schools.com/c/index.php)
- ASCII [Table](https://www.asciitable.com/)
- RapidTables - [Hex to ASCII](https://www.rapidtables.com/convert/number/hex-to-ascii.html)
- ChatGPT
