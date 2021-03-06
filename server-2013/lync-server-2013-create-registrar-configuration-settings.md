﻿---
title: Создание параметров конфигурации регистратора
TOCTitle: Создание параметров конфигурации регистратора
ms:assetid: eddfbdd2-cfd0-4c03-986e-443d6728db7d
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg182601(v=OCS.15)
ms:contentKeyID: 49311580
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Создание параметров конфигурации регистратора

 

_**Дата изменения раздела:** 2013-03-17_

Регистратор можно использовать для настройки способов проверки подлинности прокси-сервера. Заданный протокол проверки подлинности определяет, какой тип запросов серверы в пуле выдают клиентам. Далее приводятся доступные протоколы.

  - **Kerberos**   это строжайшая схема проверки подлинности на основе паролей, доступная клиентам, но обычно она доступна только клиентам предприятия, поскольку требует подключение клиента к центру распространения ключей (контроллеру домена Kerberos). Этот протокол подходит, если сервер проверяет подлинность только клиентов предприятия.

  - **NTLM**   это проверка подлинности на основе паролей, доступная клиентам, использующим в пароле схему хэширования с запросом и подтверждением. Это единственная форма проверки подлинности, доступная клиентам без подключения к центру распространения ключей (контроллеру домена Kerberos), таким как удаленные пользователи. Если сервер проверяет подлинность только удаленных пользователей, то следует выбрать NTLM.

  - **Проверка подлинности с помощью сертификата**   — это новый способ проверки подлинности, когда серверу необходимо получить сертификаты от клиентов Lync Phone Edition, телефонов общего пользования и Lync 2013. В клиентах Lync Phone Edition, после того как пользователь выполняет вход и успешно проходит проверку подлинности, предоставив персональный идентификационный номер (ПИН-код), сервер Lync Server 2013 подготавливает SIP URI для телефона, а также подготавливает подписанный сертификат или Lync Server сертификат пользователя, который идентифицирует пользователя Joe (Ex: SN=joe@contoso.com ) для телефона. Этот сертификат используется для проверки подлинности с помощью регистратора и веб-служб

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если сервер поддерживает проверку подлинности для удаленных клиентов и для клиентов предприятия, рекомендуется включить и Kerberos, и NTLM. Пограничный сервер и внутренние серверы взаимодействуют, чтобы убедиться, что для удаленных клиентов предлагается только проверка подлинности NTLM. Если на этих серверах включен только Kerberos, они не могут выполнять проверку подлинности удаленных пользователей. Если пользователи предприятия также проходят проверку подлинности на сервере, то используется Kerberos.</td>
</tr>
</tbody>
</table>


Для создания нового регистратора выполните следующие действия.

## Создание регистратора

1.  Войдите на любой компьютер, подключенный к сети, где развернут Lync Server 2013, с использованием учетной записи, входящей в группу RTCUniversalServerAdmins (или имеющей равнозначные права пользователя) либо назначенной роли CsServerAdministrator или CsAdministrator.

2.  Откройте окно браузера и введите URL-адрес для администрирования, чтобы открыть панель управления Lync Server. Дополнительные сведения о различных методах, которые можно использовать для запуска панели управления Lync Server см. в разделе [Открытие средств администрирования Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  В левой панели навигации последовательно выберите пункты **Безопасность** и **Регистратор**.

4.  На странице **регистратора** нажмите **Создать**.

5.  В поле **выбора службы** выберите службу, к которой должен быть применен регистратор, и нажмите кнопку **ОК**.

6.  В разделе **Настройка нового регистратора** установите какие-либо из следующих флажков, в зависимости от возможностей клиентов и поддержки в среде.
    
      - **Включить проверку подлинности Kerberos** — чтобы серверы в пуле выдавали запросы с использованием проверки подлинности Kerberos.
    
      - **Включить проверку подлинности NTLM** — чтобы серверы в пуле выдавали запросы с использованием NTLM.
    
      - **Включить проверку подлинности с помощью сертификата** — чтобы серверы в пуле выдавали сертификаты клиентам.

7.  Нажмите кнопку **Зафиксировать**.

