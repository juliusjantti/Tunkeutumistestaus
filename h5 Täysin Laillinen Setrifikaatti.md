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

Tässä vaiheessa en tiennyt mitä tehdä joten päätin katsella muiden raportteja. 
[Rennen](https://github.com/RenneJ/tunkeutumistestaus/blob/main/h5-t%C3%A4ysin-laillinen-sertifikaatti.md) raportista löysinkin apua.

![](https://github.com/user-attachments/assets/d1176ea9-5fbc-484a-bc67-8462807ed0a4)

Kun voihtoi "Body" kohdasta "imagen" tilalle "text", salasanat tulivat näkyviin. Joten labi ratkaistu.

![](https://github.com/user-attachments/assets/2d9ad3a5-49fe-4fe4-b6ef-365cf42f6777)

e)

Sitten seuraavassa labissa pitäisi saada sama /etc/passwd tiedosto, mutta se ei olekkaan enää samalla polulla.

![](https://github.com/user-attachments/assets/51fde631-858c-4424-bba5-e8403d90fe36)


![](https://github.com/user-attachments/assets/e7fd257e-0257-45e0-82e7-9d6c732b90e2)

Kokeillaan samaa testiä kuin aikasemmassa kohtaa, mutta huomataan että tiedostoa ei löydy.

[Portswiggerin](https://portswigger.net/web-security/file-path-traversal) path traversal ojeissa kerrotaan että joskus voidaan käyttää absoluuttista polkua juureen.
Kokeillaan käyttää suoraa sijaintia, eikä polkua. Ja kappas sehän toimi heti.

![](https://github.com/user-attachments/assets/72e86730-22f8-4e69-bf36-bdf107cd4dd8)

![](https://github.com/user-attachments/assets/f1c88b25-1c56-4fe3-b28a-ca0d8c9a6920)
Labi suoritettu.


f)

Kolmannessa path traversal labissa sovellus poistaa pyynnöstä kaikki komennot joilla voitaisiin liikkua hakemistossa. 

Kokeillaan labissa ensin [portswiggerin](https://portswigger.net/web-security/file-path-traversal) sivuilta löytyvää koodausta `%2e%2e%2f` ja `%252e%252e%252f`

![](https://github.com/user-attachments/assets/d3ad51a3-6898-40ef-86de-b1a4071486c5)
![](https://github.com/user-attachments/assets/1364a6b9-91de-459b-a85b-fc0e3dbc8304)

Kumpikaan ei toiminut.

Tässä vaiheessa en ihan tiennyt mitä tehdä joten katsoin vinkkejä. Labin "solutions" kohdasta löytyikin suora vastaus. Pyyntöön piti lisätä `....//....//....//etc/passwd`. Ja näin saatiin taas salasanat. Olin näemmä katsonut väärää kohtaa ja hypännyt jo liian pitkälle. Eli tämä ratkaisu taisi liittyä jotenkin termiin "nested travel sequences". En ihan täysin ymmärtänyt ideaa. 

![](https://github.com/user-attachments/assets/d0765aac-4b24-4431-8bef-378cdcb449d4)
![](https://github.com/user-attachments/assets/2403ffb2-50a0-433f-946c-43b1c76ce585)

Labi suoritettu.

g) jätetään viimeiseksi

h)

Ohjeena oli käyttää varaston saldon määrän tarkistusta apuna ja poistaa käyttäjä "Carlos".

Kun tarkastaa saldon, huomaa että tämän tuotteen kohdalla vastaukseksi tulee 256.

![](https://github.com/user-attachments/assets/ef9379f7-423b-47d3-8db3-e55787046218)

Kun vaihtaa "stockApi" URLlän tilalle "http://localhost/admin", aukeaa hieman html koodia.

![](https://github.com/user-attachments/assets/a5fb9407-124b-4e3b-9fde-7c4a36059111)

Kun scrollailee html tekstiä alaspäin löytyy kohta jossa voi poistaa käyttäjän. Kopioidaan kyseinen kohta samaan URLlään johon laitettiin myös aikaisempi localhost URL, ja lähetetään pyyntö uudestaan.
 
![](https://github.com/user-attachments/assets/836fe364-286f-4ade-9674-bcc3568434c5)

Ja näin käyttäjä on poistettu ja lab on valmis.

![](https://github.com/user-attachments/assets/de7a622c-99b2-4310-9e52-2366e522bef6)

i)

Kokeillaan ensin hakusanan lähettämistä ja katotaan mitä zapissa löytyy.

![](https://github.com/user-attachments/assets/6eed151a-eb9a-4f60-93f1-847c32b226d7)

Ei löytynyt mitään kovin järkevää. Ohjeissa pyydettiin käynnistämään "alert" funktio mutta en ollut ihan varma miten se tehdään. Katsotaan siis vastaus.

Tässä labissa ei olisi tarvinnut zappia ollenkaan. Riitti kuin laittoi labin hakukenttään `<script>alert(1)</script>`. Eli tässä vissiin hakusanaksi voidaan laittaa jonkinlainen skripti, ja applikaatio ajaa kyseisen skriptin?


Labi suoritettu.

![](https://github.com/user-attachments/assets/9fe41f54-7883-4f53-82ac-a9ac91ab99fb)

j) 

Ohjeena oli suorittaa "alert" funktio kommentoimalla. Joten ajetaan edellisen tehtävän komento kommentissa.

![](https://github.com/user-attachments/assets/10054959-c69c-4b55-9446-afe711dfc1b5)

Näin labi oli taas suoritettu.

![](https://github.com/user-attachments/assets/c74cf60c-9b34-46bd-8964-130e822406fd)

Zapissa näkyi seuraavasti:

![](https://github.com/user-attachments/assets/5f89de40-40ad-45b3-80ac-b55e7291dbcf)

Analysointi jäi nyt hieman vähemmälle, sillä en aina täysin tajunnut tarkalleen mitä olin tekemässä.


k)

Ladataan [Pencode](https://github.com/ffuf/pencode). Kyseisellä sivulla ohjeistettiin asentamaan pencode GO:lla.

![](https://github.com/user-attachments/assets/0c7c66b8-4e58-4818-8bd7-4b1e42003562)

Itselläni sitä ei ole, joten asensin sen komennolla `sudo apt install gccgo-go`

![](https://github.com/user-attachments/assets/a81b956a-0010-4441-b663-40e5e6c799d2)

Pencoden github sivulla luki että pencoden voi asentaa komennolla `go install github.com/ffuf/pencode/cmd/pencode@latest`, joten ajetaan komento.

![](https://github.com/user-attachments/assets/e8283b5a-191e-4e09-a165-3427cbaf6d93)

Pencoden github sivulla oli seuraava ohje encodaamiseen, joten kokeillaan sitä.

![](https://github.com/user-attachments/assets/f8450b4f-9dc7-41c3-b5ea-82f0d478b28b)

Ajetaan komento `echo 'jeejee'|pencode hexencode`.

![](https://github.com/user-attachments/assets/a326f9f3-5384-40d8-96be-7b5c02915cac)

Eipä näyttänyt toimivan. Kokeillaanpa sitten ajaa ehdotettu komento `sudo apt install golang-github-fuff-pencode-dev`

![](https://github.com/user-attachments/assets/92f4cd6e-8055-4115-8eb3-d03cc1164a7c)

Ei napannut.

![](https://github.com/user-attachments/assets/7f9a9bbc-462e-4d62-ad16-4429cb3855d9)

Pencode ei näytä olevan sittenkään asentunut. Joten kokeillaan asennusta uudestaan. 

![](https://github.com/user-attachments/assets/ad2b555d-da1c-4ebe-936f-0fd839770309)

No nyt näyttäisi toimivan. KOkeillaas ajaa `echo 'jeejee'|pencode hexencode` uudestaan.

![](https://github.com/user-attachments/assets/d5813a0e-4391-47a7-98e9-b4570c1187ab)

Noniin nyt toimii! Encoodaus suoritettu. 









 



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
- Renne Jämsen, h5 Täysin Laillinen Sertifikaatti: https://github.com/RenneJ/tunkeutumistestaus/blob/main/h5-t%C3%A4ysin-laillinen-sertifikaatti.md
- ffuf, pencode: https://github.com/ffuf/pencode
- 
