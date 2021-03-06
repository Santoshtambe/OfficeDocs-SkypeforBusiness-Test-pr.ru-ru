﻿---
title: Рекомендации по работе с сервером сохраняемого чата
TOCTitle: Рекомендации по работе с сервером сохраняемого чата
ms:assetid: dc18e7f7-599b-4d32-abf7-cd9e691426a2
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398970(v=OCS.15)
ms:contentKeyID: 49311373
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Рекомендации по работе с сервером сохраняемого чата

 

_**Дата изменения раздела:** 2012-10-06_

При создании категорий и чатов сохраняемый сеанс беседы и проектировании областей и членства следующие советы могут оказаться полезными в ходе планирования.

  - Если в организации не требуется создавать ограничение в соответствии с корпоративными стандартами, не сужайте область в дереве категорий. Поместите всех пользователей в области в одну категорию и создайте все чаты в этой категории. Затем используйте списки членства для предоставления или ограничения доступа к каждому чату.

  - В большинстве случаев требуется разрешить пользователям создание новых чатов, чтобы они могли начать обсуждение новых тем в любой момент. Это можно сделать, настроив список **Creators** так, чтобы его содержимое совпадало со списком **AllowedMembers**. Однако, если требуется, чтобы только центральная служба поддержки или назначенные пользователи могли создавать чаты, настройте список **Creators** как соответствующее подмножество.

  - Задайте для каждого чата полное имя и краткое описание, определяющее его назначение в организации. Поскольку пользователи не могут видеть имя категории при использовании чата, имя категории не поможет пользователям определить нужный форум для чата.

  - Может потребоваться создать настраиваемый рабочий процесс создания чатов при наличии определенных соглашений о наименовании или других средств контроля доступа или проверок, которые требуется внедрить. Конфигурация сохраняемый сеанс беседы позволяет настраивать параметр **RoomManagementUrl** для размещаемых компонентов. Например, когда пользователи нажимают кнопку **Create a room** (Создать чат) в клиенте Lync, они могут быть перенаправлены на ваше настраиваемое решение.

  - Создайте различные надстройки, которые помогут улучшить работу с чатами, например, добавляя в них важные бизнес-данные. Администраторы должны зарегистрировать надстройки, которые они хотят разрешить в системе. Руководители и авторы могут выбирать надстройки из представленного списка и связывать их с чатами.

## См. также

#### Другие ресурсы

[Управление категориями, чатами и надстройками в Lync Server 2013](lync-server-2013-managing-categories-rooms-and-add-ins.md)

