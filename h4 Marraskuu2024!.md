# Tehtävät


x) Lue/katso ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva kustakin artikkelista. Kannattaa lisätä myös jokin oma ajatus, idea, huomio tai kysymys.)
- Karvinen 2022: [Cracking Passwords with Hashcat](https://terokarvinen.com/2022/cracking-passwords-with-hashcat/)
- Karvinen 2023: [Crack File Password With John](https://terokarvinen.com/2023/crack-file-password-with-john/)
- € Santos et al 2017: [Security Penetration Testing - The Art of Hacking Series LiveLessons: Lesson 6: Hacking User Credentials](https://www.oreilly.com/videos/security-penetration-testing/9780134833989/9780134833989-sptt_00_06_00_00/)
- Polop et al 2024: [HackTricks: MSFVenom - CheatSheet](https://book.hacktricks.xyz/generic-methodologies-and-resources/reverse-shells/msfvenom) (Katso kokonaisuus, poimi itsellesi komento tai pari, joita voisit käyttää)

a) Asenna Hashcat ja testaa sen toiminta murtamalla esimerkkisalasana.

c) Asenna John the Ripper ja testaa sen toiminta murtamalla jonkin esimerkkitiedoston salasana.

d) Fuffme. Asenna Ffufme harjoitusmaali paikallisesti omalle koneellesi. Ratkaise tehtävät (kaikki paitsi ei "Content Discovery - Pipes")
- Basic Content Discovery
- Content Discovery With Recursion
- Content Discovery With File Extensions
- No 404 Status
- Param Mining
- Rate Limited
- Subdomains - Virtual Host Enumeration

e) Tiedosto. Tee itse tai etsi verkosta jokin salakirjoitettu tiedosto, jonka saat auki. Murra sen salaus. (Jokin muu formaatti kuin aiemmissa alakohdissa kokeilemasi).

f) Tiiviste. Tee itse tai etsi verkosta salasanan tiiviste, jonka saat auki. Murra sen salaus. (Jokin muu formaatti kuin aiemmissa alakohdissa kokeilemasi. Voit esim. tehdä käyttäjän Linuxiin ja murtaa sen salasanan.)

g) Tee msfvenom-työkalulla haittaohjelma, joka soittaa kotiin (reverse shell). Ota yhteys vastaan metasploitin multi/handler -työkalulla.
Haittaohjelma ei saa olla automaattisesti leviävä. Msfvenom tekee tunnilla opetelluilla asetuksilla ohjelman, joka avaa reverse shellin, kun sen ajaa, mutta joka ei leviä eikä tee muutenkaan mitään itsestään.



# Vastaukset

x) 

- Ohjeet hashcatin asentamiseen ja sen käyttöön. Simppeli työkalu jota voi käyttää tiivisteiden murtamiseen. Ohjeessa ladataan sanakirjatiedosto "Rockyou" joka sisältää miljoonia sanoja. Hashcat kokeilee kaikkien sanojen
  tiivisteitä murrettavaan tiivisteeseen.
- Ohjeet John-työkalun asentamiseen. Sen avulla voidaan murtaa salasanoja esimerkiksi zip-tiedostoihin. Ohjeissa on valmis zip-tiedosto jonka murtamista harjoitellaan.
- Hyökkäyksien estäminen ja korjaaminen on jatkuvaa kissa ja hiiri leikkiä. Salasanat täytyy pitää suojattuna sekä liikkeessä että varastoinnissa. Helpoin tapa murtaa salasana on kokeilla yleisimpiä salasanoja. Julkisten paikkojen Wifi-yhteyksien liikenne on harvoin salattua. Joten liikennetta nuuskimalla voi helposti saada käsiinsä salasanoja. Salasanojen murtaminen on helppoa nykyaikana koska laskentateho on nousussa, käytetään yhä heikkoja salasanoja, paljon sanakirjoja joita voi käyttää hyödyksi.

  a)

   Asennetaan hashcat [Teron](https://terokarvinen.com/2022/cracking-passwords-with-hashcat/) ohjeiden mukaisesti. Sekä ladataan "Rockyou" sanakirjatiedosto.

![](https://github.com/user-attachments/assets/f7767e48-735c-4da7-894a-ecaae8544fde)
![](https://github.com/user-attachments/assets/52273c38-132b-43ef-8def-b532c671b518)

Otetaan sanakirjan alusta yksi sana testiksi, ja ajetaan sen tiiviste erilliseen tiedostoon. Salasana on tässä testissä "princess".
![](https://github.com/user-attachments/assets/0283ba8b-8129-43fa-a429-303881f50449)

Koska kyseessä on vain testi, tehdään oma sanakirja jossa on vain muutama sana.
![](https://github.com/user-attachments/assets/dcad4dee-9f55-46e5-b0c4-63c63ebaa0fa)

Koska tiedetään jo valmiiksi että kyseessä on MD5 tiiviste, ei tiivistettä tarvitse analysoida. Nyt yritetään murtaa se hashcatilla. Ajetaan komento `hashcat -m 0 ekatesti.txt salasanoja.txt -o solved`

![](https://github.com/user-attachments/assets/3d35dfd2-666d-4c5d-8ef8-f3dc316864eb)

Ei näemmä toiminut ajaa tiiviste tiedostosta. Kokeillaan sitten laittaa tiiviste suoraan komentoon.
![](https://github.com/user-attachments/assets/c30b9a40-f373-4d2d-ab1e-a5871cc8b699)
Eipä toiminut vieläkään. 

Lisätäänpä hieman lisää muistia koneeseen.

![](https://github.com/user-attachments/assets/d47ab2e0-76a8-4a3d-8788-8bfc1eb4afc6)

ja kokeillaan uudestaan.

![](https://github.com/user-attachments/assets/1d58b6c5-b649-41ad-859d-ea73d7beb221)
Ajoin komennon useita kertoja ja useammalla tavalla mutta jostain syystä en saanut mitään tulosta.

Lopuksi kokeilin ajaa suoraan ohjeista kopioidun komennon, ja se näytti toimivan. 

![](https://github.com/user-attachments/assets/5d4765eb-9fc8-454f-aedc-28085498a370)

En ymmärrä mikä on vikana. 












# Lähteet

- Tero Karvinen 2022, Cracking Passwords with Hashcat: https://terokarvinen.com/2022/cracking-passwords-with-hashcat/
- Tero Karvinen 2023, Crack File Password With John: https://terokarvinen.com/2023/crack-file-password-with-john/
- Tero Karvinen 2024, Tunkeutumistestaus kurssi: https://terokarvinen.com/tunkeutumistestaus/
- 
