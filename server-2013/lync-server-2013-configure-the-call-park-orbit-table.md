﻿---
title: 'Lync Server 2013: настройка таблицы орбит парковки вызовов'
TOCTitle: Настройка таблицы орбит парковки вызовов
ms:assetid: e5cc0c19-7b2c-48e7-a21d-cfb23c842f0f
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg399020(v=OCS.15)
ms:contentKeyID: 49311476
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка таблицы орбит парковки вызовов в Lync Server 2013

 

_**Дата изменения раздела:** 2012-09-10_

Для Приостановка вызовов используются орбиты. Прежде чем пользователи смогут парковать вызовы и снимать их с удержания, вам следует настроить таблицу орбит Приостановка вызовов. Вам необходимо указать диапазоны добавочных номеров (орбит), которые будут зарезервированы в вашей организации для парковки вызовов, и определить маршрутизацию для этих диапазонов, указал, каким пулом Приостановка вызовов обрабатывается каждый из диапазонов. При определении диапазонов орбит требуется обеспечить достаточное число орбит, чтобы ни одна из орбит не использовалась повторно слишком часто, и одновременно не использовать слишком много орбит, чтобы не ограничивать количество добавочных номеров для пользователей и других служб. Вы можете создать несколько диапазонов орбит Приостановка вызовов для каждого пула Lync Server, в котором развернут компонент приостановки вызовов. Каждый диапазон орбит Приостановка вызовов должен иметь глобальное уникальное имя и уникальный набор добавочных номеров.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Обычно диапазон орбит содержит 100 или менее орбит. Каждый из диапазонов может быть значительно больше, максимальные значения составляют не более 10000 орбит на диапазон и менее 50000 орбит на пул. Если диапазон слишком мал, орбиты используются повторно с большей частотой.</td>
</tr>
</tbody>
</table>


Для своих диапазонов орбит используйте блоки виртуальных добавочных номеров (которым не назначен телефон или пользователь).

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Назначение номеров прямого входного набора (DID) в качестве номеров орбит в таблице Приостановка вызовов не поддерживается.</td>
</tr>
</tbody>
</table>


## Содержание

[Создание или изменение диапазона орбит для парковки вызовов в Lync Server 2013](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)
