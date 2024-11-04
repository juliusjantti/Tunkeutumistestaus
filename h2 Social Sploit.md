# h2 Tehtävät

x) Lue/katso/kuuntele ja tiivistä. (Jaswal 2020: Mastering Metasploit - 4ed: Chapter 1: Approaching a Penetration Test Using Metasploit)[https://learning.oreilly.com/library/view/mastering-metasploit/9781838980078/B15076_01_Final_ASB_ePub.xhtml#_idParaDest-31]

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








# Lähteet
- Tero Karvinen, Tunkeutumistestaus, https://terokarvinen.com/tunkeutumistestaus/
-  Jaswal 2020: Mastering Metasploit - 4ed: Chapter 1: Approaching a Penetration Test Using Metasploit https://learning.oreilly.com/library/view/mastering-metasploit/9781838980078/B15076_01_Final_ASB_ePub.xhtml#_idParaDest-31


