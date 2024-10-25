  # Sanoma Haaviin

  a) Sieppaa ja analysoi verkkoliikennettä. Tee raportista sivu weppiin. Palauta linkki Laksuun ja ristiinarvioi vähintään kaksi.


## a) Vastaus
Ladataan ensimmäiseksi [Wireshark](https://www.wireshark.org/) ohjelma. Omassa tapauksessa Mac Os Intel Disk Image. Asennetaan kyseinen ohjelma tietokoneelle asennusohjeiden mukaisesti. 

Nopealla googlailulla löytyi sivu [kaspersky](https://support.kaspersky.com/common/macos/15325), jonka ohjeita seuraamalla voidaan kapturoida paketteja. Ohjeita seuraamalla kaapataan muutama paketti. Alla kuva kaapatusta liikenteestä.



![Kaapattu liikenne](https://github.com/user-attachments/assets/1b80df87-bfb5-47ac-b03f-d40f1bccd7c7)

**Analysoidaan yhtä TCP pakettia (kuvassa ruskealla maalattu paketti)**

Kohdassa *N0.* lukee missä järjestyksessä paketti on otettu kiinni. Tämä paketti on 44. paketti. 

Kohdassa *Time* näkyy kuinka kauan pakettien kaappaamisen aloittamisesta on kulunut kuin tämä paketti kaapattiin.

Kohdassa *Source* näkyy lähde IP-osoite. Tässä kuvassa se on 10.213.107.23.

Kohdassa *Destination* näkyy kohde IP-osoite. Tässä kuvassa se on 34.203.175.187.

Kohdassa *Protocol* näkyy paketin tyyppi. Tässä vaiheessa se on TCP.

Kohdassa *Length* näkyy paketin pituus. Tässä vaiheessa se on 66 tavua.

Kohdassa *Info* näkyy lisätietoa paketista.








  # Lähteet
  - Wireshark, https://www.wireshark.org/
  - Markdown Cheat Sheet, https://www.markdownguide.org/cheat-sheet/
  - Varonis, How to use wireshark: Comprehensive tutorial, https://www.varonis.com/blog/how-to-use-wireshark#packets
  - Tero Karvinen, Tunkeutumistestaus kurssi, https://terokarvinen.com/tunkeutumistestaus/
  - Tero Karvinen, Create a web bage using Github, https://terokarvinen.com/2023/create-a-web-page-using-github/
