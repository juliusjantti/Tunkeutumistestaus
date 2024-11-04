# h2 Tehtävät

x) Lue/katso/kuuntele ja tiivistä. [Jaswal 2020: Mastering Metasploit - 4ed: Chapter 1: Approaching a Penetration Test Using Metasploit](https://learning.oreilly.com/library/view/mastering-metasploit/9781838980078/B15076_01_Final_ASB_ePub.xhtml#_idParaDest-31)

a) Harjoittelemme omassa virtuaaliverkossa, jossa on Kali ja Metaspoitable. Osoita testein, että 1) koneet eivät saa yhteyttä Internetiin 2) Koneet saavat yhteyden toisiinsa. (Koneiden ja verkon asentamista ei tarvitse raportoida uudestaan, paitsi jos siinä on ongelmia)

b) Ota Metasploit msfconsole käyttöön

c) Etsi Metasploitable porttiskannaamalla (db_nmap -sn). Tarkista selaimella, että löysit oikean IP:n - Metasploitablen weppipalvelimen etusivulla lukee Metasploitable.

d) Porttiskannaa Metasploitable perusteellisesti. Tallenna tulokset Metasploitin tietokantoihin (db_nmap) ja tiedostoihin (nmap -oA foo).

e) Tarkastele Metasploitin tietokantoihin tallennettuja tietoja komennoilla "hosts" ja "services". Kokeile suodattaa näitä listoja tai hakea niistä.

f) Vertaile nmap:n omaa tiedostoon tallennusta ja db_nmap:n tallennusta tietokantoihin. Mitkä ovat eri tiedostomuotojen ja Metasploitin tietokannan hyvät puolet?

g) Murtaudu Metasploitablen vsftpd-palveluun

h) Päivitä äskeisen vsftpd-murron yhteydessä syntynyt sessio meterpretriin

i) Kerää levittäytymisessä (lateral movement) tarvittavaa tietoa metasploitablesta. Analysoi tiedot. Selitä, miten niitä voisi hyödyntää.

j) Murtaudu Metasploitableen jollain toisella tavalla. (Jos tämä kohta on vaikea, voit tarvittaessa turvautua verkosta löytyviin läpikävelyohjeisiin. Merkitse silloin raporttiin, missä määrin tarvitsit niitä).

k) Demonstroi Meterpretrin ominaisuuksia.

l) Tallenna shell-sessio tekstitiedostoon script-työkalulla (script -fa log001.txt)



# h2 Vastaukset

x)
- Kertaa yleisiä komentoja metasploitissa. (Use, show, setg, run, exploit)
- Myös Meterpreter komentoja (sysinfo, ifconfig, arp, shell, getuid)
- Metasploit on hyvä työkalu koska se on avoimen lähdekoodin ohjelma jota kehitetään jatkuvasti. Sekä se on myös melko helppokäyttöinen.
- Metaslpoitilla hyökkäyksen lopettaminen ja järjestelmästä poistuminen on puhtaampaa ja turvallisempaa.
- Tekstissä on esimerkkihyökkäys jossa mennään vaihe kerrallaan. Siinä hyökätään yhteen yksittäiseen IP-osoitteeseen.
- 

a) 

Alhaalla kuvat siitä miten koneet eivät ole yhteydesssä internettiin, mutta saavat yhteyden toisiinsa.

![kali internet](https://github.com/user-attachments/assets/e2023154-7628-4ec4-9692-1eb6414f0bce)
![metasploit internet](https://github.com/user-attachments/assets/32fc320d-229b-4132-a81f-315ae47e870b)
![kali metasploit](https://github.com/user-attachments/assets/0ef088d2-1bfb-4c83-b218-1a09cb380cd3)
![meta kali](https://github.com/user-attachments/assets/b15da02e-8327-476b-aa3a-fc268d8f800d)

b) 

Otetaan msfconsole käyttöön komennolla `sudo msfconsole`
![konsoli](https://github.com/user-attachments/assets/56baf7a0-ab1e-4561-965e-415dc8834534)
Se on käytössä.

c) 

![löytyy](https://github.com/user-attachments/assets/5ab2f215-743f-479e-91fd-2014013468e3)
Maalikone löytyy.

d) 

Luodaan tehtävälle oma workspace.
![workspace](https://github.com/user-attachments/assets/22bddeea-6e84-41c1-93fb-798f189e7ecd)

Sitten porttiskannataan metaslpoitable ja tallennetaan tulokset tiedostoon "testi". 

![testi](https://github.com/user-attachments/assets/09632094-6ede-42d9-9651-f69811f0c8a0)

e)

Tietokantoihin tallennetut tiedot komentojen `hosts`ja `services` jälkeen. 

![tietokanta](https://github.com/user-attachments/assets/510f8cd9-46a0-4237-beae-5e8903e8b2d5)

f) 

Nmap tallentaa tiedot kolmeen omaan tiedostoon: .gnmap, .nmap ja .xml. "Nmap text format (.nmap)" on formaatti jota zenmap ei voi avata uudestaan. Jos haluaa avata tiedoston kannattaa tallettaa se -XML muotoon. Xml on myös hyvä formaatti jatkojalostukseen, jos sen osaa tehdä. Xml on myös helppo avata useammalla työkalulla. Metaslpoitin oma tietokanta on siisti ja yksinkertainen, ja se näkyy helposti yhdellä komennolla. 

g) 

Murtaudutaan vsftpd-palveluun. Etsitään ensiksi hyökkäys `search` komennolla. 
![](https://github.com/user-attachments/assets/7fef609b-649f-441a-a60f-8501cf047acf)

Sitten asetetaan kohteeksi maalikone komennolla `setg RHOSTS <ip osoite>`. Jonka jälkeen ajetaan komento `run` mikä ajaa hyökkäyksen. 

![vsftpd](https://github.com/user-attachments/assets/04f3d2c2-852d-473f-9c33-a22c68c75393)

Ja niin saatiin shell-yhteys maalikoneeseen. 

h)

 Asetetaan kyseinen sessio taka alalle komennolla `background`. Luodaan uusi sessio komennolla `sessions -u 1` ja liitytään siihen meterpreterillä komennolla `session 2`.
 
![meterpreter](https://github.com/user-attachments/assets/e7b335f3-efb4-4dd3-a978-207e98cd0e52)

i) 

En ihan täysin tiennyt mitä tässä tehtävässä tehdä joten toistin tunnilla käydyt asiat kuten käyttäjien ja salasanojen etsiminen järjestelmästä. 

![](https://github.com/user-attachments/assets/e9923b53-e036-485c-9e04-2dd8c6e98f3d)
`cat /ect/passwd`
![](https://github.com/user-attachments/assets/3125916a-d38e-4f0f-90fc-e261e53d9473)
`cat /ect/shadow`

j)

Kokeillaan yhtä [Rapid7](https://docs.rapid7.com/metasploit/metasploitable-2-exploitability-guide/) sivulta löytyvää hyökkäystä.

![](https://github.com/user-attachments/assets/c9526da3-9ac6-4ffd-ade2-58e1febf0f2a)

Ei näyttänyt onnistuvan. 

Valkamon ja Rapid7 ohjeita seuraamalla yritin UnrealIRCd:tä. 

![](https://github.com/user-attachments/assets/c0447d44-b81c-47fd-b830-9305d3435e30)

Ei onnistunut vieläkään. Tässä kohtaa muistin että tunnilla, demossa oli samanlainen ongelma. Mutta en muista enään miten ongelma korjattiin. 


k)

![](https://github.com/user-attachments/assets/0e6f19e0-e120-4d2a-a2f2-f065ebadaafe)
Komentoja meterpreterillä 

l) 

Tallennettiin shell sessio tekstitiedostoon "log001.txt".

![](https://github.com/user-attachments/assets/b2dcae1b-c35e-44e4-b8c8-2af36e1ef091)







# Lähteet
- Tero Karvinen, Tunkeutumistestaus, https://terokarvinen.com/tunkeutumistestaus/
-  Jaswal 2020: Mastering Metasploit - 4ed: Chapter 1: Approaching a Penetration Test Using Metasploit https://learning.oreilly.com/library/view/mastering-metasploit/9781838980078/B15076_01_Final_ASB_ePub.xhtml#_idParaDest-31
-  Nmap, sacing and loading scan results, https://nmap.org/book/zenmap-saving.html
-  Tuoma Valkamo, Hacking in to metasploitable, https://tuomasvalkamo.com/PenTestCourse/week-2/


