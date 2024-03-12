# TINNES-1 MQTT Chat App | Opdracht 1

<!-- ![image](https://github.com/wouterbt/RAAST/assets/122525080/1e40cedc-decd-4140-b17d-294f334cf25b) -->
<img src="https://github.com/ThomasvanEgmond/TINNES-1-Opdracht-1/blob/main/image.png" width="570">

Opdracht 1 voor `Netwerken en Security vervolg` is een MQTT chat app maken. Deze app maakt gebruikt van een centrale  MQTT broker en een webserver voor de front-end, beide moeten draaien in een docker container.

Echter kwam ik erachter dat in de MQTT broker [`Mosquitto`](https://mosquitto.org/) een ingebouwde webserver zat. Mosquitto serveert op dezelfde poort zowel de MQTT broker als de front-end webpagina.

Vanwege de vermindering in configuratie en installatie werk is dit voor deze simpele applicatie een voordeel. Voor groot schaliger gebruik van een MQTT broker (of een andere back-end) is het handiger om de webserver apart te laten draaien van de MQTT broker.


## Installatie

#### Installeer de recenste versie van docker voor jouw besturingsysteem hier.
https://docs.docker.com/get-docker/

#### Download de laatse versie van de applicatie als `.zip` van de GitHub repository
 https://github.com/ThomasvanEgmond/TINNES-1-Opdracht-1

Extraheer het `.zip` bestand naar een folder, hier noem ik hem `TINNES-1-Opdracht-1`.

#### Open een terminal in de root van de zojuist aangemaakte folder, je terminal directory lijkt dus op het volgende.
```
PS C:\Users\tvane\Desktop\School\Jaar 2\Netwerk vervolg\TINNES-1-Opdracht-1>
```
Controleer of `docker-compose.yaml` in je directory zit met het  `dir` commando.

#### In je terminal draai je het volgende commando

```
docker compose -f docker-compose.yaml up -d --build
```

Klaar! Je website is te bereiken via de URL [`localhost`](https://localhost).

**Je moet nog wel even wat gebruikers toevoegen om in te kunnen loggen!**

## Applicatie gebruiken

#### Gebruikers kunnen worden toegevoegd in een normale terminal met het volgende commando, negeer de warning.

```
docker exec Mosquitto-TINNES-1 mosquitto_passwd -b /mosquitto/passwd/password_file <username> <password>
```

Na het toevoegen van een gebruiker moet de docker container opnieuw worden opgestart.
```
docker restart Mosquitto-TINNES-1
```

De volgende gebruikers zijn standaard toegevoegd. 

**Inloggegevens zijn hoofdletter gevoelig!**
```
<username> <password>
[Steven] [Slaa]
[Alex] [Slaa]
[Nanne] [Verheij]
```

Veel chat plezier!

## ChatGPT
Het is bijna niet meer te vermijden maar ik ben persoonlijk geen fan van het gemak dat ChatGPT brengt. Aangezien het in mijn ogen wegneemt van leermomenten.

Om die reden heb ik de applicatie zonder ChatGPT gemaakt maar het moet er tuurlijk wel een beetje leuk uitzien. Nu ben ik geen CMD'er dus om het wat mooiere CSS gedeelte te krijgen heb ik wat van ChatGPT gestolen.

De barebones versie van de applicatie is ook meegeleverd en draait op [`localhost/barebones.html`](https://localhost/barebones.html). Deze heeft dezelfde functionaliteit, is iets minder mooi maar wel zonder AI gemaakt.
