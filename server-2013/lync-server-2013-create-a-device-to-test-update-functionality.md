﻿---
title: Создание устройства для проверки возможности обновления
TOCTitle: Создание устройства для проверки возможности обновления
ms:assetid: ce509fd1-17b3-4b78-b269-fe5d06fe2e1d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg182587(v=OCS.15)
ms:contentKeyID: 49311186
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Создание устройства для проверки возможности обновления

 

_**Дата изменения раздела:** 2013-02-23_

Можно добавить тестовое устройство на страницу **Тестовое устройство**, а затем использовать это устройство для проверки функционирования новых обновлений перед развертыванием обновлений на производственных устройствах. Можно выполнять тестирование устройства на глобальном уровне (во всей среде Lync Server) или на уровне отдельного сайта. Идентификация тестового устройства осуществляется по адресу Media Access Control (MAC) или серийному номеру. Когда вы добавляете устройство, оно отображается в списке на странице **Тестовое устройство** панели управления Lync Server.

## Добавление тестового устройства

1.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  На левой панели навигации щелкните **Клиенты**, а затем щелкните **Тестовое устройство**.

3.  Щелкните **Создать**, а затем щелкните либо **Тестовое устройство для глобального уровня** или **Тестовое устройство для сайта**.

4.  Выполните одно из следующих действий:
    
      - Если выбрано **Тестовое устройство для глобального уровня**, перейдите к следующему шагу.
    
      - Если выбрано **Тестовое устройство для сайта**, выберите сайт в списке доступных сайтов, а затем щелкните **ОК**.

5.  В разделе **Новое тестовое устройство** введите имя устройства в поле **Имя устройства**.

6.  В области **Тип идентификатора** щелкните либо **MAC-адрес**, либо **Серийный номер**.

7.  В поле **Уникальный идентификатор** введите MAC-адрес или серийный номер устройства.

8.  Щелкните **Исполнить**.

## Создание тестовых устройств с помощью командлетов Windows PowerShell

Тестовые устройства можно создать с помощью Windows PowerShell и командлета New-CsTestDevice. Этот командлет можно запустить из командная консоль Lync Server 2013 или из удаленного сеанса Windows PowerShell. Дополнительные сведения об использовании Windows PowerShell в удаленном режиме для подключения к Lync Server см. статью блога Lync Server Windows PowerShell "Краткое руководство: управление Microsoft Lync Server 2010 в удаленном режиме с помощью PowerShell" по адресу [http://go.microsoft.com/fwlink/p/?linkId=255876](http://go.microsoft.com/fwlink/p/?linkid=255876).

При создании тестовых устройств с помощью данного командлета необходимо выполнить два действия:

  - Укажите значения MACAddress или SerialNumber для параметра IdentifierType.

  - Включите область при указании идентификатора устройства. Для создания нового устройства на глобальном уровне используйте синтаксис, аналогичный следующему:
    
        -Identity "global/WindowsPhone"
    
    Для создания текстового устройства на уровне сайта используйте синтаксис, аналогичный следующему:
    
        -Identity "site:Redmond/WindowsPhone"

## Создание тестового устройства с помощью MAC-адреса

  - Эта команда создает тестового устройства на глобальном уровне и использует MAC-адрес в качестве значения для параметра IdentifierType:
    
        New-CsTestDevice -Identity "global/WindowsPhone" -IdentifierType "MACAddress" -Identifier "01:02:03:04:05:06"

## Создание тестового устройства с помощью серийного номера

  - Эта команда создает новое тестовое устройство на уровне сайта (для сайта Redmond) и использует серийный номер в качестве значения для параметра IdentifierType:
    
        New-CsTestDevice -Identity "site:Redmond/WindowsPhone" -IdentifierType "SerialNumber" -Identifier "01ABC5419JKR55T"

Для получения дополнительной информации см. раздел справки по командлету [New-CsTestDevice](new-cstestdevice.md).

