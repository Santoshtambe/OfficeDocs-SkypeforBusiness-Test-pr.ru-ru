﻿---
title: 'Lync Server 2013: планирование конференц-связи'
TOCTitle: Планирование конференц-связи
ms:assetid: 983a272a-e1b3-4d70-8f84-836b092fe526
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398781(v=OCS.15)
ms:contentKeyID: 49310605
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Планирование конференц-связи в Lync Server 2013

 

_**Дата изменения раздела:** 2013-01-29_

Lync Server 2013 предоставляет множество возможностей для конференц-связи:

  - Веб-конференции с функциями совместной работы, совместным использованием приложений и общим доступом к рабочему столу. Lync Server 2013 использует веб-приложения Office Web Apps и Сервер Office Web Apps для обработки общего доступа и отображения презентаций PowerPoint. Сведения об установке и настройке Сервер Office Web Apps см. в разделе [Настройка интеграции с сервером Office Web Apps и Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

  - Аудио- и видеоконференции, позволяющие пользователям проводить аудио- и видеоконференции в реальном времени без внешних служб, таких как Microsoft Live Meeting или аудиомост сторонних производителей.

  - Конференц-связь с телефонным подключением, которая позволяет пользователям подключаться к аудиосигналу конференции Lync Server 2013 с использованием телефонной сети общего пользования (ТСОП) без стороннего поставщика аудиоконференций.

  - Текстовые конференции с участием более двух сторон в одном сеансе. Сведения о текстовых конференциях см. в разделе [Планирование для серверов переднего плана, обмена мгновенными сообщениями и сведениями о присутствии в Lync Server 2013](lync-server-2013-planning-for-front-end-servers-instant-messaging-and-presence.md).

Lync Server 2013 поддерживает незапланированные и незапланированные конференции.

При развертывании Lync Server 2013,  переднего плана, вы также можете развернуть возможности веб-конференций, аудио- и видеоконференций и конференций с телефонным подключением. Функции конференций с мгновенными сообщениями всегда развертываются автоматически с функциями общения с помощью мгновенных сообщений в Lync Server 2013  переднего плана.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если развертывание включает собрания, организованные с помощью клиентов Office Communicator 2007 R2 (включая консоль Live Meeting или для проведения конференций для Microsoft Office Outlook), к собраниям применяются следующие ограничения после переноса в Lync Server 2013:
<ul>
<li><p>Пользователи, участвующие в собрании, не смогут использовать функции совместной работы с данными, включая совместное использование документов, приложений и рабочего стола.</p></li>
<li><p>Могут возникать проблемы, связанные со стабильностью, так как клиенты Office Communicator 2007 R2 не поддерживаются при использовании Lync Server 2013.</p></li>
</ul>
Чтобы избежать возникновения этих проблем, повторно запланируйте любое собрание, организованное с помощью клиентов Office Communicator 2007 R2, с помощью Outlook 2010 или Outlook 2013 посредством собраний по сети для Lync 2010 или надстройка собраний по сети для Lync 2013.</td>
</tr>
</tbody>
</table>


В следующих разделах описывается, что является необходимым для развертывания различных типов конференций, в том числе процесс планирования, компоненты, требования к оборудованию и программному обеспечению, а также процесс развертывания.

## Содержание

  - [Обзор конференц-связи в Lync Server 2013](lync-server-2013-overview-of-conferencing.md)

  - [Определение требований для конференц-связи в Lync Server 2013](lync-server-2013-defining-your-requirements-for-conferencing.md)

  - [Компоненты и топологии для конференц-связи в Lync Server 2013](lync-server-2013-components-and-topologies-for-conferencing.md)

  - [Технические требования для проведения конференций в Lync Server 2013](lync-server-2013-technical-requirements-for-conferencing.md)

  - [Контрольный список развертывания для конференций в Lync Server 2013](lync-server-2013-deployment-checklist-for-conferencing.md)

  - [Поддержка больших собраний в Lync Server 2013](lync-server-2013-support-for-large-meetings.md)
