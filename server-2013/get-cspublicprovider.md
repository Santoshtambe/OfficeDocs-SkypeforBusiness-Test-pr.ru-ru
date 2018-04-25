﻿---
title: Get-CsPublicProvider
TOCTitle: Get-CsPublicProvider
ms:assetid: c122505d-7209-4dcb-a888-5c73f58fa68a
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg412945(v=OCS.15)
ms:contentKeyID: 49311045
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPublicProvider

 

_**Дата изменения раздела:** 2015-03-09_

Возвращает сведения об общедоступных поставщиках, настроенных для использования в организации. Общедоступный поставщик — это организация, которая обеспечивает обмен мгновенными сообщениями, сведения о присутствии и другие схожие услуги для неограниченного круга лиц. Lync Server поставляется с тремя настроенными, но не включенными общедоступными поставщиками: Yahoo\!, AIM (AOL) и Messenger (MSN). Данный командлет впервые появился в Lync Server 2010.

## Синтаксис

    Get-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsPublicProvider [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Примеры

## ПРИМЕР 1

Команда, показанная в примере 1, возвращает коллекцию всех общедоступных поставщиков, настроенных для использования в организации. При вызове командлета **Get-CsPublicProvider** без дополнительных параметров всегда возвращается полная коллекция общедоступных поставщиков.

    Get-CsPublicProvider

## ПРИМЕР 2

В примере 2 возвращаются все общедоступные поставщики с идентификатором Messenger. Поскольку каждый общедоступный поставщик (как и поставщик услуг размещения) должен иметь уникальный идентификатор, эта команда возвращает не более одного объекта.

    Get-CsPublicProvider -Identity "Messenger"

## ПРИМЕР 3

В примере 3 возвращаются все общедоступные поставщики, идентификаторы которых начинаются с буквы W. Для этого используется параметр Filter со значением "W\*".

    Get-CsPublicProvider -Filter W*

## ПРИМЕР 4

Команда, показанная в примере 4, возвращает коллекцию всех общедоступных поставщиков, которые в настоящее время отключены. Для этого команда сначала вызывает командлет **Get-CsPublicProvider**, который возвращает коллекцию всех общедоступных поставщиков, настроенных для использования в организации. Эта коллекция затем передается в командлет **Where-Object**, который выбирает только тех поставщиков, свойство Enabled которых имеет значение False.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False}

## ПРИМЕР 5

В примере 5 возвращаются все общедоступные поставщики, свойство VerificationLevel которых имеет значение AlwaysUnverifiable или UseSourceVerification. (Для уровня проверки можно задать значение AlwaysUnverifiable, UseSourceVerification или AlwaysVerifiable.) Для выполнения этой задачи команда сначала вызывает командлет **Get-CsPublicProvider**, который возвращает коллекцию всех общедоступных поставщиков, настроенных для использования в организации. Эта коллекция затем передается в командлет **Where-Object**, который выбирает только тех поставщиков, свойство VerificationLevel которых не равно AlwaysVerifiable. В результате будут выбраны только те поставщики, свойство VerificationLevel которых имеет значение AlwaysUnverifiable или UseSourceVerification.

    Get-CsPublicProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable"}

## Подробное описание

Федерация позволяет двум организациям установить отношение доверия, которое облегчает взаимодействие между двумя группами. Если федерация установлена, пользователи в этих двух организациях могут обмениваться мгновенными сообщениями, подписываться на уведомления о присутствии, а также взаимодействовать другими способами с помощью приложений SIP, таких как Lync 2013. Lync Server поддерживает три типа федерации: 1) прямую федерацию между двумя организациями; 2) федерацию между организацией и общедоступным поставщиком; 3) федерацию между организацией и сторонним поставщиком услуг размещения.

Общедоступный поставщик — это организация, которая предоставляет услуги связи SIP неограниченному кругу лиц. При установке федеративных отношений с общедоступным поставщиком фактически устанавливаются отношения со всеми пользователями, учетные записи которых размещаются этим поставщиком. Например, если вы установите федеративные отношения с Messenger (MSN), ваши пользователи смогут обмениваться мгновенными сообщениями и сведениями о присутствии со всеми, у кого есть учетная запись службы мгновенных сообщений Messenger.

Для федерации с общедоступным поставщиком необходимо создать и включить нового общедоступного поставщика. (Кроме того, общедоступный поставщик должен будет создать отношения федерации с вашей организацией.) Командлет **Get-CsPublicProvider** позволяет получить сведения об общедоступных поставщиках, настроенных для использования в организации.

По умолчанию право на локальный запуск командлета **Get-CsPublicProvider** имеют члены следующих групп: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Чтобы получить список всех ролей управления доступом на основе ролей (RBAC), которым назначен этот командлет (включая все самостоятельно созданные роли RBAC), выполните в командной строке Windows PowerShell следующую команду:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPublicProvider"}

## Параметры


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Обязательный?</th>
<th>Тип</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>Необязательный</p></td>
<td><p>System.String</p></td>
<td><p>Позволяет использовать подстановочные знаки, чтобы вернуть одного или нескольких общедоступных поставщиков. Например, чтобы вернуть коллекцию всех общедоступных поставщиков, идентификаторы которых начинаются с буквы Y, используйте следующий синтаксис: -Filter &quot;Y*&quot;. Чтобы вернуть коллекцию всех общедоступных поставщиков, идентификаторы которых содержат строку &quot;Windows&quot;, используйте следующий синтаксис: -Filter &quot;*Windows*&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Необязательный</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Уникальный идентификатор общедоступного поставщика, сведения о котором необходимо вернуть. Идентификатор обычно представляет собой имя веб-сайта, на котором предоставляются веб-службы (например, Yahoo!, AOL, MSN и т. д.).</p>
<p>При указании идентификатора нельзя использовать подстановочные знаки. Чтобы вернуть одного или нескольких общедоступных поставщиков с помощью подстановочных знаков, воспользуйтесь параметром Filter.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Необязательный</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Данные общедоступных поставщиков извлекаются из локальной реплики центрального хранилища управления, а не из самого центрального хранилища управления.</p></td>
</tr>
</tbody>
</table>


## Типы входных данных

Нет. Командлет **Get-CsPublicProvider** не принимает входные данные из конвейера.

## Типы возвращаемых данных

Возвращает экземпляры объекта Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider.

## См. также

#### Другие ресурсы

[Disable-CsPublicProvider](disable-cspublicprovider.md)  
[Enable-CsPublicProvider](enable-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Remove-CsPublicProvider](remove-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)
