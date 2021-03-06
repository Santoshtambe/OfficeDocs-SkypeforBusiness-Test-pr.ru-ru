﻿---
title: 'Lync Server 2013: настройка паролей учетных записей проверки подлинности Kerberos'
TOCTitle: Настройка паролей учетных записей проверки подлинности Kerberos
ms:assetid: b435f88e-4a77-4be7-b7e5-c17484303b74
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg412870(v=OCS.15)
ms:contentKeyID: 49310906
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка паролей учетных записей проверки подлинности Kerberos в Lync Server 2013

 

_**Дата изменения раздела:** 2010-11-03_

После создания объекта-компьютера для учетной записи проверки подлинности Kerberos можно задать пароль для учетной записи. Для задания пароля учетной записи Kerberos на одном сервере можно использовать командлет Windows PowerShell. Кроме того, можно задать пароль для объекта, созданного для проверки подлинности Kerberos. В качестве пароля можно использовать известное значение, однако по умолчанию используется случайный пароль. Пароль доступен всем источникам проверки подлинности Kerberos, которые используют учетную запись. Для указания паролей учетных записей Kerberos и управления ими используйте командлеты Windows PowerShell.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Объект учетной записи Kerberos – это объект-компьютер, который использует параметр UserAccount для операций командлетов Windows PowerShell, которые ссылаются на него. Обратите внимание, что это не ошибка, а намеренное поведение командлета при использовании с учетной записью создания и поддержки Kerberos.</td>
</tr>
</tbody>
</table>


## Содержание

  - [Установка пароля учетной записи Kerberos для проверки подлинности на сервере в Lync Server 2013](lync-server-2013-set-a-kerberos-authentication-account-password-on-a-server.md)

  - [Синхронизация пароля учетной записи проверки подлинности Kerberos с IIS в Lync Server 2013](lync-server-2013-synchronize-a-kerberos-authentication-account-password-to-iis.md)

