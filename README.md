# RFID-Jukebox

Ik zag een artikel passeren over iemand die een kickstart project had nagebouwd.
Link: https://imgur.com/a/aiS5xp7
Ik had nog een Wemos D1 mini v3 liggen die nog geen bestemming had gekregen en een raspberry pi 3. Daarnaast had ik reeds een RFID module (MFRC522) met enkele tags.


Wat heb je nodig voor dit project (bijhorende links waar ik mijn materiaal kocht):

Wemos D1 mini v3: https://opencircuit.be/Product/WeMos-D1-mini-V3.1-Wifi-Module
NFC reader (headers moeten zelf gesoldeerd worden): https://opencircuit.be/Product/RC522-RFID-Reader-writer-module-kit-13.56MHz
Raspberry pi 3 (elke pi met ingebouwde wifi zou moeten werken): https://www.kiwi-electronics.nl/raspberry-pi-3-model-b-plus

NFC tags/stickers: kocht op alliexpress voor 1€ 10 NFC stickers (In België betaal je snel 15€ voor 10 stickers) Ik kocht er 50 in een keer en betaalde 5€ excl verzendkosten. (moet je wel een maand wachten).

Daarnaast heb ik zelf een 3D printer en designde dus de case, deksel met holte voor de schijfjes en aparte schijfjes in fusion360 (gratis voor hobbyisten ;-) . (zie stl's, alsook fusion files)

Nu we alles hebben kunnen we alles in elkaar prutsen. In bijgevoegde foto zie je hoe je de nfc reader verbind met je wemos D1. (pinnen heb ik niet aan de RFID gesoldeerd, wel aan de wemos D1. (eigen keuze :) ).

Nu alles verbonden is zijn we er nog niet.
Arduino kent ons boardje niet. Dus moeten we een link toevoegen dat hij deze kent. Dit doe je als volgt:
Klik op Bestand, Voorkeuren en plak bij volgende de link: Additionele boards beheer URL: http://arduino.esp8266.com/stable/package_esp8266com_index.json

Daarna kent hij ons bordje maar om de NFC module te gebruiken moeten we een bibliotheek installeren. Klik daarvoor op: Hulpmiddelen, Bibliotheken beheren. Zoek naar: MFRC522 en klik op Installeer.


Na wat zoeken stond zijn code op github: https://github.com/paulmassen/volumio-rfid-esp8266
Zijn code was onvolledig; na een test bleek al snel dat hij een kaart scant en zo een link stuurt naar Volumio. Dus als een tag bleef liggen speelde hij na 3 seconden het nummer opnieuw af. Met een "if" structuur is deze aangepast. Zodoende leest hij de tag en als deze tag net voordien al gescand is dan moet hij niks doen.
