# fellow-finder-data

`meetings.json` — de meetinglijsten van NA, AA en CA Nederland, elke nacht
opgehaald en samengevoegd tot één bestand.

Deze repo bevat alleen data. Een script schrijft hem, een app leest hem. Er
wordt hier niet met de hand aan gewerkt.

## Dit is niet officieel

Dit is geen uitgave van Narcotics Anonymous, Alcoholics Anonymous of Cocaine
Anonymous, en het is door geen van hen goedgekeurd of gecontroleerd. Het is
overgetypt werk van een enkeling: een script dat hun openbare meetinglijsten
ophaalt en netter opschrijft. Geen van deze fellowships is bij dit project
betrokken en niets hier spreekt namens hen.

**Ga voor de waarheid altijd naar de bron.** Als deze data en de site van de
fellowship van elkaar verschillen, heeft de fellowship gelijk:

- [nanederland.nl](https://www.nanederland.nl)
- [aa-nederland.nl](https://aa-nederland.nl)
- [ca-holland.nl](https://ca-holland.nl)

## Wat er in staat

Alleen wat die drie sites zelf al openbaar publiceren: naam van de groep, dag,
tijd, locatie, coördinaten, of het online is, en het type meeting. Geen mensen,
geen persoonsgegevens, geen namen van deelnemers — die staan ook niet in de
bron.

    {
      "generated": "2026-07-16T03:12:00.000Z",   // wanneer opgehaald, niet wanneer gewijzigd
      "timezone": "Europe/Amsterdam",
      "count": 943,
      "programs": ["NA", "AA", "CA"],
      "meetings": [
        {
          "id": "NA:just-for-today",
          "program": "NA",              // NA | AA | CA
          "name": "Just For Today",
          "day": 1,                     // 0 = zondag
          "time": "20:00",
          "endTime": "21:30",           // 90 minuten als de bron er geen geeft
          "timezone": "Europe/Amsterdam",
          "location": "Buurthuis De Meeuw",
          "address": "Kanaalstraat 12",  // null bij een online meeting
          "city": "Amsterdam",           // null bij een online meeting
          "postalCode": "1054 XL",       // null als de bron er geen geeft
          "region": "Noord-Holland",     // de provincie, niet de plaats
          "lat": 52.366,                 // null bij online of als de bron ze mist
          "lng": 4.86,
          "types": ["O"],               // O open · C besloten · ONL online · W vrouwen · M mannen
          "lang": "nl",                  // "nl" | "en" | "pl" | "ru" | null
          "isOnline": false,
          "conferenceUrl": null,         // gevuld bij online/hybride, anders null
          "conferencePhone": null,
          "notes": null,                 // vrije tekst van de groep, of null
          "locationNotes": null,         // extra uitleg over de plek, of null
          "url": "https://www.nanederland.nl/meetings/just-for-today/",
          "updated": "2026-07-13 14:48:49"
        }
      ]
    }

`generated` betekent **wanneer de feeds voor het laatst zijn opgehaald**, niet
wanneer er iets veranderde. Er komt elke nacht een commit, ook in een rustige
week. Zo is een stille periode te onderscheiden van een kapotte build.

Online meetings hebben `lat` en `lng` op `null`. De bronnen geven daar een
benaderde locatie (meestal het midden van het land), en dat is geen plek — daar
kun je niet naartoe fietsen.

## Bekende gaten

Zitten in de bron, niet in het script: een paar meetings missen coördinaten of
een eindtijd. Zevenaar valt daardoor helemaal weg uit de plaatsindex; de enige
meeting daar heeft geen coördinaten.

## Gebruik

Vrij te gebruiken. Het is niet van mij — het is van de fellowships, en die
publiceren het zelf al. Wil je het ophalen:

    https://raw.githubusercontent.com/jeroenrosier/fellow-finder-data/main/meetings.json

Doe het hooguit een keer per dag; vaker heeft geen zin, want het verandert maar
één keer per nacht. En cache het aan jouw kant, zodat het ook werkt als je
offline bent.
