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
- 




# Lähteet

- Tero Karvinen 2022, Cracking Passwords with Hashcat: https://terokarvinen.com/2022/cracking-passwords-with-hashcat/
- Tero Karvinen 2023, Crack File Password With John: https://terokarvinen.com/2023/crack-file-password-with-john/
- Tero Karvinen 2024, Tunkeutumistestaus kurssi: https://terokarvinen.com/tunkeutumistestaus/
- 
