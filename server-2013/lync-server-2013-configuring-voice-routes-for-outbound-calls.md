﻿---
title: 'Lync Server 2013: настройка маршрутов голосовой связи для исходящих звонков'
TOCTitle: Настройка маршрутов голосовой связи для исходящих звонков
ms:assetid: 3c182cdd-7a4a-4a9d-bdac-4199f0abd947
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg425890(v=OCS.15)
ms:contentKeyID: 49309507
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка маршрутов голосовой связи для исходящих звонков в Lync Server 2013

 

_**Дата изменения раздела:** 2012-11-01_

Маршрут голосовых вызовов системы Lync Server 2013 связывает конечные номера телефонов с одним или несколькими шлюзами ТСОП или магистралями SIP, а также одной или несколькими записями использования ТСОП.

**Просмотр голосовых маршрутов с помощью управления Lync Server**

1.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Щелкните **Маршрутизация голосовой связи** .

3.  Перейдите на вкладку **Route** (Маршрут).

4.  Дважды щелкните маршрут голосовой связи для просмотра дополнительных свойств в списке маршрутов голосовой связи или выберите маршрут и щелкните пункт **Изменить** . Затем щелкните **Подробнее** .
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Одновременно можно просматривать подробные сведения только по одному маршруту.</td>
    </tr>
    </tbody>
    </table>


**Просмотр голосовых маршрутов с помощью Windows PowerShell**

  - Запустите командную консоль Lync Server: нажмите кнопку **Пуск**, последовательно выберите пункты **Все программы** и **Microsoft Lync Server 2013** и щелкните элемент **Командная консоль Lync Server**. Маршруты голосовой связи можно также просматривать с помощью Windows PowerShell и командлета **Get-CsVoiceRoute**. Этот командлет можно запустить либо из командная консоль Lync Server 2013, либо из удаленного сеанса Windows PowerShell. Дополнительные сведения об использовании Windows PowerShell в удаленном режиме для подключения к Lync Server см. статью блога Lync Server Windows PowerShell "Краткое руководство: управление Microsoft Lync Server 2010 в удаленном режиме с помощью PowerShell" по адресу [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).
    
    Чтобы просмотреть сведения обо всех маршрутах голосовой связи, введите следующую команду в командной консоли Командная консоль Lync Server и нажмите клавишу ВВОД:
    
        Get-CsVoiceRoute
    
    Команда возвращает примерно следующую информацию:
    
        Identity          : global
        Priority          : -1
        Description       :
        NumberPattern     : ^(\+1[0-9]{10})$
        PstnUsages        : {}
        PstnGatewayList   : {}
        Name              : global
        SuppressCallerId  :
        AlternateCallerId :

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Подробные сведения см. в разделе <a href="lync-server-2013-voice-routes.md">Маршруты голосовых вызовов в Lync Server 2013</a> документации по планированию.</td>
</tr>
</tbody>
</table>


## Содержание

  - [Создание голосового маршрута в Lync Server 2013](lync-server-2013-create-a-voice-route.md)

  - [Изменение голосового маршрута в Lync Server 2013](lync-server-2013-modify-a-voice-route.md)

## См. также

#### Другие ресурсы

[Управление маршрутизацией голосовой связи в Lync Server 2013](lync-server-2013-managing-voice-routing.md)

