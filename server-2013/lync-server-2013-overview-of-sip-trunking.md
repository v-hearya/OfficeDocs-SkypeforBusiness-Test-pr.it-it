﻿---
title: 'Lync Server 2013: Panoramica del trunking SIP'
TOCTitle: Panoramica del trunking SIP
ms:assetid: 204f2c21-436f-4b2d-93ea-d6db98fa2952
ms:mtpsurl: https://technet.microsoft.com/it-it/library/Gg398285(v=OCS.15)
ms:contentKeyID: 49299902
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Panoramica del trunking SIP in Lync Server 2013

 

_**Ultima modifica dell'argomento:** 2012-10-05_

La distribuzione del trunking SIP può costituire un importante passo verso la semplificazione delle telecomunicazioni nella propria organizzazione e per prepararsi agli ultimi aggiornamenti relativi alle comunicazioni in tempo reale. Uno dei principali vantaggi del trunking SIP è rappresentato dalla possibilità di consolidare le connessioni dell'organizzazione alla rete PSTN (public switched telephone network) presso un sito centrale, mentre il relativo predecessore, il trunking TDM (time division multiplexing) in genere richiede un trunk separato per ogni sito derivato.

## Trunking SIP in Lync Server

Le funzionalità di trunking SIP di Lync Server 2013 consentono di eseguire le operazioni seguenti:

  - Un utente Enterprise all'interno o all'esterno del firewall aziendale può effettuare una chiamata locale o interurbana specificata da un numero compatibile con E.164 che viene terminata sulla rete PSTN come servizio del provider di servizi corrispondente.

  - Qualsiasi sottoscrittore PSTN può contattare un utente Enterprise all'interno o all'esterno del firewall aziendale componendo un numero DID (Direct Inward Dialing) associato all'utente Enterprise.

## Risparmi sui costi

I risparmi sui costi associati al trunking SIP possono essere significativi:

  - Le chiamate interurbane in genere sono molto meno costose tramite un trunk SIP.

  - È possibile tagliare i costi di gestione e ridurre la complessità della distribuzione.

  - Le tariffe BRI (Basic Rate Interface) e PRI (Primary Rate Interface) possono essere eliminate se si connette un trunk SIP direttamente al provider di servizi di telefonia Internet (ITSP) con un costo significativamente inferiore. Nel trunking TDM i provider di servizi applicano alle chiamate una tariffa al minuto. Il costo del trunking SIP può basarsi sull'utilizzo della larghezza di banda, che può essere acquistato con incrementi inferiori, più economici. Il costo effettivo dipende dal modello di servizio dell'ITSP scelto.

## Confronto tra trunking SIP e hosting di un gateway PSTN o di un sistema IP-PBX

Poiché i trunk SIP si connettono direttamente al provider di servizi, è possibile eliminare i gateway PSTN con relativa complessità e con i costi di gestione a essi associati. L'utilizzo di un trunk SIP può determinare significativi risparmi sui costi grazie a una riduzione delle attività di manutenzione e amministrazione.

## Servizi VoIP estesi

Le funzionalità vocali sono spesso la causa principale per la distribuzione del trunking SIP, ma il supporto vocale è solo il primo passo. Con il trunking SIP è possibile estendere le funzionalità VoIP e abilitare Lync Server 2013 per offrire un più ampio set di servizi:

  - Il rilevamento avanzato di informazioni sulla presenza per dispositivi che non eseguono Lync Server 2013 garantisce una maggiore integrazione con i cellulari, in modo che sia possibile visualizzare quando un utente è impegnato in una chiamata al cellulare.

  - La funzionalità per le chiamate di emergenza E9-1-1 consente alle autorità che rispondono a tali chiamate di determinare il luogo da cui proviene la chiamata dal numero di telefono.


> [!NOTE]
> Contattare il provider di servizi Internet per un elenco dei servizi supportati e che possono essere abilitati per la propria organizzazione.


