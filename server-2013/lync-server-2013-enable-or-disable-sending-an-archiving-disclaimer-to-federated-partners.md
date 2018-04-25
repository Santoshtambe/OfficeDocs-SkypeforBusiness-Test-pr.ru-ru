﻿---
title: 'Lync Server 2013: включение и отключение отправки отказа от архивирования федеративным партнерам'
TOCTitle: Включение и отключение отправки отказа от архивирования федеративным партнерам
ms:assetid: c8e9a2fa-9dc1-4e4d-919f-56ece8004864
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg182584(v=OCS.15)
ms:contentKeyID: 49311138
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Включение и отключение отправки отказа от архивирования федеративным партнерам в Lync Server 2013

 

_**Дата изменения раздела:** 2013-02-23_

Во время развертывания пограничных серверов и включения федерации для организации должно быть указано, следует ли отправлять федеративным партнерам заявление об отказе для архивации. Если вы выполняете архивацию внешних взаимодействий, то следует включить отправку этого заявления об отказе. С помощью процедуры в этом разделе можно изменить эту конфигурацию.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В следующей процедуре предполагается. что вы уже включили федерацию для организации. Подробные сведения о включении федерации см. в разделе <a href="lync-server-2013-enable-or-disable-remote-user-access.md">Включение или отключения удаленного доступа пользователей в Lync Server 2013</a> документации по развертыванию или документации по операциям.</td>
</tr>
</tbody>
</table>


## Включение и отключение отправки федеративным партнерам заявления об отказе для архивации

1.  Войдите на любой компьютер, находящийся во внутреннем развертывании, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации щелкните элемент **External User Access** (Доступ для внешних пользователей), а потом щелкните элемент **Access Edge Configuration** (Конфигурация сервера пограничного доступа).

4.  На вкладке **конфигурации сервера пограничного доступа** последовательно выберите пункты **Global** (Глобальные параметры), **Edit** (Правка) и **Show details** (Показать подробности).

5.  В диалоговом окне **изменения конфигурации сервера пограничного доступа** в разделе **включения взаимодействий с федеративными пользователями** установите или снимите флажок **Send archiving disclaimer to federated partners** (Отправлять федеративным партнерам заявления об отказе для архивации), чтобы включить или отключить автоматическую отправку этого заявления об отказе.

6.  Щелкните **Исполнить** .

Для разрешения федеративным пользователям взаимодействия с пользователями в вашем развертывании Lync Server 2013 должна быть также настроена по крайней мере одна политика внешнего доступа для поддержки доступа федеративных пользователей. Подробные сведения см. в разделе [Управление федеративными XMPP-партнерами в Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md) документации по развертыванию или документации по операциям. Подробные сведения об управлении доступом для конкретных федеративных доменов см. в разделе [Настройка поддержки для разрешенных внешних доменов в Lync Server 2013](lync-server-2013-configure-support-for-allowed-external-domains.md) документации по развертыванию или документации по операциям.

## Включение и отключение заявления об отказе с помощью командлетов Windows PowerShell

Использованием заявления об отказе можно также управлять с помощью Windows PowerShell и командлета Set-CsAccessEdgeConfiguration. Этот командлет можно запустить либо из командная консоль Lync Server 2013, либо из удаленного сеанса Windows PowerShell. Дополнительные сведения об использовании Windows PowerShell в удаленном режиме для подключения к Lync Server см. статью блога Lync Server Windows PowerShell "Краткое руководство: управление Microsoft Lync Server 2010 в удаленном режиме с помощью PowerShell" по адресу [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Включение заявления об отказе

  - Чтобы включить заявление об отказе для архивации, установите свойство **EnableArchivingDisclaimer** в значение True ($True):
    
        Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $True

## Отключение заявления об отказе

  - Чтобы отключить заявление об отказе для архивации, установите свойство **EnableArchivingDisclaimer** в значение False ($False):
    
        Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $False
