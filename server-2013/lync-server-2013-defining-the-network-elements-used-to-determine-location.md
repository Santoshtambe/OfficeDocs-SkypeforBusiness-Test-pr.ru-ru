﻿---
title: 'Lync Server 2013: определение сетевых элементов, используемых для определения местоположения'
TOCTitle: Определение сетевых элементов, используемых для определения местоположения
ms:assetid: 7538779d-055d-44ed-8dd7-11c45fc1b9f5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398567(v=OCS.15)
ms:contentKeyID: 49310199
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Определение сетевых элементов, используемых для определения местоположения, в Lync Server 2013

 

_**Дата изменения раздела:** 2012-10-29_

Если вы настраиваете в инфраструктуре Lync Server поддержку автоматического определения местоположения клиента, сначала необходимо решить, какие элементы сети будут использоваться для сопоставления звонящих с местоположениями. В Lync Server 2013 вы можете связать с местоположениями следующие элементы сети уровней 2 и 3:

  - адреса BSSID точек беспроводного доступа (WAP) (уровень 2);

  - порт коммутатора LLDP (уровень 2);

  - идентификаторы шасси коммутаторов LLDP (уровень 2);

  - IP-подсети (уровень 3);

  - MAC-адреса клиентов (уровень 2).

Элементы сети перечислены в порядке приоритета. Если местоположение клиента можно определить с помощью нескольких элементов сети, Lync Server использует этот порядок для выбора используемого способа.

В следующих подразделах приводятся более подробные сведения об использовании каждого элемента сети.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если вы используете элементы сети для сопоставления звонящих с местоположениями, крайне важно поддерживать базу данных информирования о местонахождении в актуальном состоянии. Так, если вы добавляете или изменяете элемент сети, например WAP, вам нужно удалить старую запись и добавить новую в базу данных местоположений.</td>
</tr>
</tbody>
</table>


## Точка беспроводного доступа

Если клиент подключается к сети по беспроводной связи, в запросе местоположения используется адрес BSSID точки WAP. Если клиент перемещается, полученная точка WAP может оказаться не самой близко расположенной. Возможны даже ситуации, когда она находится на другом этаже здания. Чтобы указать на то, что местоположение является приблизительным, вы можете добавить перед значением местоположения дескриптор Near или Close to.

Этот метод определения местоположения предполагает, что адреса BSSID всех точек WAP являются статическими. Однако если производитель WAP использует динамически назначаемые адреса BSSID, полученный адрес BSSID может измениться (вследствие изменения конфигурации WAP) и беспроводные клиенты могут не получить местоположение. Во избежание этого вам нужно добавить в базу данных информирования о местонахождении сведения о местоположении для экстренных служб (ERL) для всех возможных адресов BSSID, используемых каждой точкой WAP.

## Порты и коммутаторы LLDP

Управляемые коммутаторы Ethernet, поддерживающие протокол LLDP-MED, могут сообщить свои идентификационные данные и сведения о портах клиентам, совместимым с LLDP-MED. Это позволяет затем выполнять запросы к базе данных местоположений для определения местоположения устройства. Вы можете связать сведения о местоположении для экстренных служб с идентификатором шасси коммутатора или сопоставить их также на более низком уровне – уровне портов.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Lync Server 2013 поддерживает использование LLDP-MED для определения местоположений только для устройств Lync Phone Edition и Lync 2013 с Windows 8. Если вам нужно использовать данные коммутатора уровня 2 для определения местоположения клиентов Lync на ПК с проводным подключением, воспользуйтесь MAC-адресами клиентов.</td>
</tr>
</tbody>
</table>


## Подсеть

IP-подсети (уровень 3) обеспечивают механизм автоматического определения местоположения, поддерживаемый всеми клиентами Lync Server. Использование IP-подсетей является самым простым способом определения местоположения в плане настройки клиентов проводного доступа и управления ими. Однако прежде чем выбрать его, ответьте на следующие вопросы, чтобы определить, будет ли он достаточно точным в вашей ситуации.

  - Охватывают ли какие-либо клиентские подсети несколько этажей?

  - Охватывают ли какие-либо подсети несколько зданий?

  - Какую площадь покрывает каждая клиентская подсеть?

Если подсеть покрывает слишком большую площадь, может потребоваться использовать другой способ для определения местоположения клиентов. Однако, если это целесообразно, мы рекомендуем клиентам реорганизовать структуру IP-подсетей в соответствии с требованиями к точности определения местоположений ERL вместо того, чтобы реализовывать сторонние решения на основе SNMP, связанные с дополнительными затратами и повышением сложности.

## MAC-адрес клиента

Чтобы использовать MAC-адреса клиентских компьютеров для определения местоположения звонящих, требуются управляемые коммутаторы Ethernet. Кроме того, нужно развернуть стороннее решение SNMP, которое может обнаруживать MAC-адреса клиентов Lync, подключенных к этим коммутаторам или через них. Решение SNMP непрерывно опрашивает управляемые коммутаторы для получения текущих сопоставлений MAC-адресов конечных точек, подключенных к каждому порту, и получает ИД соответствующих портов. Когда клиент Lync выполняет запрос к информирования о местонахождении, информирования о местонахождении отправляет запрос стороннему приложению, используя MAC-адрес клиента, и затем возвращает все соответствующие IP-адреса коммутаторов и ИД портов. информирования о местонахождении использует эти сведения для запроса соответствующей записи из опубликованной карты географических соответствий (уровень 2), после чего возвращает местоположение клиенту. Если вы используете этот способ, убедитесь в том, что идентификаторы портов коммутаторов согласованы между приложением SNMP и записями в опубликованной базе данных местоположений.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Некоторые сторонние решения SNMP могут поддерживать неуправляемые коммутаторы доступа. Если коммутатор, обслуживающий клиент Lync, является неуправляемым, но имеет исходящее подключение к управляемому коммутатору-распределителю, управляемый коммутатор может сообщать приложению SNMP MAC-адреса клиентов, подключенных к коммутатору доступа. Эти сведения позволяют информирования о местонахождении определять местоположение пользователя. Однако всем портам неуправляемого коммутатора можно назначить только одно общее значение ERL, поэтому конкретизация местоположения возможна только на уровне шасси коммутатора доступа, но не на уровне портов.</td>
</tr>
</tbody>
</table>

