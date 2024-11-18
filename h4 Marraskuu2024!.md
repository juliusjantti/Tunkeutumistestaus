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
- Hyökkäyksien estäminen ja korjaaminen on jatkuvaa kissa ja hiiri leikkiä. Salasanat täytyy pitää suojattuna sekä liikkeessä että varastoinnissa. Helpoin tapa murtaa salasana on kokeilla yleisimpiä salasanoja. Julkisten paikkojen Wifi-yhteyksien liikenne on harvoin salattua. Joten liikennetta nuuskimalla voi helposti saada käsiinsä salasanoja. Salasanojen murtaminen on helppoa nykyaikana koska laskentateho on nousussa, käytetään yhä heikkoja salasanoja, paljon sanakirjoja joita voi käyttää hyödyksi. John the ripper erinomainen työkalu salasanojen murtamiseen. Hashcat myös hyvä ja nopeampi vaihtoehto salasanojen murtamisenn. Salasanoja täytyy parantaa: käyttää suolausta, parempia tiivisteitä, pidempiä ja monimutkaisia ja uniikkeja salasanoja, kaksisuuntainen vahvistus.

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

![](https://github.com/user-attachments/assets/3bccee59-6173-4c36-ae0a-1a9f16987567)

Statukseksi ei tule "cracked" vaan "exhausted"

Tässä vaiheessa kulutin enemmän aikaa itse kalin kanssa tappelemiseen kuin tehtävien tekemiseen joten ensimmäinen osa jää nyt tähän.

c) 

Asennetaan John [Teron](https://terokarvinen.com/2023/crack-file-password-with-john/) ohjeiden mukaisesti. 

![](https://github.com/user-attachments/assets/9e2e7b89-44ac-4853-9312-81b06df17e2a)

Komentoja ajaessa tuli kuitenkin ongelma. Zlib-gst-pakettia ei löytynyt.

![](https://github.com/user-attachments/assets/c9b599bc-471f-4529-ae87-26c5b4f01ed1)

Koitin jatkaa ohjeita eteenpäin mutta se ei onnistunut.

`./configure` komentoa ajessa tuli virhe OpenSSLlän kanssa.

![](https://github.com/user-attachments/assets/3eabbe3e-5570-41df-a94d-881002f82e77)

Ohjeena oli ajaa komento `./configure --without-openssl`, joten kokeilin sitä, ja se näytti toimivan. 

![](https://github.com/user-attachments/assets/6335c2ad-ed44-4ca8-bb24-4ff737f0f7cf)

Ajetaan sitten näytölle ilmestynyt komento `make -s clean && make -sj2`. Se näytti toimivan.

Testataan vielä ajamalla pelkkä `john`
![](https://github.com/user-attachments/assets/9f95d759-33bc-4a7a-ae3f-94814c7c68b9)

Ladataan zip-tiedosto nimeltään tero ja koitetaan purkaa sitä.
![](https://github.com/user-attachments/assets/476c7767-d66e-4e9b-99df-ce4abdcee768)
Eipä onnistunut.

Seurataan ohjeita ja lopulta saadaan tiedoston salaus purettua.

![](https://github.com/user-attachments/assets/c60c9ff4-24fa-4649-b225-da2859faae72)

Salasana oli "butterfly", niin kuin pitikin


d)

Asennetaan fuff [Teron](https://terokarvinen.com/2023/fuffme-web-fuzzing-target-debian/) ohjeiden mukaisesti.

![](https://github.com/user-attachments/assets/442c2e05-b483-45cc-aa49-23c393e1bbda)

Maalin lataus ja asennus sujui ongelmitta.
Ladataan vielä sanalistat

Sanalistojen jälkeen kokeillaan fuzzausta komennolla `ffuf -w ~/wordlists/common.txt -u http://localhost/cd/basic/FUZZ`
![](https://github.com/user-attachments/assets/16240d9a-57ea-4efa-9e7d-10a5a8ecf298)

"Class" ja "developement.log" näyttäisi löytyvän.

Ensimmäisen tehtävän suoritus epäonnistui mutta seuraavassa tuli jo erroria.

![](https://github.com/user-attachments/assets/910400a4-b74e-4f0f-a1c2-5610f31228ff)

Seuraavakaan tehtävä ei toiminut, sama error. En tiedä mikä on vikana. 

Pitkän pähkäilyn jälkeen tajusin että koitin fuzzata itse FFuf.me sivua enkä omaa localhostia. Korjasin osoitteen oikeaski ja näin löysin oikeita vastauksia.

![](https://github.com/user-attachments/assets/4fb2fab9-0b58-4305-a953-e601793381d8)

Kohta "File extensions"

![Näyttökuva 2024-11-18 kello 10 52 49](https://github.com/user-attachments/assets/70e6145e-90e1-48c7-8e2d-4ab1733e8b95)

Kohta " No 404 status"
![Näyttökuva 2024-11-18 kello 10 54 33](https://github.com/user-attachments/assets/ec92c9d2-5fab-4268-b3c6-b6867d5e177a)

Loput kohdat "Param Mining", "Rate Limited" ja "Subdomains".

![Näyttökuva 2024-11-18 kello 10 56 18](https://github.com/user-attachments/assets/af34c637-bc98-4f2e-8849-6530547ac169)
![Näyttökuva 2024-11-18 kello 11 00 40](https://github.com/user-attachments/assets/8d4f2211-a7a1-4abd-8906-35b30c4575c5)
![Näyttökuva 2024-11-18 kello 11 02 25](https://github.com/user-attachments/assets/0696aba0-6d9f-48f3-af9a-3c21a8ab6c01)

e) 

Luodaan salasanalla suojattu PDF tiedosto.

[Tästä](https://www.youtube.com/watch?v=-AnQ2GAbFUY) videosta löytyi ohjeet PDF tiedoston salaamiseen ja salauksen murtamseen.

Asennetaan ensin "pdftk" komennolla `sudo apt-get install pdftk`

Sitten luodaan tiedosto komennolla `pdftk tiedosto.pdf output pwd.pdf user_pw salasana`

![Näyttökuva 2024-11-18 kello 11 26 11](https://github.com/user-attachments/assets/b22439e2-d515-420c-8ec0-bd1740aa6bfa)

Ja huomataan miten se ei toimi.

Kokeillaan ladata netistä valmis .pdf tiedosto ja asetetaan sille salasana. 

![Näyttökuva 2024-11-18 kello 11 40 29](https://github.com/user-attachments/assets/1b649d7c-9b60-4f29-b778-07b23b595353)

Se näyttäisi toimivan.

Sitten otetaan salasanan tiiviste erilliseen pdf.hash tiedostoon. 

![Näyttökuva 2024-11-18 kello 11 41 36](https://github.com/user-attachments/assets/db6baf43-8e93-4e6e-acea-ba90b61863df)

Sitten käytetään Johnia salasanan korkkaamiseen komennolla `john pdf.hash`

![Näyttökuva 2024-11-18 kello 11 43 37](https://github.com/user-attachments/assets/9fd10e32-c53b-4996-af4e-641eb52e8cf5)

f) 

Kokeillaan murtaa linuxin käyttäjän salasana tiivisteestä.
Ensin luodaan uusi käyttäjä "Matti" komennolla `sudo useradd Matti`. Ja asetetaan hänelle salasana komennolla `sudo passwd Matti`
![Näyttökuva 2024-11-18 kello 11 50 11](https://github.com/user-attachments/assets/2bc46eef-b014-43a4-99ee-1cd0800e22f0)

Matin tiiviste löytyi kansiosta /etc/shadow, sekä matin muut tiedot löytyvät osoitteesta /etc/passwd.
Kopioidaan molemmista tiedostoista Matin tiedot ja lisätään ne omiin tiedostoihin nimeltä "shadow" ja "passwd", jonka jälkeen yhdistetään tiedostot uuteeen "unshadow" tiedostoon..

![Näyttökuva 2024-11-18 kello 12 09 34](https://github.com/user-attachments/assets/40d8eb0f-2d8d-4235-8cc5-c90811c7c7d2)

Samalla luodaan myös oma sanalista "salasanoja.txt" jossa on salasanoja joita John kokeilee.

![Näyttökuva 2024-11-18 kello 12 09 06](https://github.com/user-attachments/assets/4db4d0b0-1da9-4b5b-ac09-1b3aa6e704ca)

Lopuksi ajetaan komento`sudo john --wordlist=/usr/share/wordlists/salasanoja.txt --format=crypt unshadow` joka hoitaa itse murtamisen. Komennossa esitetään missä sanaista tiedosto sijaitsee sekä mikä tiedosto on murron kohteena (tässä kohtaa tiedosto unshadow).

![Näyttökuva 2024-11-18 kello 12 12 29](https://github.com/user-attachments/assets/04b73044-54f8-4a78-a500-72c379138c54)

Ja kappas se toimi. Matin salasana on murrettu.

[Kyseinen](https://www.youtube.com/watch?v=5MLprTAxYDA&t=10s) video toimi apuna tähän tehtävään.










# Lähteet

- Tero Karvinen 2022, Cracking Passwords with Hashcat: https://terokarvinen.com/2022/cracking-passwords-with-hashcat/
- Tero Karvinen 2023, Crack File Password With John: https://terokarvinen.com/2023/crack-file-password-with-john/
- Tero Karvinen 2024, Tunkeutumistestaus kurssi: https://terokarvinen.com/tunkeutumistestaus/
- Tero Karvinen, Fuffme - Install Web Fuzzing Target on Debian: https://terokarvinen.com/2023/fuffme-web-fuzzing-target-debian/
- ffuf.me, Target practice: http://ffuf.me/
- CybrZone, Crack password protecte PDF documents with John The Ripper: https://www.youtube.com/watch?v=-AnQ2GAbFUY
- G MAN: Security, CRACK the Password | JOHN the Ripper Password Cracking (5 Minutes) | Basic Tutorial: https://www.youtube.com/watch?v=5MLprTAxYDA&t=10s
