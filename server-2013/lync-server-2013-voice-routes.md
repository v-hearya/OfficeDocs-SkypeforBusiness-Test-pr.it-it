﻿---
title: 'Lync Server 2013: Route vocali'
TOCTitle: Route vocali
ms:assetid: a2ddf327-2ec4-407b-af0f-276f2b13eefd
ms:mtpsurl: https://technet.microsoft.com/it-it/library/Gg412757(v=OCS.15)
ms:contentKeyID: 49301534
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Route vocali in Lync Server 2013

 

_**Ultima modifica dell'argomento:** 2012-10-22_

Le route delle chiamate specificano come devono essere gestite da Lync Server le chiamate in uscita effettuate da utenti di VoIP aziendale. Quando un utente compone un numero, il Front End Server normalizza la stringa di composizione nel formato E.164, se necessario, e tenta di associarla a un URI SIP. Se il server non riesce a effettuare l'associazione, applica la logica di routing delle chiamate in uscita in base al numero. Il passaggio finale della definizione della logica consiste nel creare una route di chiamata denominata separata per ogni insieme di numeri di telefono di destinazione elencati in ogni dial plan.

Prima di definire le route delle chiamate in uscita, è necessario completare le operazioni seguenti:

  - Distribuire uno o più trunk.

  - Creare dial plan in base alle necessità per siti, individui e oggetti contatto.

  - Creare record di utilizzo PSTN (Public Switched Telephone Network).

Per abilitare il routing delle chiamate in uscita, è inoltre necessario creare e assegnare uno o più criteri vocali. È possibile eseguire questa attività prima o dopo avere definito le route delle chiamate in uscita.

Per ogni route, è necessario specificare:

  - Un nome in base al quale la route possa essere facilmente identificata.

  - Una descrizione facoltativa per i casi in cui il nome da solo potrebbe non essere sufficiente per descrivere la route.

  - Il formato di corrispondenza dell'espressione regolare per l'identificazione dei numeri di telefono di destinazione a cui è applicata la route e le eccezioni a cui il formato di corrispondenza non deve essere applicato.

  - Uno o più trunk che si desidera assegnare alla route.

  - I record di utilizzo PSTN di cui gli utenti devono disporre per chiamare i numeri corrispondenti all'espressione regolare dei numeri di telefono di destinazione.

È possibile specificare route delle chiamate nel Pannello di controllo di Lync Server. Queste route vengono inserite nella tabella di routing del server, utilizzata da Lync Server per instradare le chiamate destinate alla rete PSTN.

## Supporto di trunk M:N

Lync Server offre una certa flessibilità per il routing delle chiamate alla rete PSTN. Una route vocale specifica un insieme di trunk alla rete PSTN che possono essere utilizzati per una determinata chiamata vocale. Un trunk associa un Mediation Server e un numero di porta a un gateway PSTN e a un numero di porta di attesa. Questa associazione logica consente a un Mediation Server di essere associato a più gateway e di avere più connessioni allo stesso gateway. Durante la definizione di una route delle chiamate vengono specificati i trunk associati alla route, ma non i Mediation Server associati alla route stessa. Per creare trunk definendo le relazioni tra i Mediation Server e i gateway PSTN, i sistemi IP-PBX e i Session Border Controller (SBC), utilizzare Generatore di topologie.

## Least Cost Routing

La possibilità di specificare i trunk verso cui vengono instradati diversi numeri consente di determinare quali route comportano i costi minori e di implementarle di conseguenza. In generale, per ridurre i costi delle chiamate interurbane, è consigliabile scegliere il trunk con il gateway più vicino alla località del numero di destinazione. Se ad esempio ci si trova a New York e si sta chiamando un numero a Roma, è possibile trasmettere la chiamata tramite la rete IP al trunk con il gateway nell'ufficio di Roma, sostenendo in questo modo solo i costi di una chiamata locale.

Per un esempio di utilizzo del Least Cost Routing, si consideri quanto segue. Fabrikam decide di consentire agli utenti tedeschi di comporre numeri degli Stati Uniti utilizzando il trunk degli Stati Uniti. Fabrikam inoltre desidera configurare il sistema in modo che tutte le chiamate di utenti di Lync Server statunitensi verso la Germania e paesi o regioni adiacenti vengano instradate al trunk con il gateway in Germania. Questo routing consente di risparmiare, dato che una chiamata dalla Germania all'Austria ad esempio costa meno di una chiamata dagli Stati Uniti all'Austria.

## Conversione delle stringhe di composizione in uscita

Lync Server 2013, come gli immediati predecessori, richiede la normalizzazione di tutte le stringhe di composizione al formato E.164 per consentire l'esecuzione della ricerca inversa dal numero (RNL, Reverse Number Lookup). Per i trunk con gateway o centralini (PBX, Private Branch Exchange) che richiedono numeri convertiti nei formati di composizione locali, Lync Server 2013 consente di creare una o più regole in grado di semplificare la modifica del numero chiamato, ovvero dell'URI della richiesta, prima di instradarlo al trunk. È ad esempio possibile scrivere una regola per rimuovere il prefisso +44 all'inizio di una stringa di composizione e sostituirlo con 0144.

Con Lync Server 2013, è possibile creare una o più regole che semplificano la modifica del numero chiamante prima di instradarlo al trunk.

Per pianificare i trunk che associano le coppie gateway:porta alle coppie Mediation Server:porta, può essere utile raggruppare i trunk con requisiti di composizione locale simili, in modo da ridurre il numero di regole di conversione necessarie e il tempo richiesto per scriverle.

## Configurazione dell'ID chiamante

Lync Server consente di modificare l'ID chiamante per le chiamate in uscita. Se ad esempio un'organizzazione desidera mascherare gli interni a composizione diretta dei dipendenti sostituendoli con il numero generico dell'azienda o del reparto, un amministratore può utilizzare il Pannello di controllo di Lync Server per eliminare l'ID chiamante e sostituirlo con un ID chiamante alternativo specificato. Nella pianificazione della logica di routing considerare per quali singoli, gruppi o siti si desidera utilizzare questa opzione oppure se deve essere applicata addirittura per tutti i dipendenti.


> [!NOTE]
> Per le chiamate reinoltrate tramite PSTN, verrà visualizzato l'ID chiamante generico anziché quello originario. La chiamata potrebbe quindi ignorare eventuali impostazioni Non disturbare o di privacy configurate dal destinatario.



## Logica di routing aggiuntiva

Durante la creazione delle route delle chiamate in uscita, tenere presente i fattori seguenti che influiscono sulla logica di routing:

  - Nelle situazioni in cui viene effettuata una chiamata attraverso un confine federato, la parte dell'URI relativa al dominio viene utilizzata per instradare la chiamata all'azienda responsabile dell'applicazione della logica di routing in uscita.

  - Se la parte dell'URI della richiesta relativa al dominio non contiene un dominio supportato per l'azienda, il componente di routing in uscita nel server non elabora la chiamata.

  - Se un utente non è abilitato per VoIP aziendale, il server applica un'altra logica di routing appropriata.

  - Se una chiamata viene instradata a un gateway completamente occupato (tutte le linee di trunk sono occupate), il gateway rifiuta la chiamata e la logica di routing in uscita la reindirizza alla successiva route Least Cost Routing. È necessario valutare con attenzione questo aspetto perché un gateway adatto nelle dimensioni a una piccola sede all'estero, ad esempio Zurigo, potrebbe in realtà trasportare una quantità significativa di traffico non locale per le chiamate internazionali dirette in Svizzera. Se il gateway non presenta dimensioni adeguate a questo traffico aggiuntivo, le chiamate dirette in Svizzera potrebbero essere instradate mediante un gateway in Germania, con conseguenti tariffe più alte.

