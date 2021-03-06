﻿---
title: 'Lync Server 2013: включение службы E9-1-1'
TOCTitle: Включение службы E9-1-1
ms:assetid: 3cc64f5b-492e-4c47-9713-3c376f2aad02
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg425892(v=OCS.15)
ms:contentKeyID: 49309523
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Включение службы E9-1-1 в Lync Server 2013

 

_**Дата изменения раздела:** 2012-06-06_

Во время регистрации клиента Lync Server использует политику определения местоположения, чтобы настроить свойства E9-1-1 для пользователей с включенной поддержкой корпоративной голосовой связи. Эта политика содержит параметры, которые определяют способ реализации E9-1-1. Например, политика определения местоположения содержит сведения о строке набора номера экстренного вызова и о том, требуется ли пользователю вручную указывать местоположение, если службе информирования о местонахождении не удается определить его автоматически. Полное описание политики определения местоположения см. в разделе [Определение политики расположения для Lync Server 2013](lync-server-2013-defining-the-location-policy.md).

Lync Server может назначать политику определения местоположения клиентам на основе подсети или пользователям на основе глобальной политики, политики на сайт или политики на пользователя. Чтобы облегчить принятие решения о способе реализации такой поддержки для пользователей, вам следует сначала ответить на следующие вопросы.

  - **Вы планируете включить поддержку для всех пользователей или ограничить ее отдельными географическими областями в рамках предприятия?**  
    Вы можете назначить местоположение всем пользователям предприятия с помощью глобальной политики определения местоположения. Однако, назначив политику определения местоположения сетевому узлу Lync Server и затем добавив на него подсети, вы можете обеспечить поддержку E9-1-1 только для выбранных расположений в рамках предприятия и задавать режим маршрутизации E9-1-1 для отдельных сайтов.

<!-- end list -->

  - **Планируете ли вы включить поддержку для отдельных пользователей с помощью ?**  
    Для настройки поддержки E9-1-1 вы можете назначать политики определения местоположения непосредственно отдельным пользователям или объектам-контактам телефона общего доступа.

<!-- end list -->

  - **Следует ли включать поддержку E9-1-1 для клиентов, которые находятся в роуминге за пределами сети или подключаются из неопределенной подсети?**  
    Если пользователям назначается глобальная политика, политика на сайт или политика на пользователя, им может потребоваться вручную указывать местоположение в клиенте, если он расположен за пределами определенной подсети или службе информирования о местонахождении не удалось определить местоположение. Дополнительные сведения см. в разделе [Определение пользовательского интерфейса для получения местоположения вручную в Lync Server 2013](lync-server-2013-defining-the-user-experience-for-manually-acquiring-a-location.md).

