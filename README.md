# RFID-Jukebox

Ik zag een artikel passeren over iemand die een kickstart project had nagebouwd.
Link: https://imgur.com/a/aiS5xp7
Ik had nog een Wemos D1 mini v3 liggen die nog geen bestemming had gekregen en een raspberry pi 3. Daarnaast had ik reeds een RFID module (MFRC522) met enkele tags.

Na wat zoeken stond zijn code op github: https://github.com/paulmassen/volumio-rfid-esp8266
Zijn code was onvolledig; na een test bleek al snel dat hij een kaart scant en zo een link stuurt naar Volumio. Dus als een tag bleef liggen speelde hij na 3 seconden het nummer opnieuw af. Met een "if" structuur is deze aangepast. Zodoende leest hij de tag en als deze tag net voordien al gescand is dan moet hij niks doen.



Wat heb je nodig voor dit project (bijhorende links waar ik mijn materiaal kocht):

Wemos D1 mini v3: https://opencircuit.be/Product/WeMos-D1-mini-V3.1-Wifi-Module</br>
NFC reader (headers moeten zelf gesoldeerd worden): https://opencircuit.be/Product/RC522-RFID-Reader-writer-module-kit-13.56MHz</br>
Raspberry pi 3 (elke pi met ingebouwde wifi zou moeten werken): https://www.kiwi-electronics.nl/raspberry-pi-3-model-b-plus</br>
HDMI naar VGA adapter: kost 5€ in de action. We gebruiken deze om de audio jack die achteraan de vga poort zit te gebruiken en zo mooie kwaliteit als output te krijgen.</br>
NFC tags/stickers: kocht op alliexpress voor 1€ 10 NFC stickers (In België betaal je snel 15€ voor 10 stickers) Ik kocht er 50 in een keer en betaalde 5€ excl verzendkosten. (moet je wel een maand wachten).

Daarnaast heb ik zelf een 3D printer en designde dus de case, deksel met holte voor de schijfjes en aparte schijfjes in fusion360 (gratis voor hobbyisten ;-) . (zie stl's, alsook fusion files)

Nu we alles hebben kunnen we alles in elkaar prutsen. In bijgevoegde foto zie je hoe je de nfc reader verbind met je wemos D1. (pinnen heb ik niet aan de RFID gesoldeerd, wel aan de wemos D1. (eigen keuze :) ).

Nu alles verbonden is zijn we er nog niet. Open het .ino bestand in de ARDUINO IDE.
Arduino kent ons boardje niet. Dus moeten we een link toevoegen dat hij deze kent. Dit doe je als volgt:
Klik op Bestand, Voorkeuren en plak bij volgende de link: Additionele boards beheer URL: http://arduino.esp8266.com/stable/package_esp8266com_index.json

Daarna kent hij ons bordje maar om de NFC module te gebruiken moeten we een bibliotheek installeren. Klik daarvoor op: Hulpmiddelen, Bibliotheken beheren. Zoek naar: MFRC522 en klik op Installeer.

Daarna selecteer je bij Boards: Wemos D1 mini pro V3. en bij poorten de juist COM.

Extra info: Als Volumio met geen wifi-netwerk verbonden is dan maakt hij een eigen hotspot aan. Deze Heet Volumio en gebruiken we.
Wachtwoord verander je in de volumio settings. Deze vind je door met de hotspot te verbinden en in je browser naar: volumio.local te surfen.

Als alles is aangesloten open je het bestand: DumpInfo.ino, dit vind je hierbij of onder: Voorbeelden, MFRC522, Dumpinfo.
Verander SSPin naar D8 ipv 10 en upload naar je bord. Ga naar Hulpmiddelen en open de seriele poort. Controleer dat hij zeker op 9600 Baud staat. Scan je tag en kopieer ergens de Tag UID (vb Kladblok).

Nu open je de RFID met volumio.ino. Je plakt je tag onder clients tag. (verander deze met jou gescande UID).
Daaronder verander je de url naar jou afspeellijst (leg ik uit onder het onderdeel Volumio)
Daarna uploaden naar je board (vergeet je poort niet te selecteren!)



Volumio

Volumio flashen op je sd kaart doe je via win32DiskImager. Dit leg ik niet verder uit. Hiervan vind je veel tutorials op internet. zoek onder: img naar sd kaart flashen.

Verbindt via wifi op je pc met Volumio. Wachtwoord: Volumio. Surf naar http://volumio.local

Als je volumio voor de eerste keer start stelt hij wat vragen. Belangrijk is dat je HDMI als default selecteert en niet de audio jack. De raspberry pi's audio jack heeft geen versterker dus produceert ruis. Via HDMI kan je dan achteraan de adapter je jack insteken.

Nu alles van geluid in orde is moeten we afspeellijsten maken. Kort uitgelegd: De wemos stuurt een link naar een afspeellijst die in volumio staat. Je gaat dus naar muziekbibliotheek en steekt een usb stick in met muziek of muziek die op de sd kaart staat (leg ik zo meteen uit hoe je er op zet). Klik op de 3 puntjes naast een mapje en klik op toevoegen aan afspeellijst. Geef een naam en klik op Nieuw.


Muziek overzetten vanop je pc:
Open een verkenner en typ in de url: \\volumio.local
Nu kan je muziek in de Internal storage slepen en vind je terug in je Muziekbibliotheek.


Vul de naam van je afspeellijst in de plaats van mijn afspeellijstnamen met enkele regels daarboven je tagnummer. Vergeet niet: een spatie tussen je afspeellijst doe je weg en vul je %20 in. (zie in mijn namen van afspeellijsten in het bestand).
Je kan in de instellingen je wachtwoord voor je persoonlijke hotspot aanpassen.


Nu hoef je zelf nog je foto's te maken. (mijn breedte van fotos was 2.7cm om zo te passen. Veel prutswerk om deze mooi op het schijfje te krijgen. Op de achterkant plak je dan je nfc sticker. Mooiste kwaliteit is printen op fotopapier (mat zodat de vingerafdrukken er niet aanplakken).

Vergeet geen play en pauze schijfje! :-)

Succes en veel plezier!
