# Tehtävät

Tehtävät löytyvät [täältä](https://terokarvinen.com/tunkeutumistestaus/) kohdasta h5.

# Vastaukset

x) Lue ja Tiivistä

- Access Control pitää huolen ettei käyttäjät voi tehdä mitään mihin heillä ei ole valtuuksia. Monia AC sääntöjä voi kiertää jos ne ei ole konfiguroitu täydellisesti. AC tarkistuksia voi kiertää vaikka muuttamalla URLia, tai HTML sivua, tai käyttää työkalua jolla voi muokata API pyyntöjä. Lisäksi metadataa voi muokata.
  Väärinkäyttöä voi kuitenkin ennaltaehkäistä. Esimerkiksi kiellä implisiittisesti kaikki (implicit deny). Pidä lokia kaikista tapahtumista, sekä varmista että lokia ei voi muuttaa tai poistaa. Server Side Request Forgery (SSRF) on toiminto jossa webbiapplikaatio tekee käyttäkälle pyyntöjä varmistamatta käyttäjän URL:lää. TÄmän avulla hökkääjä voi manipuloida applikaatiota tekemään pyyntöjä paikoista minne ei pitäisi päästä käsiksi. Esimerkiksi tulimuurin tai ACn taakse.

- IDOR on haavoittuvuus jossa hyökkääjä voi käyttää järjestelmän suoria viittauksia (kuten ID-tunnuksia) ilman riittävää käyttöoikeuksien tarkastusta.
- Path Traversal on tietoturvahaavoittuvuus, jossa hyökkääjä manipuloi sovelluksen tiedostopolkuja päästäkseen käsiksi tiedostoihin tai hakemistoihin, jotka ovat normaalisti suojattuja. Tämä tapahtuu usein hyödyntämällä erityismerkkejä, kuten ../, joiden avulla voidaan navigoida tiedostojärjestelmässä sovelluksen sallitun käyttöalueen ulkopuolelle.
- Server-Side Template Injection on haavoittuvuus, jossa hyökkääjä pystyy syöttämään haitallista sisältöä sovelluksen mallipohjaan (template), jota palvelin käsittelee ja suorittaa
- Cross-Site Scripting (XSS) on haavoittuvuus, jossa hyökkääjä pystyy upottamaan haitallista JavaScript-koodia verkkosovellukseen siten, että se suoritetaan muiden käyttäjien selaimissa. Tämä voi johtaa esimerkiksi käyttäjätietojen, kuten evästeiden, varastamiseen tai haitallisten toimien suorittamiseen käyttäjän puolesta.

Tiivistämiseen ja lukemisen ymmärtämiseen käytetty apuna tekoälyä.


a) / b)

 Zap asennettiin jo tunnilla jote sen asennuksesta ei ole kuvia. Asensin [Zapin](https://www.zaproxy.org/download/) sivuilta "Cross Platform Packagen" omaan virtuaalikoneeseeni, sekä purin tiedoston. 
![](https://github.com/user-attachments/assets/e61892b7-6c77-4458-ae4e-fba55c211e03)
Zap lähti käyntiin komennolla `java -jar zap-2.15.0.jar`
![](https://github.com/user-attachments/assets/139c3699-2ea3-4f6d-8b8c-dbb59ba75d13)
Zappi toimii.

Luodaan ZAPissa sertificaatti ja ladataan se koneelle.
![](https://github.com/user-attachments/assets/221fc053-c7a4-4211-b12e-d52e2c38167d)
![](https://github.com/user-attachments/assets/43ad774d-c4fa-4dfc-9d85-bc8dd156b483)

FoxyProxykin ehdittiin ladata jo tunnilla.
![](https://github.com/user-attachments/assets/1af776b4-840d-414a-a336-665b9b121eed)

Laitetaan ZAPista importattu sertifikaatti firefoxiin. Mennään > settings > privacy and security > Certificates ja view certificates > importataan sertifikaatti sinne.
![](https://github.com/user-attachments/assets/514e1625-faad-4ec4-aec3-c2e1e80e98ce)
![](https://github.com/user-attachments/assets/38d10e82-ac56-4a23-b138-4a3d42759caa)

Sitten yhdistetään ZAP ja foxyproxy. Localhost ip osoitteeseen sekä portti 8080.
![](https://github.com/user-attachments/assets/8c663471-fcb7-41ce-9d9f-d525f7784a8e)

![](https://github.com/user-attachments/assets/3885d1df-9c8f-42d9-b152-fd13157e9ac0)
Näin pyynnöt näkyvät myös ZAPissa.

Sitten yritettiin muokata FoxyProxin patterns toimintoa siten että vain tietyn sivun liikennettä napataan. Whitelistattiin portswiggerin nettisivut.

![](https://github.com/user-attachments/assets/8fbd84bb-c8a8-46c6-b6d6-b815e0d01326)

Ja sitten kokeiltiin mennä is.fi, ja katsottiin näkyikö ZAPissa liikennettä. 
![](https://github.com/user-attachments/assets/2d4dd873-c462-49e2-a2b6-5374759af346)
Eipä näyttänyt onnistuvan. Foxyproxy jota käytän näyttää hieman erilaiselta kuin tunnilla käytetty versio. Joten en ollut täysin varma mistä tämä patterns otettiin käyttöön. En lopulta saanut toimimaan patternsia siten että se kaappaisi liikenteen vain tietyiltä sivuilta.

c) 

Yritetään suorittaa ensimmäinen labi "Lab: Insecure direct object references"

Zapin käytössä on hieman ongelmia mutta koitetaan silti ratkaista labi. Ohjeissa sanottiin että kun labissa menee chattaamaan, voi ladata chatin transcriptin. Zapin avulla voi muokata urlia hakemaan juuri tietyn transcriptin. Ja juuri "1.txt" transcriptia hakemalla saa selvitetyksi salasanan. 

Joten muokataan GET pyyntöä ja laitetaan siihen 1.txt. Oikealla alhaalla kuvassa näkyy salasana.

![](https://github.com/user-attachments/assets/583f8141-c2a3-4a0c-b0df-7be6c99f34ec)

Käytetään kyseistä salasanaa ja kirjaudutaan sisään käyttäjänä "Carlos"

![](https://github.com/user-attachments/assets/3432afde-9456-40c8-a323-3cd4dcb490df)

Ja labi saatiin ratkaistua.

d)

Kun avataan labi ja mennään labissa tietyn kuvan kohdalle, huomataan ZAPissa että kuvaa haetaan.

![](https://github.com/user-attachments/assets/fe49e048-4052-40d9-a1c7-c87d48ce28d5)

Tiedetään että pyyntöä joka hakee kuvan, voidaan muokata joten muokataan pyyntöä hakemaan meille /etc/passwd tiedoston sisällön. 

![](https://github.com/user-attachments/assets/435b5a72-4aac-4524-a939-ce7046303e53)

Tämä ei kuitenkaan toiminut, sillä vastauksena ei tullut mitään. 

![](https://github.com/user-attachments/assets/341f6712-a2f7-410c-a361-968e7bab07da)






 



# Lähteet
- Tero Karvinen, Tunkeutumistestaus kurssi: https://terokarvinen.com/tunkeutumistestaus/
- Portswigger academy, What is XSS; https://portswigger.net/web-security/cross-site-scripting
- Portswigger academy, What isInsecure Direct Object Refrences: https://portswigger.net/web-security/access-control/idor
- Portswigger academy, What is Path traversal: https://portswigger.net/web-security/file-path-traversal
- Portswigger academy, What is Server Side Template Injection: https://portswigger.net/web-security/server-side-template-injection
- Portswigger academy, What is Server Side Request Forgery: https://portswigger.net/web-security/ssrf
- Owasp 10:2021, Broken Access Control: https://owasp.org/Top10/A01_2021-Broken_Access_Control/
- Owasp 10:2021, Server Side Request Forgery: https://owasp.org/Top10/A10_2021-Server-Side_Request_Forgery_%28SSRF%29/
- Zaproxy, Download Zap: https://www.zaproxy.org/download/
- FoxyProxy, Url Patterns: https://help.getfoxyproxy.org/index.php/knowledge-base/url-patterns/
