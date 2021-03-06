﻿---
title: Configurazione delle impostazioni dell'intervallo di porte multimediali
TOCTitle: Configurazione delle impostazioni dell'intervallo di porte multimediali
ms:assetid: 2c4b7c0b-0dce-48f4-a489-336d6e526f7c
ms:mtpsurl: https://technet.microsoft.com/it-it/library/JJ204770(v=OCS.15)
ms:contentKeyID: 49300031
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurazione delle impostazioni dell'intervallo di porte multimediali

 

_**Ultima modifica dell'argomento:** 2015-03-09_

Le impostazioni degli intervalli di porte multimediali possono influire in modo significativo sulle prestazioni del client e devono essere configurate. Per farlo, è possibile usare Lync Server Management Shell.

### Impostazioni intervallo di porte multimediali

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Impostazione</th>
<th>Descrizione</th>
<th>Cmdlet di Lync Server Management Shell</th>
<th>Parametri cmdlet</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Portrange\Enabled</p></td>
<td><p>Specifica se gli intervalli di porte inviati dal server devono essere usati dal client per il contenuto multimediale e la segnalazione. Viene usata con i valori secondari MinMediaPort e MaxMediaPort.</p></td>
<td><p><strong>CsConferencingConfiguration</strong></p></td>
<td><p>ClientMediaPortRangeEnabled</p></td>
</tr>
<tr class="even">
<td><p>Portrange\MinMediaPort</p></td>
<td><p>Specifica il numero iniziale di porte da usare per il contenuto multimediale. Insieme a MaxMediaPort specifica l'intervallo di porte. L'intervallo minimo consigliato è 40 porte.</p></td>
<td><p><strong>CsConferencingConfiguration</strong></p></td>
<td><p>ClientMediaPort (rappresenta il numero di porta iniziale da usare per il contenuto multimediale del client)</p></td>
</tr>
<tr class="odd">
<td><p>Portrange\MaxMediaPort</p></td>
<td><p>Specifica il numero massimo di porte da usare per il contenuto multimediale. Insieme a MinMediaPort specifica l'intervallo di porte. L'intervallo minimo consigliato è 40 porte.</p></td>
<td><p><strong>CsConferencingConfiguration</strong></p></td>
<td><p>ClientMediaPortRange (indica il numero totale di porte disponibili per il contenuto multimediale dei client; il valore predefinito è 40)</p></td>
</tr>
</tbody>
</table>


## Per configurare le impostazioni dell'intervallo di porte multimediali

1.  Avviare Lync Server Management Shell: fare clic sul pulsante **Start**, scegliere **Tutti i programmi**, **Microsoft Lync Server 2013** e quindi **Lync Server Management Shell**.

2.  Eseguire il cmdlet seguente:
    
        Get-CsConferencingConfiguration
    
    Questo cmdlet restituisce le impostazioni di configurazione delle conferenze.

3.  Eseguire il cmdlet seguente con i parametri e i valori che si desidera modificare. Per informazioni dettagliate sui parametri per questo cmdlet, vedere la documentazione di Lync Server Management Shell:
    
        Set-CsConferencingConfiguration
    

    > [!NOTE]
    > È possibile creare set aggiuntivi di impostazioni di configurazione delle conferenze per siti specifici. Usare il cmdlet <STRONG>New- CsConferencingConfiguration</STRONG> con un'identità di sito. Quando si creano nuove impostazioni di configurazione delle conferenze per i siti, le impostazioni dei siti hanno la precedenza su quelle globali. Per informazioni dettagliate, vedere la documentazione di Lync Server Management Shell.


