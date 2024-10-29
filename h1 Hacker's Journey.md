# h1 Hacker's journey

## Tehtävät

x) Lue/katso/kuuntele ja tiivistä.

- Herrasmieshakkerit (RSS) tai Darknet Diaries (RSS) , yksi vapaavalintainen jakso jommasta kummasta.

- [Hutchins et al 2011: Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains, chapters Abstract, 3.2 Intrusion Kill Chain.](https://lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf)

- [Santos et al: The Art of Hacking (Video Collection): 4.3 Surveying Essential Tools for Active Reconnaissance.](https://learning.oreilly.com/videos/the-art-of/9780135767849/9780135767849-SPTT_04_00/)

- [KKO 2003:36](https://finlex.fi/fi/oikeus/kko/kko/2003/20030036)

a) Asenna Kali virtuaalikoneeseen. (Jos asennuksessa ei ole mitään ongelmia tai olet asentanut jo aiemmin, tarkkaa raporttia tästä alakohdasta ei tarvita. Kerro silloin kuitenkin, mikä versio ja millä asennustavalla. Jos on ongelmia, niin tarkka ja toistettava raportti).

b) Irrota Kali-virtuaalikone verkosta. Todista testein, että kone ei saa yhteyttä Internetiin (esim. 'ping 8.8.8.8')

c) Porttiskannaa 1000 tavallisinta tcp-porttia omasta koneestasi (nmap -A localhost). Analysoi tulokset.

d) Asenna kaksi vapaavalintaista demonia ja skannaa uudelleen. Analysoi ja selitä erot.

e) Asenna Metasploitable 2 virtuaalikoneeseen

f) Tee koneiden välille virtuaaliverkko. Jos säätelet VirtualBoxista
Kali saa yhteyden Internettiin, mutta sen voi laittaa pois päältä
Kalin ja Metasploitablen välillä on host-only network, niin että porttiskannatessa ym. koneet on eristetty intenetistä, mutta ne saavat yhteyden toisiinsa
Vaihtoehtoisesti voit tehdä molempien koneiden asennuksen ja virtuaaliverkon vagrantilla. Silloin molemmat koneet samaan Vagrantfile:n.

g) Etsi Metasploitable porttiskannaamalla (nmap -sn). Tarkista selaimella, että löysit oikean IP:n - Metasploitablen weppipalvelimen etusivulla lukee Metasploitable.

h) Porttiskannaa Metasploitable huolellisesti ja kaikki portit (nmap -A -p-). Poimi 2-3 hyökkääjälle kiinnostavinta porttia. Analysoi ja selitä tulokset näiden porttien osalta.

## Vastaukset

x)

- Kuuntelin Herrasmieshakkereiden jakson 34, Tietoturvan Niksipirkka. Ohessa muistiinpanoja jaksosta.
    - Onko rikollinen tausta este vai meriitti it alalla? Sinänsä ei mutta luottamuksen rakentaminen voi olla vaikeaa. 

      Korona aikana nettikaupoittelu kasvanut paljon esimerkiksi Wolt. Tämä vaatii paljon uutta digiosaamista ja kehitystä. 

      Keskolla vain yksi tietoturvatiimi, joka sijaitsee pääkaupunkiseudulla. Toimii yhteistyössä muiden IT tiimien kanssa. 

      Kesko kerää kulutustietoa asiakkaista, mutta vain heiltä jotka ovat antaneet luvan. Tietoa käytetään tarjouksien räätälöimiseen ostotottumusten perusteella. 

      Kruoka äpissä ominaisuus jolla voi seurata omaa ruokakulutusta. Syökö vastuullisesti, tai liikaa suolaa/sokeria/lihaa. 

      EUn direktiivit aiheuttavat Keskon konsernille enenevissä määrin jatkuvasti töitä. 

      K-plussa kortin saaminen Apple pay lompakkoon on työn alla, mutta ei ihan lähellä vielä. 


- LockHeed and Martinin kehittämä Cyber Kill Chain on turvallisuusmalli, joka kuvaa kyberhyökkäyksen vaiheet alusta loppuun. Sitä käytetään apuna hyökkäyksien tunnistamisessa sekä estämisessä. Kybertappoketju koostuu seitsemästä kohddasta jotka ovat: Reconnaissance, Weaponization, Delivery, Exploitation, Installation, Command and Control (C2), sekä Actions on Objectives.
  
- Active reconnaissance eli aktiivinen tiedustelu on tiedustelu jossa lähetetään aktiivisesti informaatiota hyökkäyksen kohteelle. Yleensä aktiivisen tiedustelun vaiheet ovat jo yksinään lain vastaisia. Aktiivista tiedustelua on esimerkiksi porttien skannaus, sekä haavoittuvuuksien etsiminen. Porttiskannaukseen käytettyjä ohjelmia on esimerkiksi: Nmap, Masscan, sekä Udpprotoscanner. Verkkosovelluksia voi tutkia ohjellmalla nimeltä EyeWitness. Verkkohaavoittuvuuksien etsimiseen käytettäviä sovelluksia: Nessus, Nexpose, Nikto, Zed Attack Proxy. 

- Oikeudessa käsitelty tapaus jossa 17-vuotias tekijä oli porttiskannannut ja yrittänyt tunkeutua Osuuspankkikeskus-OPK osuuskunnan tietojärjestelmiin. Tekijä tuomittiin syylliseksi ja hänet määrättiin korvaamaan sattuneet vahingot yhteensä noin 75 000 markkaa.

a) 
Asennetaan Kali virtuaalikoneeseen. Aloitetaan lataamalla valmiiksi rakennettu Virtuaalikone sivulta [Per-Built Virtual Mchines](https://www.kali.org/get-kali/#kali-virtual-machines). Sekä seurataan [GeeksforGeeks:n](https://www.geeksforgeeks.org/install-kali-linux-in-virtualbox/) sivuilta ohjeita.
Alla vielä kuva asennetusta virtuaalikoneesta. 

![valmis kone](https://github.com/user-attachments/assets/6802edbe-fc04-4a56-a1d6-1b88b4826ce0)

Virtuaalikone on toistaiseksi yhteydessä verkkoon.

![google](https://github.com/user-attachments/assets/ba6a01e8-f2e5-46f2-a24c-bf0003536576)

b) 

Otetaan se irti verkosta vetämällä virtuaalisesti verkkokaapli irti koneesta. Mennään kohtaan settings > network > advanced > ja täppä pois kohdasta "Cable Connected".

![töpseli irti](https://github.com/user-attachments/assets/a49830e8-0c94-40f0-bbc7-8a73529813fb)

Kokeillaan vielä toimiiko netti.

![google ei toimi](https://github.com/user-attachments/assets/54f61e2a-f7e1-4deb-8a5a-fea438a5c3cf)
![ping](https://github.com/user-attachments/assets/2ac3d184-d716-4d01-8f6d-fb54c8e502a8)

Kuvankaappauksista näkyy miten sekä selain että pingaus ei toimi.

c) 

Porttiskannataan komennolla `nmap -A localhost` 1000 yleisintä porttia. 
![skannaus](https://github.com/user-attachments/assets/d45fcead-ccf6-4a26-8be1-719e9fdc720a)
Niitä löytyi nolla kappaletta. Virtuaalikone ei ole kiinni internetissä joten portteja ei ole löydettäväksi. 

Asennetaan muutama demoni ja ajetaan komento uudestaan. Tässä kohtaa asensin Apache2 HTTP palvelimen ja FTP palvelimen. 
![kaksi](https://github.com/user-attachments/assets/4b8ba94b-aa16-41f2-8821-f0e6c748ae94)
Skannasin 100 ensimmäistä porttia, ja kappas skannauksen jälkeen löytyikin kaksi avonaista. Portit auki FTP ja HTTP liikenteelle. 

e) 
f) 

Asennetaan Metasploitable 2 virtuaalikone [sivustolta](https://sourceforge.net/projects/metasploitable/). Seurataan [Tuomas Valkamon ohjeita](https://tuomasvalkamo.com/PenTestCourse/week-2/) metasploitablen asentamiseen ja verkon luomiseen tietokoneiden välille. Metasploitablen lataukseen meni jostain syystä noin tunti. 

Pienen pyristelyn jälkeen metasploitable on asennettu. 
![](https://github.com/user-attachments/assets/ed75339b-84be-4119-ac8c-aff95c55a8c5)
Käynnistetään se ja kirjaudutaan sisään käyttäjällä msfadmin
![](https://github.com/user-attachments/assets/5acbf0d5-1122-49df-8ee2-65f547c43665)
Sisään päästy! Testataan vielä että tietokone ei ole yhteydessä internettiin pingaamalla 8.8.8.8 tai google.com. Niihin ei saada yhteyttä. Varmistetaan sitten myös ettei hyökkäävällä Kali koneellakaan pääse internettiin.

Yritetään ottaa Kalilla yhteys Metasploitable koneeseen:
![toimii](https://github.com/user-attachments/assets/aac4012f-28a5-44a6-ac33-6cefb72fd092)
Ja kas näin molemmat tietokoneet näyttävät olevan samassa verkossa.

g) 





















## Lähteet

- Kali, Pre-Built Virtual Machines, https://www.kali.org/get-kali/#kali-virtual-machines
- Tero Karvinen, Tunkeutumistestaus, https://terokarvinen.com/tunkeutumistestaus/
- Geeksforgeeks, How to Install Kali Linux in VirtualBox: Using Pre-built VM, https://www.geeksforgeeks.org/install-kali-linux-in-virtualbox/
- Tony Teaches Tech, How to use nmap to scan for open ports, https://www.youtube.com/watch?v=ifbwTt3_oCg
- Tuomas Valkamo, Hacking into a target using metasploit, https://tuomasvalkamo.com/PenTestCourse/week-2/
- Sourceforge, Metasploitable 2 download, https://sourceforge.net/projects/metasploitable/
- 


