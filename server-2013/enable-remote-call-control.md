﻿---
title: Включение функции удаленного управления звонками
TOCTitle: Включение функции удаленного управления звонками
ms:assetid: 0b91d418-e6ed-4556-97af-e8523e01f249
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204664(v=OCS.15)
ms:contentKeyID: 49308903
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Включение функции удаленного управления звонками

 

_**Дата изменения раздела:** 2012-10-02_

Дистанционное управление вызовами позволяет пользователям управлять телефонами своей УАТС (учрежденческой АТС) с помощью Lync Server 2013. Если дистанционное управление вызовами развернуто в унаследованной среде и требуется перенести такое управление в Lync Server 2013, потребуется выполнить следующие задачи:

1.  Установить шлюз SIP/CSTA и настроить его для связи с УАТС. Этот шаг необходимо выполнить при развертывании пилотного пула Lync Server 2013.

2.  После объединения топологии и миграции политик и настроек настроить Lync Server 2013 для маршрутизации CSTA-запросов в шлюз SIP/CSTA. Этот шаг выполняется вручную после миграции в автоматическом режиме. Чтобы настроить маршрутизацию CSTA-запросов, выполните следующие действия:
    
      - Удалите унаследованные записи санкционированных узлов (известные как *записи доверенных серверов* в Lync Server 2013). Если выполняется миграция пользователей из унаследованного развертывания, убедитесь, что удаляете все существующие записи санкционированных узлов, созданные для шлюза SIP/CSTA, прежде чем настроить новые записи доверенных приложений в пилотном пуле Lync Server 2013. Подробности о том, как удалить унаследованные записи санкционированных узлов см.в разделе [Удаление записи авторизованного размещения](remove-an-authorized-host-entry.md).
    
      - Настройте для дистанционного управления вызовами статический маршрут. Можно настроить статический маршрут для отдельных пулов, которые согласно вашим планам должны поддерживать дистанционное управление вызовами, или можно настроить глобальный статический маршрут, чтобы каждый пул, который не сконфигурирован со статическим маршрутом на уровне пулов, использовал глобальный статический маршрут. Сведения о настройке статического маршрута см. в разделе [Настройка статического маршрута для дистанционного управления вызовами в Lync Server 2013](lync-server-2013-configure-a-static-route-for-remote-call-control.md) в документации по развертыванию.
    
      - Настройте запись доверенного приложения для дистанционного управления вызовами в каждом пуле, который согласно вашим планам должен поддерживать дистанционное управление вызовами. Сведения о настройке записи доверенного приложения см. в разделе [Настройка записи доверенного приложения для удаленного управления звонками в Lync Server 2013](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md) в документации по развертыванию.

3.  Если развернут шлюз SIP/CSTA, использующий протокол управления передачей (TCP) для подключения к Lync Server 2013, определите IP-адрес шлюза в построителе топологий. Сведения об определении IP-адреса см. в разделе [Определение IP-адреса для шлюза SIP/CSTA в Lync Server 2013](lync-server-2013-define-a-sip-csta-gateway-ip-address.md) в документации по развертыванию.

4.  Настройте пользователей Lync 2013 для дистанционного управления вызовами путем включения дистанционного управления вызовами и назначения универсального идентификатора ресурса (URI) сервера линии и URI линии. Когда выполняется миграция пользователей из унаследованного развертывания в Lync Server 2013, настройки дистанционного управления вызовами мигрируют вместе с другими настройками пользователей.

5.  Если в унаследованном развертывании настроены правила нормализации телефонных номеров адресной книги, после завершения автоматической миграции политик и настроек требуется выполнить некоторые задачи вручную, чтобы выполнить миграцию настроенных правил нормализации. Если правила нормализации не настраивались, миграция адресной книги выполняется вместе с остальной топологией. Сведения о миграции вручную настроенных правил нормализации см. в разделе [Перенос адресной книги](migrate-address-book_1.md).

