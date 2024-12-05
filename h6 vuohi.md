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


x) 

Artikkelissa ohjeet WebGoatin asentamiseen ja sen ajamisee. WebGoat laitetaan pyörimään porttiin 8888, jotta sen tehtäviä voidaan ratkaista selaimessa localhost osoitteessa.


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

## Pieni probleema

Tässä vaiheessa tuli tehtävien tekemiseen tauko, joten sammutin WebGoatin. Ja seuraavan kerran kun taas jatkoin tehtäviä, ei WebGoat suostunutkaan aukemaan enään.

Sisäänkirjautumissivu aukesi normaalisti, mutta kun yritti kirjautua sisään näkyi komentorivissä seuraava errori
![](https://github.com/user-attachments/assets/dfc24ebf-4a1c-4bd5-a609-d6a2c4a73f1f)

Eikä selaimessa näkynyt mitään.
![](https://github.com/user-attachments/assets/b31006dd-41f8-438e-8c59-058fe20525ac)

Mainittakoon vielä että "admin" käyttäjän salasana näkyi syötteessä, webgoatin käynnistyessä mutta salasana ei kuitenkaan toiminut. 

Kokeilin luoda uuden käyttäjän ja kirjautua sillä sisään mutta sekään ei toiminut.
![](https://github.com/user-attachments/assets/8abe4ab1-5ff8-4aef-ab8c-b4dfb4ce0415)

Urli hieman muuttui mutta edelleen näyttää tyhjää. Urlissa näytti olevan kahteen kertaan osoite "127.0.0.1:8888/WebGoat", joten kumitin sen pois. 

![](https://github.com/user-attachments/assets/02709d68-3f8e-4375-a411-56a35da578b8)

WebGoat tuntui nyt aukeavan.
![](https://github.com/user-attachments/assets/03cd8519-28c9-44bc-83a2-ea4ed1735287)

Mutta syötteessä on kuitenkin kyseinen Errori. Kokeillaan jatkaa tehtäviä

## Jatketaan tehtäviä



- Missing Function Level Access Control

 Tehtävässä piti löytää kaksi piilotettua esinettä. 

  ![](https://github.com/user-attachments/assets/e3aac2dc-b869-430c-8310-8dc4066f0dce)

  Kokeillaan ensin painella kyseisiä nappeja ja katsotaan mitä ZAP nappaa.

  Löytyi ainakin seuraavanlainen kohta mutta siitä ei löytynyt mitään järkevää.

  ![](https://github.com/user-attachments/assets/e68a78a7-6155-4f17-8eaa-26715285dd41)

  TÄssä vaiheessa piti etsiä hieman vinkkejä, ja niitä löytyi [tästä](https://www.youtube.com/watch?v=C-MTbhfXbgg) videosta.

  ![](https://github.com/user-attachments/assets/639f4395-5491-42e2-80ee-33cc0feaffd0)

  Tehtävään löytyy vastaukset kun tarkistaa sivun elementit. Sieltä löytyy kohta "Hidden menu"

![](https://github.com/user-attachments/assets/fdffff7a-0d49-4c6e-9d54-c658c0338eb3)


Seuraavaksi koitetaan saada käyttäjän Jerry tiiviste. 

![](https://github.com/user-attachments/assets/6cc016b3-3d5b-4c87-9864-9601f9ec6899)
Submit-nappia painaessa ottaa ZAP kiinni seuraavanlaista tietoa.

![](https://github.com/user-attachments/assets/d1929400-b346-462e-91bd-4728a40e45b6)

Kyseistä puuntöä pitää hieman muokata. Ensiksi muuttaa "Content-type" JSONiksi, sekä muuttaa POST pyyntö GET pyyntöön. Lisäksi laittaa jotain tekstiä "userHash" kohtaan jotta se ei ole tyhjä. Ja näin saatiin tiivisteet haettua.

![](https://github.com/user-attachments/assets/ac710a9d-c9fe-449b-98ac-b00f388d7f83)

Tähänkin tehtävään oli aiemassa videosta apua. 

![](https://github.com/user-attachments/assets/3088a84f-208a-4cec-b5de-0e17ffbb8dca)
Kohta suoritettu.


c) 

- Authentication bypasses
  
  Tehtävässä pitää päästä turvakysymyksistä läpi.
  
![](https://github.com/user-attachments/assets/a4033724-b3df-4025-abdf-4b8ea01641d2)

Kokeillaan taas ensiksi mitä ZAP nappaa.

![](https://github.com/user-attachments/assets/72e9bad2-a925-416c-972a-07156fb37f56)

Ei näy mitään kovin kummallista. Venkslataan kuitenkin kyseisiä parametreja.


![](https://github.com/user-attachments/assets/249e6dc4-1a00-4de7-8ba3-a97e101a5f36)

Tehtävässä riitti että vaihtoi secQuestion1 ja 2 parametreihin secQuestion A ja B.

![](https://github.com/user-attachments/assets/cb1f529b-4d98-4267-8b74-c8b89e20fd9b)

- Insecure Login

  Tässä kohdassa ei tarvinnut muuta kuin ottaa ZAPilla paketti kiinni ja noukkia sieltä tarvittavat käyttäjätiedot "CaptainJack" ja "BlackPearl".
  ![](https://github.com/user-attachments/assets/df5b1131-1685-4fee-aeeb-c085d83e14a1)

  ![](https://github.com/user-attachments/assets/2b592326-a3e0-4c78-8f2c-757ab32f2ea7)



Tässä vaiheessa alkoi aika loppumaan joten kaikkiin tehtäviin en ehtinyt. Lisäksi nopealla vilkaisulla ne olivat senverran monimutkaisia että omat taidot eivät välttämättä niihin riitä, sekä tehtävien tekeminen älyttömän hitaalla virtuaalikoneella aiheuttaa jo harmaita hiuksia.

d)

- Server SIde Request Forgery



e) 

- Client side filtering

  


  




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
