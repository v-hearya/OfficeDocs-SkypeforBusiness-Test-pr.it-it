﻿---
title: 'Lync Server 2013: Tabella Pools'
TOCTitle: Tabella Pools
ms:assetid: e0632b8d-e23a-4365-8a7a-6ca0957a46a9
ms:mtpsurl: https://technet.microsoft.com/it-it/library/Gg398991(v=OCS.15)
ms:contentKeyID: 49302228
ms.date: 08/24/2015
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabella Pools in Lync Server 2013

 

_**Ultima modifica dell'argomento:** 2015-03-09_

La tabella Pools è una tabella di supporto in cui vengono archiviate informazioni sui diversi pool. Ogni record della tabella rappresenta un pool.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Colonna</th>
<th>Tipo di dati</th>
<th>Chiave/indice</th>
<th>Dettagli</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PoolId</strong></p></td>
<td><p>int</p></td>
<td><p>Primaria/o</p></td>
<td><p>Numero univoco che identifica il pool.</p></td>
</tr>
<tr class="even">
<td><p><strong>PoolFQDN</strong></p></td>
<td><p>nvarchar(256)</p></td>
<td><p> </p></td>
<td><p>Nome di dominio completo del pool.</p></td>
</tr>
</tbody>
</table>

