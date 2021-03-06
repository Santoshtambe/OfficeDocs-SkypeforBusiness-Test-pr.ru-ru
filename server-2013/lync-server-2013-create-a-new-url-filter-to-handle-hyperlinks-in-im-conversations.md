﻿---
title: Создание нового фильтра URL-адресов для управления гиперссылками в сеансах обмена мгновенными сообщениями
TOCTitle: Создание нового фильтра URL-адресов для управления гиперссылками в сеансах обмена мгновенными сообщениями
ms:assetid: d0ee01e5-f039-4a34-ac9d-659fe4e9e879
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg182590(v=OCS.15)
ms:contentKeyID: 49311239
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Создание нового фильтра URL-адресов для управления гиперссылками в сеансах обмена мгновенными сообщениями

 

_**Дата изменения раздела:** 2012-09-26_

Кроме изменения глобального фильтра URL-адресов, можно настроить пользовательские фильтры URL-адресов для отдельных сайтов в развертывании Lync Server 2013. Дополнительные сведения о фильтрации URL-адресов см. в разделе [Настройка фильтрации передачи файлов и URL-адресов для обмена мгновенными сообщениями в Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md).

## Создание нового фильтра URL-адресов

1.  Войдите на любой компьютер во внутреннем развертывании с использованием учетной записи пользователя, назначенной роли CsUserAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой области навигации щелкните пункт **Мгновенные сообщения и присутствие**, а затем **Фильтр URL-адресов**.

4.  На странице **Фильтр URL-адресов** нажмите кнопку **Создать**.

5.  В диалоговом окне **Выбор сайта** щелкните сайт, для которого требуется создать фильтр URL-адресов, а затем нажмите кнопку **ОК**.

6.  В диалоговом окне **Создание фильтра URL-адресов** установите флажок **Включить фильтр URL-адресов**, чтобы включить фильтрацию URL-адресов для сайта.

7.  Чтобы заблокировать все активные URL-адреса, которые содержат файл с расширением, заданном в разделе **Расширения типов файлов для блокировки** в окне **Редактирование фильтра файлов**, установите флажок **Блокировать URL-адреса с расширением файлов**.

8.  В раскрывающемся списке **Префикс гиперссылки** выберите вариант, который соответствует тому, как требуется обрабатывать URL-адреса в беседах с обменом мгновенными сообщениями.
    
    Флажок **Разрешить сообщение** позволяет отправку пользователю предупреждающего сообщения, когда отправляются разрешенные для отправки гиперссылки.

9.  Щелкните **Исполнить**.

## См. также

#### Задачи

[Настройка фильтрации передачи файлов и URL-адресов для обмена мгновенными сообщениями в Lync Server 2013](lync-server-2013-configuring-file-transfer-and-url-filtering-for-instant-messaging-im.md)  
[Создание нового фильтра передачи файлов для определенного сайта](lync-server-2013-create-a-new-file-transfer-filter-for-a-specific-site.md)  
[Изменение фильтра передачи файлов по умолчанию](lync-server-2013-modify-the-default-file-transfer-filter.md)  

#### Концепции

[Изменение фильтра URL-адресов по умолчанию](lync-server-2013-modify-the-default-url-filter.md)

