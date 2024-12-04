# Tehtävät

Oma ympäristö omaan weppihakkerointiin.

Määräaika on 2024-12-04 w49 Wed 14:00, vaikka itsenäisyyspäivänä ei tietenkään ole opetusta.

x) Lue/katso ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva kustakin artikkelista. Kannattaa lisätä myös jokin oma ajatus, idea, huomio tai kysymys.)
Karvinen 2020: [Using New Webgoat 2023.4 to Try Web Hacking](https://terokarvinen.com/2023/webgoat-2023-4-ethical-web-hacking/)

a) Asenna Webgoat 2023.4. (Nimenomaan tämä versio, koska tehtävien numerot ja tehtävät vaihtelevat versioittain.)
Ratkaise WebGoat 2023.4:

  b) (A1) Broken Access Control (WebGoat 2023.4. Pitää olla nimenomaan tämä versio. Eri versioissa on eri tehtävät.)
  Hijack a session (1) [vaikea]
  Insecure Direct Object References (4) [vaikeita kohtia]
  Missing Function Level Access Control (2) [Ei kohtaa 4 "The company fixed the problem, right?", se saattaa olla rikki]
  
  c) (A7) Identity & Auth Failure (WebGoat 2023.4)
  Authentication Bypasses (1)
  Insecure Login (1)
  
  d) (A10) Server-side Request Forgery (WebGoat 2023.4)
  Server-Side Request Forgery (2)
  
  e) Client side (WebGoat 2023.4)
  Bypass front-end restrictions (2)
  
f) Editmenu. Lisää uusi oma komento micro:n palettero-lisäkkeellä käytettäväksi.


# Vastaukset


a) 

Asennetaan webgoat 2023.4, seuraamalla [Teron](https://terokarvinen.com/2023/webgoat-2023-4-ethical-web-hacking/) ohjeita.

Asennetaan tarvittavat muut paketit `sudo apt-get install openjdk-17-jre` sekä `sudo apt-get install ufw`, ja laitetaan palomuuri päälle  `sudo ufw enable`.

![](https://github.com/user-attachments/assets/473cfbc3-5390-412c-a31c-39d3fe41b7c2)

Sitten vain ladataan WebGoat wgetillä

![](https://github.com/user-attachments/assets/ad258301-215b-4304-8295-0b6a662dbded)

Ja ajetaan komento `java -Dfile.encoding=UTF-8 -Dwebgoat.port=8888 -Dwebwolf.port=9090 -jar webgoat-2023.4.jar`

![](https://github.com/user-attachments/assets/446ee9b2-86c6-44e5-8460-10717d6a547f)

Mennään osoitteeseen http://127.0.0.1:8888/WebGoat

![](https://github.com/user-attachments/assets/003ef0ea-9495-43e4-8a2d-b249f20003b1)

Vuohi on elossa.

Luotiin uusi käyttäjä, sekä kirjauduttiin sisään. 
![](https://github.com/user-attachments/assets/5bc51073-f276-46f5-a0fc-9fa8cd0fbea5)

Tässä vaiheessa on hyvä vielä varmistaa että tietokone ei ole yhteydessä internettiin.

Tarkistetaan vielä että ZAP ottaa liikennettä kiinni. 

![](https://github.com/user-attachments/assets/a439d3c7-784e-4c64-8849-7b8af9c6d8b0)

b)
  - Hijack a session
      Ensimmäisessä kohdassa piti varastaa toisen ihmisen istunto. Kokeillaan ensin kirjautua "admin" "password" kombinaatiolla.

    ![](https://github.com/user-attachments/assets/e5f191f4-a649-4dc6-acdc-79e221302e38)

    ZAPissa näkyi kuinka ei kelvannut. Mutta palautteessa näkyi kohta "hijack_cookie". Ohjeessa mainittiin miten tämän avulla ratkaisu pitäisi löytyä.
    Koitin venkslata kyseista arvoa eri suuntiin mutta en keksinyt oikeaa tapaa ratkaista tehtävää. Vinkit kertoivat että olin oikeilla jäljillä mutta en tiennyt
    mistä saisin napattua tarvittavan keksin.
    
   ![](https://github.com/user-attachments/assets/f7c3f60b-d1ec-4460-acc6-194cad5ee3e2)

- Insecure Direct Object References

  Tehtävässä pyritään muokkaamaan urlia jotta päästään käsiksi muiden käyttäjiin. Aluksi syötetään tarvittavat käyttäjätiedot omasta käyttäjästä. 

  Sitten katsotaan serverin vastausta ja löydetään hieman extratietoa, kuten "role" ja "userid".
  ![](https://github.com/user-attachments/assets/84c7695c-233a-4a46-8f48-458881d69792)

  Sitten osoitteesta "WebGoat/IDOR/profile/2342384" saadaan samat tiedot.

  Seuraavassa kohdassa pitäisi keksiä jokin oma userid jotta löytyisi jokin toinen käyttäjä.
  
  ![](https://github.com/user-attachments/assets/7a796ae5-0c11-4682-9d72-f476e97b4fef)
  Webgoat antaa palautteen "internal server error".

  Tässä kohtaa jäin hieman jumiin sillä pelkkä "userid" numeron kohotus ei riittänyt. Vihjeissä luki että tässä kohtaa pitäisi fuzzata jotta oikea ID löytyisi. Kokeilin manuaalisesti muutamia numeroita ja löysin oikean IDn joka oli "2342388"

![](https://github.com/user-attachments/assets/8d0bd27a-c08c-41fe-b415-6f7ca9de4f51)

Niinpä tiedot löytyivät. 

Toisessa kohdassa tietoja piti muuttaa. Mutta en tiennyt miten se tehdään. Kokeilin eri tapoja tehdä PUT request mutta se ei toiminut. 

![](https://github.com/user-attachments/assets/59acb74f-f342-4b48-83f4-097245571a7a)

![](https://github.com/user-attachments/assets/b0970324-5136-457b-95ba-739c75025d28)

IDOR on kuitenkin ratkaistu.


  




f)

Paletteron asennus hoidettiin jo tunnilla, sen asentaminen onnistui komennolla `micro --plugin install palettero`. Teen tämän tehtävän muistikuvieni perusteella, siitä miten Tero näytti tunnilla kuinka uusi komento luodaan. 

Tämän jälkeen voi avata jonkin tekstitiedoston ja siirtyä editmenuun painamalla "ctrl + space". (Ennen editmenuun siirtymistä pitää muistaa valita kaikki muokattava teksti, esimerkiksi "ctrl + a", jos käyttää textfilter komentoja.)


![](https://github.com/user-attachments/assets/d45fd28b-16d8-476e-ad29-c688da46469c)

Joka näyttää tältä.

Valitaan ensimmäinen vaihtoehto eli "add custom commands..."
![](https://github.com/user-attachments/assets/ad56e01b-66ec-425b-afd2-3261663b407f)

Tässä vaiheessa voidaan kirjoittaa oma komento.

Testissä käytin valmista komentoa mikä löytyy jo Paletteron listalta. Kyseinen komento siirtää käyttäjän riville 23.

![](https://github.com/user-attachments/assets/c10620b2-dcb9-4b6c-9f22-5b599d3f9af0)
Annetaan komennolle jokin nimi/kuvaus

![](https://github.com/user-attachments/assets/5e03adeb-86d7-4945-a46f-f663e39f164c)
Sitten aukeaa tiedosto mihin itse komento kirjoitetaan. Kun komento on kirjoitettu voi sen tallentaa "ctrl + s"

![](https://github.com/user-attachments/assets/80726591-8271-4245-a7e1-50955c96af36)
Tiedosto tallentuu /.config/micro hakemistoon, "palettero.pfg" tiedostona. 

![](https://github.com/user-attachments/assets/385b20ac-243d-424d-9b23-472f55a5637b)
Lopulta paletteroon on tullut yksi komento lisää. Aikaisemmin oli 117, mutta nyt on 118 komentoa.




# Lähteet

- Tero Karvinen, Try web hacking on new webgoat 2023.4: https://terokarvinen.com/2023/webgoat-2023-4-ethical-web-hacking/
- Tero Karvinen, Tunkeutumistestaus-kurssi: https://terokarvinen.com/tunkeutumistestaus/
- Tero Karvinen, Palettero: https://github.com/terokarvinen/palettero
