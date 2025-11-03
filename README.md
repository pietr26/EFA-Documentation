# EFA-Documentation

>⚠️ Hinweis: Die Dokumentation befindet sich gerade in den ersten Entwürfen. Grundsätzlich kann sie schon verwendet werden, jedoch werde ich in den nächsten Tagen und Wochen wohl noch einiges umstrukturieren. ~03.11.2025

> Dokumentation hier ansehen: https://5desypxb3b.eu.apidog.com/

Diese API ist nicht die offizielle EFA-Webservice-API, sondern diejenige, die von der Webseite selbst verwendet wird – sie ist schneller, liefert mehr Daten und unterstützt statt exklusiv XML-Output auch jenen in JSON.

## Motivation

Die offizielle EFA-API ist zwar gut und ausführlich dokumentiert, liefert jedoch nur XML-Antworten und ist hinsichtlich der Detailtiefe der Daten ungenau. Nachdem ich mich mehrere Monate mit der offiziellen API, zufrieden mit der Detailtiefe und gequält durch den XML-Output, habe ich mich nach einer Alternative umgeschaut.

Beim Blick ins Netzwerkprotokoll auf efa.de fiel mir auf, dass die Webseite eine andere, interne API (folgend: IntAPI) nutzt.

Ziel dieses Projekts ist es, die IntAPI zugänglich und nachvollziehbar zu machen.

## Unterschiede zwischen der offiziellen API und der IntAPI

| Aspekt | Offizielle API | IntAPI |
| --- | --- | --- |
| Authentifizierung | [Beantragung eines Zugangs-Tokens](https://connect-fahrplanauskunft.de/datenbereitstellung#openservice) | frei zugänglich |
| Dokumentation | [Offiziell](https://www.vdv.de/431-2-sdsv1.2.pdfx) | nur inoffiziell - hier |
| Anfragelimit | 10000 pro Tag (pro Zugang) | keine Beschränkung bzw. unbekannt |
| Mögliche Detailtiefe der Anfrage | hoch | mittel - genügt für die meisten Anwendungsfälle, teilweise Zusatzparameter |
| Mögliche Detailtiefe der Antwort | mittel | sehr hoch |
| Ø Antwortzeit bei üblicher Verbindungsabfrage | 500-1000ms | 500-1000ms |

## Endpunkte / Dienste

Abgesehen von efa.de lassen sich auch andere EFA-Dienste auf die Dokumentation anwenden. Damit lassen sich für bestimmte Gebiete genauere Daten wie Echtzeitdaten oder Störungsmeldungen anzeigen.
> Achtung: Im Grundsatz lässt sich die Dokumentation auf alle Dienste anwenden. Allerdings ergeben sich in einigen Datenstrukturen durchaus weitere Properties, die ich noch nach und nach dokumentiere.

API | Endpoint | Gebietsabdeckung Echtzeitdaten und Störungsmeldungen | Einbindung in Dokumentation
| --- | --- | --- | --- |
| EFA-Allgemein (offiziell) | https://v4-api.efa.de/ | Hannover, Braunschweig, Hameln | nicht eingebunden |
| EFA-Allgemein (IntAPI) | https://efa.de/efa/ | Hannover, Braunschweig, Hameln | Fortgeschritten ([#1](pietr26/EFA-Documentation/issues/1)) |
| EFA-VRR | https://www.vrr.de/vrr-efa/ | Rhein-Ruhr | Ausstehend ([#3](pietr26/EFA-Documentation/issues/3)) |
| EFA-VVS | https://www3.vvs.de/mngvvs/ | Stuttgart | Ausstehend ([#4](pietr26/EFA-Documentation/issues/4)) |
| EFA-BW | https://www.bwegt.de/bwegt-efa/ | Baden-Württemberg | Ausstehend ([#5](pietr26/EFA-Documentation/issues/5)) |

In der Dokumentation ist stets der Endpunkt der allgemeinen IntAPI angegeben, kann aber 1:1 durch eine der o.g. Alternativen (bis auf die offizielle API) ersetzt werden.

## Disclaimer

Ich oder dieses Projekt steht in keiner Verbindung zu den Betreibern von efa.de oder anderen EFA-basierten Diensten.

Die hier dokumentierte Schnittstelle ist nicht offiziell dokumentiert oder freigegeben und kann sich jederzeit ändern.
Die Informationen wurden ausschließlich durch die Analyse öffentlich zugänglicher Netzwerkrequests der Webseiten gewonnen.

Nutzung auf eigene Verantwortung.

## Mitmachen

Issues sind willkommen! - Pull Requests eher weniger, da sich hier auf GitHub nur der Export von Apidog befindet und ich dann ständig Re-Imports durchführen müsste.
- Fehlende Parameter oder Felder dokumentieren
- Weitere EFA-Dienste hinzufügen
- Abweichungen zwischen Regionen analysieren
- ...
