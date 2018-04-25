﻿---
title: Настройка параметров архивации для сайта
TOCTitle: Настройка параметров архивации для сайта
ms:assetid: 59b48fd9-d5fc-40b4-abae-e9cf89ee5573
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ204930(v=OCS.15)
ms:contentKeyID: 49309861
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка параметров архивации для сайта

 

_**Дата изменения раздела:** 2012-10-09_

Чтобы задать параметры архивации, которые должны применяться к определенным сайтам, создайте и настройте параметры в конфигурации архивации для каждого из этих сайтов. Конфигурация сайта переопределяет глобальную конфигурацию, но только для сайта, указанного в конфигурации. Конфигурации пулов переопределяют конфигурации сайтов.

Подробные сведения о том, как работают конфигурации архивации, включая информацию об иерархии конфигураций глобального уровня, сайтов и пулов, см. в разделе [Принцип работы архивации в Lync Server 2013](lync-server-2013-how-archiving-works.md) документации по планированию, развертыванию или эксплуатации.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Перед тем как включать архивацию, необходимо указать все соответствующие параметры в конфигурациях архивации.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Для активации архивации необходимо сначала указать политики архивации для управления архивацией внутренних и внешних взаимодействий на глобальном уровне и при необходимости на уровне сайтов и пользователей. При настройке политик на уровне пользователей необходимо также назначить пользовательские политики определенным пользователям. Создание и настройка политик архивации рассматривается в разделе <a href="lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md">Управление архивацией внутренних и внешних коммуникаций в Lync Server 2013</a> документации по операциям.</td>
</tr>
</tbody>
</table>


## Настройка параметров архивации на уровне сайта

1.  Используя учетную запись пользователя, назначенную роли CsArchivingAdministrator или CsAdministrator, войдите на любой компьютер во внутреннем развертывании.

2.  Откройте окно браузера и введите URL-адрес администратора, чтобы открыть панель управления Lync Server 2013. Дополнительные сведения о различных методах запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  На левой панели навигации щелкните **Мониторинг и архивация**, а затем щелкните **Конфигурация архивации**.

4.  На странице **Конфигурация архивации** щелкните **Создать** и затем выберите пункт **Конфигурация сайта**.

5.  В разделе **Выбор сайта** выберите сайт, для которого нужно настроить архивацию.

6.  На странице **Новый параметр архивации** в раскрывающемся списке **Параметр архивации** выполните одно из следующих действий.
    
      - Чтобы включить архивацию только для сеансов обмена мгновенными сообщениями, выберите пункт **Архивировать сеансы обмена мгновенными сообщениями**.
    
      - Чтобы включить архивацию как для сеансов обмена мгновенными сообщениями, так и для конференций, выберите пункт **Архивировать сеансы обмена мгновенными сообщениями и веб-конференций**.
    
      - Чтобы отключить архивацию для политики, щелкните **Отключить архивацию**.

7.  Кроме того, на странице **Новый параметр архивации** выполните следующие действия.
    
      - Чтобы заблокировать действия, если архивация невозможна, установите флажок **Блокировать сеансы обмена мгновенными сообщениями и конференц-связи при сбое архивации**.
    
      - Чтобы использовать Microsoft Exchange Server для хранения данных архивации, установите флажок **Интеграция с Microsoft Exchange**.
    
      - Чтобы включить очистку данных, установите флажок **Включить очистку данных архивации** и выполните одно из следующих действий.
        
          - Чтобы задать очистку после определенного числа дней, щелкните **Очищать экспортированные и сохраненные данные архивации после максимального срока (дней)** и укажите число дней.
        
          - Чтобы задать очистку только экспортированных данных архивации, щелкните **Очищать только экспортированные данные архивации**.

8.  Нажмите кнопку **Сохранить**.
