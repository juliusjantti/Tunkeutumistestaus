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
