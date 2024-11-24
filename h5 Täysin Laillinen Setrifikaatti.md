# Tehtävät

Tehtävät löytyvät [täältä](https://terokarvinen.com/tunkeutumistestaus/) kohdasta h4.

# Vastaukset

x) 

- Access Control pitää huolen ettei käyttäjät voi tehdä mitään mihin heillä ei ole valtuuksia. Monia AC sääntöjä voi kiertää jos ne ei ole konfiguroitu täydellisesti. AC tarkistuksia voi kiertää
  vaikka muuttamalla URLia, tai HTML sivua, tai käyttää työkalua jolla voi muokata API pyyntöjä.
  Väärinkäyttöä voi kuitenkin ennaltaehkäistä. Esimerkiksi kiellä implisiittisesti kaikki (implicit deny). Pidä lokia kaikista tapahtumista, sekä varmista että lokia ei voi muuttaa tai poistaa.
  
