﻿---
title: Создание или изменение правила политики версий клиентов
TOCTitle: Создание или изменение правила политики версий клиентов
ms:assetid: 6f879d99-8401-41e0-a562-195c890d63ea
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ898478(v=OCS.15)
ms:contentKeyID: 52058256
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Создание или изменение правила политики версий клиентов

 

_**Дата изменения раздела:** 2013-01-21_

Правила политики версий клиентов определяют действия, которые следует предпринять при попытке пользователей выполнить вход с использованием определенных клиентов и их версий. Вы можете создавать или изменять отдельные правила для политики версий клиентов с помощью панели управления Lync Server 2013.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Правила перечислены в списке в порядке приоритета. Например, если есть правило, которое разрешает подключение клиентов с версией 1.5, за которым следует правило, блокирующее клиенты с версией ниже 2.0, преимуществом будет пользоваться первое правило, поэтому клиентам версии 1.5 будет разрешено выполнять подключение.</td>
</tr>
</tbody>
</table>


## Создание или изменение политик версий клиентов с помощью панели управления Lync Server

1.  [Создание или изменение политики версий клиентов](lync-server-2013-create-or-modify-a-new-client-version-policy.md) с помощью панели управления Lync Server.

2.  На странице **Edit Client Version Policy** (Изменение политики версий клиентов) выполните одно из следующих действий.
    
      - Нажмите кнопку **New** (Создать), чтобы создать новое правило версий клиентов.
    
      - Выберите один из заданных типов клиентов в списке, а затем щелкните **Show details** (Показать подробности).
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Чтобы указать тип клиента, можно использовать подстановочные знаки.</td>
    </tr>
    </tbody>
    </table>


3.  В поле **User agent** (Агент пользователя) выберите тип клиента.

4.  В области **Version number** (Номер версии) выполните следующие действия.
    
      - В поле **Major version** (Основной номер версии) введите число, соответствующее основной версии клиента.
    
      - В поле **Minor version** (Дополнительный номер версии) введите число, соответствующее дополнительной версии клиента.
    
      - В поле **Build** (Построение) введите число, которое соответствует основной и дополнительной версии клиента.
    
      - В поле **Update** (Обновление) введите число, соответствующее обновленной версии клиента.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Чтобы указать версию клиента, можно использовать подстановочные знаки.</td>
    </tr>
    </tbody>
    </table>


5.  Чтобы указать операцию сопоставления для версии клиента, указанной в предыдущих действиях, в поле **Comparison operation** (Операция сравнения) выберите один из следующих вариантов:
    
      - **Same as** (Равняется)
    
      - **Is not** (Не равняется)
    
      - **Newer than** (Новее чем)
    
      - **Newer than or same as** (Не старее чем)
    
      - **Older than** (Старее чем)
    
      - **Older than or same as** (Не новее чем)

6.  Чтобы указать действие, которое будет выполняться при удовлетворении условий предыдущего действия, в области **Action** (Действие) выберите один из вариантов:
    
      - Чтобы разрешить клиенту вход в систему, выберите параметр **Allow** (Разрешить).
    
      - Чтобы разрешить клиенту вход в систему и получение обновлений из службы Windows Server Update Service или Центра обновления Майкрософт, выберите **Allow and Upgrade** (Разрешить и обновить). Это действие доступно, только если выбран агент пользователя **OC**.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>В случае выбора этого действия при следующем входе пользователя в систему Lync 2013 отображается уведомление, сообщающее о наличии обновлений, даже если обновления еще не выпущены в службе Windows Server Update Service или в Центре обновления Майкрософт. Чтобы избежать противоречий, необходимо выбирать это действие только после того, как станут доступны обновления.</td>
        </tr>
        </tbody>
        </table>
    
      - Чтобы разрешить клиенту выполнять вход в систему и выводить на экран сообщение о расположении для загрузки новой версии клиента, выберите параметр **Allow with URL** (Разрешить с URL-адресом). URL-адрес указывается позднее в этой процедуре.
    
      - Чтобы запретить клиенту вход в систему, выберите параметр **Block** (Блокировать).
    
      - Чтобы запретить клиенту вход в систему и разрешить получение обновлений из службы Windows Server Update Service или Центра обновления Майкрософт, выберите параметр **Block and Upgrade** (Блокировать и обновлять). Это действие доступно, только если выбран агент пользователя **OC**.
    
      - Чтобы запретить клиенту выполнять вход в систему и выводить на экран сообщение о расположении для загрузки новой версии клиента, выберите параметр **Block with URL** (Блокировать с URL-адресом). URL-адрес указывается позднее в этой процедуре.

7.  (Дополнительно). Если в предыдущем действии выбран параметр **Allow with URL** (Разрешить с URL-адресом) или **Block with URL** (Блокировать с URL-адресом), в поле **URL** (URL-адрес) введите URL-адрес для загрузки клиента, чтобы включить его в сообщение.

8.  Нажмите кнопку **OK** (ОК), а затем кнопку **Commit** (Подтвердить).

