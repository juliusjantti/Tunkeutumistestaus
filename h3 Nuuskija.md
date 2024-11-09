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




# Lähteet

- Karvinen Tero, Find Hidden Web Directories - Fuzz URLs with ffuf: https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/
- Hacktricks, Wireshark tricks: https://terokarvinen.com/2023/fuzz-urls-find-hidden-directories/
- Karvinen Tero, Tunkeutumistestaus-kurssi: https://terokarvinen.com/tunkeutumistestaus/
