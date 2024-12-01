## [h6](https://terokarvinen.com/application-hacking/#:~:text=kalvot%20l%C3%B6ytyv%C3%A4t%20Moodlesta-,h6,-Sulaa%20hulluutta) Sulaa hulluutta
Tämä tehtävänanto sisältää pääosin Lari Iso-Anttilan laatimia tehtäviä.

#### a) Tutki tiedostoa h1.jpg jo opituilla työkaluilla. Mitä saat selville?

- `file h1-jpg` komennolla aukesi seuraavaa:

![image](https://github.com/user-attachments/assets/7ca7a3a9-5ccd-4341-9e57-76b5fda575bd)

- tiedostotyyppi: JPEG
- kuva sisältää Exif standardin dataa TIFF formaatissa
- kuvan resoluutio 1024x1024 pikseliä eli 1:1 neliön mallinen
- `precision 8` ja `components 3` viittaa RGB 256 värikuvaan

#### b) Tutki tiedostoa h1.jpg binwalk:lla. Mitä tietoja löydät nyt tiedostosta? Mitä työkalua käyttäisit tiedostojen erottamiseen? (Huomaa, että binwalk versio 2.x ja 3.x toimivat eri tavalla.)
#### c) FOSS (Free Android OpenSource). Tutustu Android-sovelluksiin Offan (2024) listalta: [Android FOSS](https://github.com/offa/android-foss). Valitse listalla itsellesi mielenkiintoisin applikaatio ja mene sen GitHubiin. Lataa ohjelman APK itsellesi ja käytä seuraavia työkaluja tutustuaksesi, miten APK:n voi avata.
- ZIP
- JADX
- Bytecode-viewer
#### d) Vapaaehtoinen: Tutustu ESP32-projekteihin Covarrubias 2024: [Awesome ESP](https://github.com/agucova/awesome-esp). Valitse niistä itsellesi mielenkiintoisin projekti. Tutki, miten saat avattua ESP32 binäärin. Kirjoita raporttiin mitä applikaatiota tutkit ja mitä tietoja sait selvitettyä käännetystä paketista. Tarvittaessa voit verrata, vastaako tieto githubissa olevaa koodia.
