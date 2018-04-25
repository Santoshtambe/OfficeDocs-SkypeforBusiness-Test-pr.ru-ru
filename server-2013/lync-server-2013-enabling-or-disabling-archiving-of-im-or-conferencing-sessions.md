﻿---
title: Включение или отключение архивации мгновенных сообщений или сеансов конференц-связи
TOCTitle: Включение или отключение архивации мгновенных сообщений или сеансов конференц-связи
ms:assetid: aa4b5983-dbe1-4d64-8a18-fe2c33994e94
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg182567(v=OCS.15)
ms:contentKeyID: 49310809
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Включение или отключение архивации мгновенных сообщений или сеансов конференц-связи

 

_**Дата изменения раздела:** 2012-10-10_

Чтобы включить или отключить архивацию сеансов обмена мгновенными сообщениями, конференций или обоих, используйте конфигурации архивации на панели управления Lync Server 2013. Доступны следующие конфигурации архивации:

  - Глобальная конфигурация, которая создается по умолчанию при развертывании Lync Server 2013.

  - Конфигурации на уровне сайта и пула (необязательные), которые вы можете создать и использовать для указания реализации архивации для определенных сайтов или пулов.

Первичная настройка конфигураций архивации выполняется при развертывании архивации, однако изменение, добавление и удаление конфигураций доступно только после развертывания. Дополнительные сведения о реализации конфигураций архивации, включая сведения о доступных параметрах и иерархии конфигураций архивации, см. в разделе [Принцип работы архивации в Lync Server 2013](lync-server-2013-how-archiving-works.md) документации по планированию, развертыванию или операциям.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Перед использованием архивации необходимо настроить политики архивации, которые позволяют включать и отключать архивацию для внутренних коммуникаций, внешних коммуникаций или коммуникаций обоих типов для пользователей Lync Server 2013. По умолчанию для внутренних и внешних коммуникаций архивация отключена. Перед включением архивации с помощью политик необходимо указать конфигурации архивации для развертывания, а также для сайтов и пулов при необходимости. Дополнительные сведения о включении архивации см. в разделе <a href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Настройка и назначение политик архивации</a> документации по развертыванию.<br />
Если после развертывания архивации вы решили использовать интеграцию Microsoft Exchange для хранения данных и файлов архивации на серверах Exchange 2013 и все ваши пользователи расположены на серверах Exchange 2013, вам потребуется удалить конфигурацию базы данных SQL Server из топологии. Для выполнения этой задачи необходимо использовать топологий. Дополнительные сведения см. в разделе <a href="lync-server-2013-changing-archiving-database-options.md">Изменение параметров базы данных для архивации в Lync Server 2013</a> документации по операциям.</td>
</tr>
</tbody>
</table>


## Включение и отключение архивации сеансов обмена мгновенными сообщениями и конференций

1.  Войдите на любой компьютер во внутреннем развертывании с использованием учетной записи пользователя, назначенной роли CsArchivingAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  На левой панели навигации щелкните **Мониторинг и архивация**, а затем щелкните **Конфигурация архивации**.

4.  В списке конфигураций архивации выберите глобальную конфигурацию, конфигурацию на уровне сайта или пула, щелкните **Edit** (Изменить), щелкните **Show details** (Показать сведения) и затем выполните следующие действия:
    
      - Чтобы включить только архивацию сеансов обмена мгновенными сообщениями, щелкните **Archive IM sessions** (Архивировать сеансы обмена мгновенными сообщениями).
    
      - Чтобы включить архивацию сеансов обмена мгновенными сообщениями и конференций, щелкните **Archive IM and conferencing sessions** (Архивировать сеансы обмена мгновенными сообщениями и конференций).
    
      - Чтобы отключить архивацию, щелкните **Disable archiving** (Отключить архивацию).

5.  Щелкните **Commit** (Применить).

## См. также

#### Другие ресурсы

[Управление параметрами конфигурации архивации для организации, сайтов и пулов в Lync Server 2013](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)  
[Настройка и назначение политик архивации](lync-server-2013-configuring-and-assigning-archiving-policies.md)
