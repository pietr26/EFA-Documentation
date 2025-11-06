# Dokumentation der internen EFA-API

> ⚠️ Hinweis: Die Dokumentation befindet sich gerade in den ersten Entwürfen. Grundsätzlich kann sie schon verwendet werden, jedoch werde ich in den nächsten Tagen und Wochen wohl noch einiges umstrukturieren. ~03.11.2025

Diese API ist nicht die offizielle EFA-Webservice-API, sondern diejenige, die von der Webseite selbst verwendet wird – sie ist schneller, liefert mehr Daten und unterstützt statt exklusiv XML-Output auch jenen in JSON.

## Motivation
Die offizielle EFA-API ist zwar gut und ausführlich dokumentiert, liefert jedoch nur XML-Antworten und ist hinsichtlich der Detailtiefe der Daten ungenau. Nachdem ich mich mehrere Monate mit der offiziellen API, zufrieden mit der Detailtiefe und gequält durch den XML-Output, habe ich mich nach einer Alternative umgeschaut.

Beim Blick ins Netzwerkprotokoll auf efa.de fiel mir auf, dass die Webseite eine andere, interne API (folgend: IntAPI) nutzt.

Ziel dieses Projekts ist es, die IntAPI zugänglich und nachvollziehbar zu machen.

## Unterschiede zwischen der offiziellen API und der IntAPI
<table>
  <tr>
    <th>Aspekt</th>
    <th>Offizielle API</th>
    <th>IntAPI</th>
  </tr>
  <tr>
    <td>Authentifizierung</td>
    <td><a href="https://connect-fahrplanauskunft.de/datenbereitstellung#openservice" target="_blank">Beantragung eines Zugangs-Tokens</a></td>
    <td>frei zugänglich</td>
  </tr>
  <tr>
    <td>Dokumentation</td>
    <td><a href="https://www.vdv.de/431-2-sdsv1.2.pdfx" target="_blank">Offiziell</a></td>
    <td>nur inoffiziell - hier</td>
  </tr>
  <tr>
    <td>Anfragelimit</td>
    <td>10000 pro Tag (pro Zugang)</td>
    <td>keine Beschränkung bzw. unbekannt</td>
  </tr>
  <tr>
    <td>Mögliche Detailtiefe der Anfrage</td>
    <td>hoch</td>
    <td>(mindestens) mittel<br><sup>tw. exklusive Parameter</sup></td>
  </tr>
  <tr>
    <td>Mögliche Detailtiefe der Antwort</td>
    <td>mittel</td>
    <td>sehr hoch</td>
  </tr>
  <tr>
    <td>Ø Antwortzeit bei Verbindungsabfrage</td>
    <td colspan="2" align="center">500-1000ms (tageszeitabhängig)</td>
  </tr>
</table>

## Endpunkte / Dienste
Abgesehen von efa.de lassen sich auch andere EFA-Dienste auf die Dokumentation anwenden. Damit lassen sich für bestimmte Gebiete genauere Daten wie Echtzeitdaten oder Störungsmeldungen anzeigen.
> Achtung: Im Grundsatz lässt sich die Dokumentation auf alle Dienste anwenden. Allerdings ergeben sich in einigen Datenstrukturen durchaus weitere Properties, die ich noch nach und nach dokumentiere.

<table>
  <tr>
    <th>API</th>
    <th>URL</th>
    <th>Abdeckung Fahrplandaten</th>
    <th>Abdeckung Echtzeitdaten & Störungsmeldungen</th>
    <th>Einbindung in Dokumentation</th>
  </tr>
  <tr>
    <td>EFA-Allgemein (offiziell)</td>
    <td>https://v4-api.efa.de/</td>
    <td>gesamt Deutschland</td>
    <td>Hannover, Braunschweig, Hameln</td>
    <td>nicht eingebunden</td>
  </tr>
  <tr>
    <td>EFA-Allgemein (IntAPI)</td>
    <td>https://efa.de/efa/</td>
    <td>gesamt Deutschland</td>
    <td>Hannover, Braunschweig, Hameln</td>
    <td><img src="https://geps.dev/progress/80" alt="80% Fortschritt"> (<a href="https://github.com/pietr26/EFA-Documentation/issues/1">#1</a>)</td>
  </tr>
  <tr>
    <td>EFA-VRR</td>
    <td>https://www.vrr.de/vrr-efa/</td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0" alt="0% Fortschritt"> (<a href="https://github.com/pietr26/EFA-Documentation/issues/3">#3</a>)</td>
  </tr>
  <tr>
    <td>EFA-VVS</td>
    <td>https://www3.vvs.de/mngvvs/</td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0" alt="0% Fortschritt"> (<a href="https://github.com/pietr26/EFA-Documentation/issues/4">#4</a>)</td>
  </tr>
  <tr>
    <td>EFA-BW</td>
    <td>https://www.bwegt.de/bwegt-efa/</td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0" alt="0% Fortschritt"> (<a href="https://github.com/pietr26/EFA-Documentation/issues/5">#5</a>)</td>
  </tr>
</table>

In der Dokumentation ist stets der Endpunkt der allgemeinen IntAPI angegeben, kann aber 1:1 durch eine der o.g. Alternativen (bis auf die offizielle API) ersetzt werden.

## Mitmachen
Falls du...
- fehlende Parameter oder Felder herausfindest,
- einen weiteren EFA-Dienst entdeckst,
- weitere Abweichungen der bekannten Dienste aufdeckst (ggf. auf Version achten),
- ...

<a href="https://github.com/pietr26/EFA-Documentation/issues" target="_blank">eröffne gerne ein Issue</a>!

## Disclaimer
Ich oder dieses Projekt steht in keiner Verbindung zu den Betreibern von efa.de oder anderen EFA-basierten Diensten.

Die hier dokumentierte Schnittstelle ist nicht offiziell dokumentiert oder freigegeben und kann sich jederzeit ändern.
Die Informationen wurden ausschließlich durch die Analyse öffentlich zugänglicher Netzwerkrequests der Webseiten gewonnen.

Nutzung auf eigene Verantwortung.
