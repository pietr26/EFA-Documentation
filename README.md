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
    <th>Dienst-ID</th>
    <th>URL</th>
    <th>Abdeckung Fahrplandaten</th>
    <th>Abdeckung Echtzeitdaten & Störungsmeldungen</th>
    <th>Einbindung in Dokumentation</th>
  </tr>
  <tr>
    <td>A</td>
    <td><code>https://efa.de/efa/</code></td>
    <td>gesamt Deutschland</td>
    <td>Hannover, Braunschweig, Hameln</td>
    <td><img src="https://geps.dev/progress/80"> (<a href="https://github.com/pietr26/EFA-Documentation/issues/6">#6</a>)</td>
  </tr>
  <tr>
    <td>DE-VRR</td>
    <td><code>https://www.vrr.de/vrr-efa/</code><br><code>https://efa.vrr.de/standard/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
  <tr>
    <td>DE-BWS</td>
    <td><code>https://www.bwegt.de/bwegt-efa/</code><br><code>https://www.efa-bw.de/nvbw3L/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
  <tr>
    <td>DE-VVV</td>
    <td><code>https://vogtlandauskunft.de/vvv2/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
  <tr>
    <td>DE-MVV</td>
    <td><code>https://efa.mvv-muenchen.de/mobile/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
  <tr>
    <td>AT-LI</td>
    <td><code>https://www.linzag.at/static/</code><br><code>https://www.linzag.at/linz2/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
  <tr>
    <td>AU-NSW</td>
    <td><code>https://transportnsw.info/web/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
  <tr>
    <td>DE-BY</td>
    <td><code>https://mobile.defas-fgi.de/beg/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
  <tr>
    <td>DE-VRN</td>
    <td><code>https://mandanten.vrn.de/takt2/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
  <tr>
    <td>DE-VGN</td>
    <td><code>https://efa.vgn.de/vgn/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
  <tr>
    <td>IT-BZ</td>
    <td><code>https://mobility.api.opendatahub.com/v2/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
  <tr>
    <td>DE-VVO</td>
    <td><code>http://efa.vvo-online.de:8080/std3/trias/</code></td>
    <td>...</td>
    <td>...</td>
    <td><img src="https://geps.dev/progress/0"></td>
  </tr>
</table>

In der Dokumentation ist stets der Endpunkt der allgemeinen IntAPI angegeben, kann aber 1:1 durch eine der o.g. Alternativen (bis auf die offizielle API) ersetzt werden.

Folgende Dienste wurden bereits kontrolliert und besitzen die selben Daten wie oder eine Teilmenge der Daten der schon o.g. Dienste. Die Beurteilung dieser Doppelungen findet anhand einer Abfrage von <code>XML_ADDINFO_REQUEST</code> und anschließendem Vergleich der ausgegebenen Meldungen statt, da sich diese erfahrungsgemäß nur auf das abgedeckte Verkehrsgebiet beschränken. Die doppelten Dienste können zwar genutzt werden, aufgrund keiner weiteren Prüfung kann es hier jedoch noch zu Unterschieden kommen oder geringeren Datenmengen kommen. Aus dem Grunde empfehle ich einfach die Nutzung der obigen Dienste, die eh ja nicht weniger abdecken.
<table>
  <tr>
    <th>URL</th>
    <th>(Teil-)Übereinstimmung mit Dienst</th>
  </tr>
  <tr>
    <td><code>https://bsvg.efa.de/vrbstd/</code> (BSVG)</td>
    <td>A</td>
  </tr>
  <tr>
    <td><code>https://efa.projektionisten.eu/efaws2/default/</code> (RVHI)</td>
    <td>A</td>
  </tr>
  <tr>
    <td><code>https://www.westfalenfahrplan.de/nwl-efa/</code> (WT)</td>
    <td>DE-VRR</td>
  </tr>
  <tr>
    <td><code>https://www.naldo.de/_assets/012ccdbd1331184d82aa9387f0ed2f73/efa/</code> (naldo)</td>
    <td>DE-BWS</td>
  </tr>
  <tr>
    <td><code>https://www3.vvs.de/mngvvs/</code> (VVS)</td>
    <td>DE-BWS</td>
  </tr>
  <tr>
    <td><code>https://www.kvv.de/tunnelEfaDirect.php?action=</code> (KVV)</td>
    <td>DE-BWS</td>
  </tr>
  <tr>
    <td><code>https://www.fahrplanauskunft-mv.de/vmv-efa/</code> (MV)<br>Tatsächlich enthalten MV und BW dieselben Daten</td>
    <td>DE-BWS</td>
  </tr>
  <tr>
    <td><code>https://www.vrt-info.de/fahrplanauskunft/</code> (VRT)</td>
    <td>DE-VRN</td>
  </tr>
</table>

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
