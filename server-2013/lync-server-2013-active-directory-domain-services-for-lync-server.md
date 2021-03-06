﻿---
title: Доменные службы Active Directory для Lync Server 2013
TOCTitle: Доменные службы Active Directory для Lync Server 2013
ms:assetid: 5483afd5-d8af-4825-ae95-a82dbe941dbf
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn481129(v=OCS.15)
ms:contentKeyID: 59679352
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Доменные службы Active Directory для Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

Доменные службы Active Directory работает в качестве службы каталогов для сетей Windows Server 2003, Windows Server 2008, Windows Server 2012 и Windows Server 2012 R2. Доменные службы Active Directory также служит основой, на которой создается инфраструктура безопасности Microsoft Lync Server 2013. Целью данного раздела заключается в описании способа использования сервером Lync Server 2013Доменные службы Active Directory для создания надежной среды для служб мгновенных сообщений, веб-конференций, мультимедии и голосовых служб. Дополнительные сведения о расширениях Lync Server для Доменные службы Active Directory и по подготовке среды для Доменные службы Active Directory см. в разделе [Подготовка доменных служб Active Directory для Lync Server 2013](lync-server-2013-preparing-active-directory-domain-services.md) документации по развертыванию. Дополнительные сведения о роли Доменные службы Active Directory в сетях Windows Server см. в документации к версии используемой операционной системы.

Сервер Lync Server 2013 использует Доменные службы Active Directory для хранения следующих данных:

  - глобальные параметры, которые требуются для всех серверов по управлением Lync Server 2013 в лесе;

  - служебная информация, которая определяет роли всех серверов под управлением Lync Server 2013 в лесе;

  - некоторые пользовательские параметры.

## Инфраструктура Active Directory

Требования к инфраструктуре для Active Directory содержат следующее:

  - требования к ОС для доменных контроллеров;

  - требования для функциональных уровней домена и леса;

  - требования для домена глобального каталога.

Подробные сведения см. в разделе [Требования к инфраструктуре Active Directory для Lync Server 2013](lync-server-2013-active-directory-infrastructure-requirements.md) документации по развертыванию.

## Подготовка Доменные службы Active Directory

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Мы рекомендуем развертывать глобальные настройки в контейнере конфигураций, а не в контейнере системы. Это действие не повысит уровень безопасности, но может повлечь за собой улучшение масштабируемости для некоторых топологий Доменные службы Active Directory. При выполнении миграции с сервера Microsoft Office Communications Server 2007 и использовании контейнера системы, но с планированием использования контейнера конфигураций НЕОБХОДИМО переместить параметры контейнера системы ПЕРЕД подготовкой к любым обновлениям. О переносе параметров контейнера системы в контейнер конфигурации см. в разделе Office Communications Server 2007 средства миграции глобальных параметров по адресу <a href="http://go.microsoft.com/fwlink/p/?linkid=145236">http://go.microsoft.com/fwlink/p/?LinkId=145236</a>.</td>
</tr>
</tbody>
</table>


При развертывании Lync Server 2013 первым действием требуется подготовить Доменные службы Active Directory. Подготовка Доменные службы Active Directory для Lync Server 2013 состоит из трех этапов.

  - **Подготовка схемы**. Эта задача расширяет схему в Доменные службы Active Directory, чтобы она включала определенные классы и атрибуты для Lync Server 2013. Подробные сведения о подготовке схемы см. в разделе [Проведение подготовки схемы Active Directory в Lync Server 2013](lync-server-2013-running-schema-preparation.md) документации по развертыванию. Дополнительные сведения см. в разделе [Миграция с Office Communications Server 2007 R2 на Lync Server 2013](migration-from-office-communications-server-2007-r2-to-lync-server-2013.md).

  - **Подготовка леса**. Эта задача создает глобальные параметры и объекты в корневом домене леса, а также универсальные группы обслуживания и администрирования, которые управляют доступом к этим параметрам и объектам. Подробные сведения о подготовке леса см. в разделе [Проведение подготовки леса для Lync Server 2013](lync-server-2013-running-forest-preparation.md) документации по развертыванию.

  - **Подготовка домена**. Эта задача добавляет необходимые записи управления доступом (ACE) в универсальные группы, которые предоставляют разрешения на размещение и управление пользователями в домене. Задачу необходимо выполнить для всех доменов, на которых требуется развернуть серверы под управлением Lync Server 2013, и любых доменов, на которых расположены пользователи сервера Lync Server. Подробные сведения о подготовке домена см. в разделе [Проведение подготовки домена для Lync Server 2013](lync-server-2013-running-domain-preparation.md) документации по развертыванию.

Обзор полного процесса по подготовке Active Directory, а также необходимые для выполнения каждого этапа права и разрешения см. в разделе [Требования к инфраструктуре Active Directory для Lync Server 2013](lync-server-2013-active-directory-infrastructure-requirements.md) документации по развертыванию.

## Универсальные группы

Во время подготовки леса Lync Server 2013 создает разные универсальные группы в Доменные службы Active Directory, которые имеют разрешения для доступа и управления глобальными параметрами и службами. Универсальные группы делятся на следующие группы:

  - **административные группы**. Эти группы определяют основные роли администратора для сети сервера Lync Server. При подготовке леса эти группы администрирования добавляются в группы инфраструктуры сервера Lync Server;

  - **группы обслуживания**. Эти группы представляют собой служебные учетные записи, которым требуется доступ к разным службам, предоставляемым сервером Lync Server;

  - **группы инфраструктур**. Эти группы предоставляют разрешения для доступа к определенным областям инфраструктуры сервера Lync Server. Они работают как компоненты административных групп; не следует изменять их или добавлять в них пользователей непосредственно. При подготовке леса определенные группы обслуживания и администрирования добавляются в соответствующие группы инфраструктур.

Подробные сведения об определенных универсальных группах, созданных при подготовке AD для сервера Lync Server, а также о добавляемых в группы инфраструктур группах обслуживания и группах администрирования см. в разделе [Изменения, вносимые во время подготовки леса в Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md) документации по развертыванию.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Сервер Lync Server 2013 поддерживает универсальные группы в Windows Server 2012 для серверов под управлением Lync Server 2013, а также ОС Windows Server 2003 для контроллеров доменов. Участники универсальных групп могут включать в себя другие группы и учетные записи из любого домена в дереве доменов или лесе; можно назначить разрешения в любом домене дерева доменов или леса. Поддержка универсальных групп совместно с делегированием административных полномочий упрощает управление развертыванием Lync Server. Например, не нужно добавлять один домен к другому, чтобы разрешить администратору управлять обоими.</td>
</tr>
</tbody>
</table>


## Управление доступом на основе ролей

Кроме создания универсальных групп обслуживания и администрирования и добавления этих групп в соответствующие универсальные группы, подготовка леса также создает группы управления доступом на основе ролей (RBAC). Подробные сведения об определенных группах RBAC, созданных при подготовке леса, см. в разделе [Изменения, вносимые во время подготовки леса в Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md) документации по развертыванию. Дополнительные сведения о группах RBAC см. в разделе [Управление доступом на основе ролей (RBAC) для Lync Server 2013](lync-server-2013-role-based-access-control-rbac.md).

## Записи управления доступом (ACE) и наследование

В процессе подготовки леса создаются частные и общедоступные записи ACE, а также создаются записи ACE универсальных групп при их добавлении. Создаются определенные частные записи ACE в контейнере глобальных параметров, используемом сервером Lync Server. Этот контейнер используется только Lync Server и расположен в контейнере конфигураций или в контейнере системы в корневом домене в зависимости от местоположения для хранения глобальных параметров.

На этапе подготовки домена в универсальные группы добавляются необходимые записи управления доступом (ACE), которые предоставляют разрешения для размещения и управления пользователями в домене. При подготовке домена создаются записи ACE в корне домена и три встроенных контейнера: пользователи, компьютеры и контроллеры домена.

Подробные сведения об общедоступных записях ACE, созданных и добавленных в процессе подготовки леса и домена, см. в разделе [Изменения, вносимые во время подготовки леса в Lync Server 2013](lync-server-2013-changes-made-by-forest-preparation.md) и [Изменения, внесенные в ходе подготовки домена в Lync Server 2013](lync-server-2013-changes-made-by-domain-preparation.md) документации по развертыванию.

Организации часто блокируют Доменные службы Active Directory (AD DS) во избежание рисков для безопасности. Однако при блокировании среды Active Directory могут ограничиваться разрешения, необходимые для Lync Server 2013. Это может включать в себя записи ACE из контейнеров и подразделений, а также отключение разрешений наследования для объектов пользователя, контакта, InetOrgPerson или компьютеров. В заблокированной среде Active Directory разрешения должны устанавливаться вручную для контейнеров и подразделений, которым они требуются. Подробные сведения см. в разделе [Подготовка заблокированных доменных служб Active Directory в Lync Server 2013](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md) документации по развертыванию.

## Информация о сервере

В процессе активации сервер Lync Server 2013 публикует информацию о сервере в три следующих местоположения в Доменные службы Active Directory:

  - точка подключения службы (SCP) для каждого объекта компьютера Active Directory, соответствующего физическому компьютеру, на котором установлен сервер Lync Server 2013;

  - объекты сервера, созданные в контейнере класса **msRTCSIP-Pools**;

  - доверенные серверы, указанные в топологий.

## Точки подключения служб

Каждый объект Lync Server 2013 в Доменные службы Active Directory имеет SCP под названием RTC Services, который в свою очередь содержит количество атрибутов для определения каждого компьютера и указания предоставляемых им служб. Более важные атрибуты SCP включают в себя *serviceDNSName*, *serviceDNSNameType*, *serviceClassname* и *serviceBindingInformation*. Сторонние приложения по управлению активами могут извлекать информацию о сервере в развертывании путем выдачи запросов по отношению этих и других атрибутов SCP.

## Объекты сервера Active Directory

Каждая роль сервера Lync Server 2013 имеет соответствующий объект Active Directory, атрибуты которого определяют предоставляемые этой ролью службы. Также при активации Standard Edition или создании пула Enterprise Edition сервер Lync Server 2013 создает новый объект **msRTCSIP-Pool** в контейнере **msRTCSIP-Pools**. Класс **msRTCSIP-Pool** указывает полное доменное имя пула и сопоставление между компонентами переднего плана и встроенными компонентами пула. (Standard Edition рассматривается как логический пул, передний и встроенный план которого совмещается на одном компьютере.)

## Доверенные серверы

В Lync Server 2013 доверенными серверами являются те, которые указываются при выполнении топологий и публикации топологии. Опубликованная топология, включая все сведения сервера, сохраняется в центральном хранилище управления. Только серверы, определенные в центральном хранилище управления, являются доверенными. В Lync Server 2013 доверенными сервером является тот, который соответствует указанным ниже критериям.

  - Полное доменное имя сервера встречается в топологии, сохраненной в центральном хранилище управления.

  - Сервер предоставляет действительный сертификат от доверенного ЦС. Подробные сведения см. в разделе [Требования инфраструктуры сертификатов для Lync Server 2013](lync-server-2013-certificate-infrastructure-requirements.md).

При отсутствии любого из этих критериев сервер не является доверенным, а при подключении приходит отказ. Это двойное требование предотвращает возможную атаку, в которой незаконный сервер пытается присвоить себе полное доменное имя действительного сервера.

Кроме того, для разрешения развертываниям Microsoft Office Communications Server 2007 R2 и Microsoft Office Communications Server 2007 взаимодействовать с серверами Lync Server 2013 сервер Lync Server 2013 создает контейнеры на этапе подготовки леса для размещения списков недоверенных серверов из предыдущих выпусков. В таблице ниже описаны контейнеры, созданные для обеспечения совместимости с предыдущими развертываниями.

### Списки доверенных серверов и их контейнеры Active Directory для совместимости с предыдущими выпусками

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Список доверенных серверов</th>
<th>Контейнер Active Directory</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Серверы стандартного выпуска и серверы переднего плана пула Enterprise</p></td>
<td><p>Служба RTC Service/глобальные параметры</p></td>
</tr>
<tr class="even">
<td><p>Серверы для конференций</p></td>
<td><p>Служба RTC Service/доверенные MCU</p></td>
</tr>
<tr class="odd">
<td><p>Серверы веб-компонентов</p></td>
<td><p>Служба RTC Service/доверенные серверы веб-компонентов</p></td>
</tr>
<tr class="even">
<td><p>Серверы-посредники и серверы веб-клиента Communicator, сервер приложений, регистратор с качеством взаимодействия, служба аудио- и видеоконференции (а также сторонние серверы SIP)</p></td>
<td><p>Служба RTC Service/доверенные службы</p></td>
</tr>
<tr class="odd">
<td><p>Прокси-серверы</p></td>
<td><p>Сервер Lync Server 2013 не поддерживает возможность обратной совместимости для прокси-серверов.</p></td>
</tr>
</tbody>
</table>


Для поддержки доверенных серверов из предыдущих выпусков необходимо запустить анализатор соответствия рекомендациям. Подробные сведения о запуске анализатора соответствия рекомендациям см. на веб-сайте по адресу [http://go.microsoft.com/fwlink/p/?LinkId=330633](http://go.microsoft.com/fwlink/p/?linkid=330633).

