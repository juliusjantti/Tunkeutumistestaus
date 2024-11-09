# Tehtävät

x) Lue ja tiivistä. Muutama ranskalainen viiva riittää.
  - [Popov 2024: Hacktricks: Wireshark tricks](https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/pcap-inspection/wireshark-tricks#improve-your-wireshark-skills)
  - [Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/)

a) Valitse valmis hyökkäys. Ota sellainen hyökkäys, jonka saat toimimaan omaan paikalliseen harjoitusmaaliin, kuten Metasploitableen. Demonstroi hyökkäyksen toiminta.
  - Normaali vaihtoehto: Ota hyökkäys Metasploitista (muu kuin vsftpd backdoor).
  - Helpotettu vaihtoehto: Tunnilla käyty vsftpd backdoor Metasploitista.
  - Vaikea vaihtoehto: Ota hyökkäys exploitdb:sta ('searchsploit').
    
b) Sorsa. Selitä ja arvioi valitsemasi hyökkäyksen toimintaa lähdekoodista.

c) Snif snif. Selitä ja arvioi valitsemasi hyökkäyksen toimintaa verkkosnifferillä. Pohdi myös, miten näkyvä tämä hyökkäys tai kontrollikanava on verkossa. (Vapaaehtoinen bonus: liitä mukaan pcap tekemästäsi nauhoituksesta).

d) Fuzzzz. Ratkaise dirfuz-1 artikkelista Karvinen 2023: Find Hidden Web Directories - Fuzz URLs with ffuf.

d) HTB. Ratkaise 1-2 konetta HackTheBoxisssa. Voit valita omaan taitotasoon sopivat koneet. "Starting point" ovat helppoja.

e) Vapaaehtoinen, helppo: Vaihda 'micro' Metasploitin oletuseditoriksi. Sille on oma 'setg' asetus.


# Vastaukset

x) 

- Paljon vinkkejä Wiresharkin käyttöön. Kuinka nähdä käytetyt protocollat, osoitteet, DNS-tiedot.
- Kuinka hyödyntää Fluffia piilotettujen hakemistojen löytämiseen. Käydään läpi ohjeet miten Fluffia käytetään maalikohteeseen. Kohteen on luonut Tero Karvinen, ja sen voi ladata sivulta suoraan.

a) 

Otetaan tässä vaiheessa helpotettu vaihtoehto, eli VSFTPD, sillä tällä viikolla ei ole kauheasti aikaa tehdä läksyjä. Ja lisäksi viimetunnilla meni huomattavan paljon aikaa Kalin ongelmien korjaamiseen, joten en ehtinyt tunnilla tutkia hyökkäyksen toimintaa verkkosnifferillä. Toteutetaan hyökkäys samalla tavalla kuin viime viikon [läksyissä](https://github.com/juliusjantti/Tunkeutumistestaus/blob/main/h2%20Social%20Sploit.md) (Löytyy kohdasta g).

b) 

VSFTPD lähdedkoodi.
![](https://github.com/user-attachments/assets/7c89056b-2f02-4d49-8508-fc0c39329ad8)
Sieltä löytyi ainakin portti johon hyökätään. 


c)

Kokeillaan ensin toimiiko wireshark normaalisti. Alla kaapattu ensin pelkästään maalikoneen pingausta.

![](https://github.com/user-attachments/assets/76c6624d-36d5-45c9-8ee7-759caa6d7066)

Hyökkäus ja hyökkäyksen sniffaus on suoritettu virtuaaliympäristössä Kalin ja Metasploitablen välillä, joten mitään oikean maailman liikennettä ei näy.

Suoritetaan hyökkäys ja annetaan Wiresharkin seurata liikennettä hyökkäyksen ajan. 

![](https://github.com/user-attachments/assets/63ed2a50-8800-46b9-b677-934eb4734ae3)
Tietoa tuli aika paljon.

En nyt ole täysin varma mistä mitäkin löytyy, ja mitä tästä pitäisi etsiä.

Paketteja tutkailemalla löytyi ainakin seuraava kohta:
![](https://github.com/user-attachments/assets/71e3cc22-4efd-456b-a8af-42c60bc051c3)
Tästä puhuttiin tunnilla jotain. Mukana on hymynaama joka oli tärkeässä osassa [hyökkäystä](https://docs.rapid7.com/metasploit/metasploitable-2-exploitability-guide/). 

![](https://github.com/user-attachments/assets/f461d2b8-d003-4bd3-a140-edaf22d35b69)
Koneiden osoitteet löytyy.

![](https://github.com/user-attachments/assets/37d11fd8-ca69-4eac-8b7b-7caf35bb4c82)
Loppupäästä löytyi osia metasploitablen shellistä.

d)

Seurataan [Teron](https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/) kirjoittamia ohjeita miten ratkaista "dirfuz-1".

![](https://github.com/user-attachments/assets/9e0e7c62-5caf-4b3c-8f7f-6dc5a71146d6)
![](https://github.com/user-attachments/assets/9900a930-1fa6-4771-89d8-42a9fa2bbf6f)

Tämän jälkeen asennetaan ffuf ohjeiden mukaisesti. 
Ja sitten ladataan tiedosto jossa on hakemistojen nimiä.

![](https://github.com/user-attachments/assets/fce8e045-d45a-4102-a4d3-894e350cf41b)

Varmistetaan taas että kone ei ole netissä kiinni. 

![](https://github.com/user-attachments/assets/e8ae5add-7f44-41d7-8ee4-1737bb85b82e)

Sitten kokeillaan fuzzaamista.

![](https://github.com/user-attachments/assets/50b3de0a-c838-43d6-a401-722f89a75d49)
Ensin tuli kokeiltua aika monta hakemistovaihtoehtoa, mutta lopulta ohjeiden avulla saatiin rajattua se kahteen. 

![](https://github.com/user-attachments/assets/0aafdf6d-eeaa-4495-b76d-269727063014)
Lopuksi oikea hakemisto löytyi. Se oli /admin. 





















# Lähteet

- Karvinen Tero, Find Hidden Web Directories - Fuzz URLs with ffuf: https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/
- Hacktricks, Wireshark tricks: https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/
- Karvinen Tero, Tunkeutumistestaus-kurssi: https://terokarvinen.com/tunkeutumistestaus/
- Rapid7, Metasploitable 2 Exploitability guide: https://docs.rapid7.com/metasploit/metasploitable-2-exploitability-guide/