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

- LockHeed and Martinin kehittämä Cyber Kill Chain on turvallisuusmalli, joka kuvaa kyberhyökkäyksen vaiheet alusta loppuun. Sitä käytetään apuna hyökkäyksien tunnistamisessa sekä estämisessä. Kybertappoketju koostuu seitsemästä kohddasta jotka ovat: Reconnaissance, Weaponization, Delivery, Exploitation, Installation, Command and Control (C2), sekä Actions on Objectives.
  
- Active reconnaissance eli aktiivinen tiedustelu on tiedustelu jossa lähetetään aktiivisesti informaatiota hyökkäyksen kohteelle. Yleensä aktiivisen tiedustelun vaiheet ovat jo yksinään lain vastaisia. Aktiivista tiedustelua on esimerkiksi porttien skannaus, sekä haavoittuvuuksien etsiminen. Porttiskannaukseen käytettyjä ohjelmia on esimerkiksi: Nmap, Masscan, sekä Udpprotoscanner. Verkkosovelluksia voi tutkia ohjellmalla nimeltä EyeWitness. Verkkohaavoittuvuuksien etsimiseen käytettäviä sovelluksia: Nessus, Nexpose, Nikto, Zed Attack Proxy. 

- Oikeudessa käsitelty tapaus jossa 17-vuotias tekijä oli porttiskannannut ja yrittänyt tunkeutua Osuuspankkikeskus-OPK osuuskunnan tietojärjestelmiin. Tekijä tuomittiin syylliseksi ja hänet määrättiin korvaamaan sattuneet vahingot yhteensä noin 75 000 markkaa.

a) 


 


