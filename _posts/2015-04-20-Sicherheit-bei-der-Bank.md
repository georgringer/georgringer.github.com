---
layout:     post
title:      Sicherheit im Bankenalltag
summary:      Der folgende Blogpost beschreibt Sicherheit im Bankenalltag und wie schwer es ist, diese zu verbessern
date:       2015-04-20
categories: security bank
---

Der folgende Blogpost beschreibt Sicherheit im Bankenalltag und wie schwer es ist, diese zu verbessern. Als neugieriger Entwickler bleibt auch der Onlineauftritt einer Bank nicht vor den Blick hinter die Kulissen verschont.
<!--more-->
Schnell wird einem bewusst, dass die unterschiedlichen Bereiche der Applikation teilweise nur lose aneinander gekoppelt sind und unterschiedlichen Sicherheitsanforderungen unterliegen. 

Während der Teil, der sich um Transaktionen kümmert, sicher scheint, kann man das von anderen nicht behaupten. Auf dem ersten Blick mag das beruhigend klingen, aber wie schon Goethe schrieb: "*Ein einziges Glied, das in einer großen Kette bricht, vernichtet das Ganze.*".

## Lücken im Detail

Solange die Lücken nicht behoben sind bzw diese nicht als solche nicht komplett ignoriert werden, werde ich hier keine genauen Details nennen.

Schon mal vorweg, es gibt genügend. Sortiert nach den Top 10 der OWASP:

- 2.) Broken Authentication & Session Management
- 3.) Cross-Site Scriptiong
- 4.) Insecure Direct Object Reference
- 5.) Security Misconfiguration
- 6.) Sensitive Data Exposure
- 9.) Using Components with Known Vulnerabilities

Zusätzlich machen es Konzeptionsfehler einfach, beinahe perfekte Phishing-Attacken zu implementieren, die selbst versierte Personen nicht als solches wahrnehmen würden.

## Ablauf

Es ist nicht leicht, einen Ansprechpartner zu finden, der kompetent genug ist, um die Problematiken von Sicherheitslücke zu verstehen und der auch an einer Lösung mitarbeiten kann.

Die gesamte Website hilft hier genausowenig weiter wie der Bankbetreuer oder der Helpdesk. Letztere wissen leider nicht wen genau Sie fragen müssen. 

### 15.2.2015

Ein erster Versuch über den eigenen Bankbetreuer via Mail scheitert, Abwesenheitsinfo: Die Person ist noch 1 Woche auf Urlaub.

### 11.3.2015

Das erste Nachhaken bei einem persönlichen Termin mit dem Betreuer. Dieser hat die Informationen (Ein PDF mit Proof of concept Links und weiteren Details) an die IT weitergeleitet.

### 23.3.2015

Die IT hat geantwortet! Das liest sich leider nicht sehr erfreulich.

    [...] Dieses Feedback Formular gehört zur "Homepage"   
    und dient nicht zum Austausch vertraulicher Informationen im   
    Sinne eines sichereren Kommunikationskanals. Das hier aufgerufene   
    Feedback Formular wird lediglich durch einen Reverse Proxy   
    angezeigt. [...] Der Schutz des Webformulars basiert auf   
    ähnlichen Verfahren wie Session, Token und Bearer.
        
In meiner heilen Welt bin ich davon ausgegangen, dass in keinster Applikation einer Bank nur irgendeine kleinste XSS-Lücke auftreten darf. Andere Sicherheitslücken, die keine Authentifizierung benötigen, wurden gar nicht erst erwähnt.

Ich bin nicht zufrieden.

### 25.3.2015

Der Social-Media-Account der Bank kreuzt meine Wege und diese sind die Ersten, die versprechen sich bis zum nächsten Tag darum zu kümmern. Hoffnung keimt auf!

Es wird mir eine Kontaktperson genannt und ich lege wieder los. Eine automatische Antwort erreicht mich leider sofort: 

    Ich bin am 08.05.2012 leider nicht erreichbar.   
    E-Mails werden nicht weitergeleitet und am 09.05.2012 bearbeitet.
    
Ich fühle mich etwas vera****t.

### 27.3.2015

Im Hintergrund tut sich wohl doch mehr als gedacht und es wird ein Termin für eine Telefonkonfernz ausgemacht.

### 13.4.2015

Einen Termin zuvor musste ich leider absagen, aber ich bin gespannt! 5 weitere Personen sind involviert, ich kann keine Namen nennen, ich hab sie mir auch nicht gemerkt. 

In Kurz:

- Echtes Cross-Site Scripting ist ohnedies nicht möglich, wir blocken alle spitzen Klammern und nun in Einzelfällen auch Strichpunkte
- Wir haben alle 1-2 Jahre einen Penetrationstest der alles überprüft
- Der nächste Pentest startet in den nächsten Tagen
- Ich schlage Ende Mai als Termin für eine Disclosure vor und empfinde dass diese Idee Bewegung in die Sache bringt.

Ich fasse alle bisherigen Erkenntnisse und ein paar neue, noch üblere, zusammen und gebe diese beim IT-Security verantwortlichen ab.

**Ich bin gespannt!**

### 20.4.2015

Der Bereichsleiter für Marketing und Kommunikation ruft mich an und fragt ob er den Kontakt zur Herstellerfirma knüpfen darf. Ich willige gerne ein. Kurze Zeit später ruft der Geschäftsführer dieser Firma an. Ein sehr interessantes Gespräch! Wir werden uns treffen.

# Mein persönliches Fazit

Noch immer bin ich der Meinung, dass viele von den aufgezeigten Fehlern gar nicht erst passieren dürften. 
Sofware ist nicht von einem auf den anderen Tag "End of life" und wenn ein Penetrationstest die simplesten XSS-Lücken nicht findet, ist er meiner Meinung nach schlicht weg nicht gelaufen.

Mittlerweile ist der Frustrationslevel gesunken und ich bin gespannt wie es weiter geht. Es kündigen sich interessante Meetings an. 
