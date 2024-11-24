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

- Näyttäisi siltä, että ajatukseni osuivat oikeaan!



#### b) Lab2. Selvitä salasana ja lippu + kirjoita raportti siitä miten aukesi. [lab2.zip](https://terokarvinen.com/application-hacking/lab2.zip)


#### c) Lab3. Kokeile Nora Crackmes harjoituksia tehtävä 3 ja 4 ja loput vapaaehtoisia. Tindall 2023: [NoraCodes / crackmes.](https://github.com/NoraCodes/crackmes)


#### d) Lab4. Vapaaehtoinen: Crackmes.one harjoitus. Saatko salasanan selville? lab4.zip Moodlessa.

---
## Lähteet:

W3Schools - [C](https://www.w3schools.com/c/index.php)
