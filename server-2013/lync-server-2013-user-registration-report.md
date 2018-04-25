﻿---
title: 'Lync Server 2013: отчет о регистрации пользователей'
TOCTitle: Отчет о регистрации пользователей
ms:assetid: 151d5cc9-cc1b-4cfa-be9c-55ebe321f7a4
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg558614(v=OCS.15)
ms:contentKeyID: 49309038
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Отчет о регистрации пользователей в Lync Server 2013

 

_**Дата изменения раздела:** 2015-03-09_

В отчете о регистрации пользователей содержится обзор действий пользователей по регистрации в системе, а именно сведения о количестве пользователей, входивших в систему Microsoft Lync Server 2013 в течение заданного периода времени (ежечасно, ежедневно, еженедельно, ежемесячно). Следует иметь в виду, что в отчете лишь сообщается, сколько людей входило в систему. В нем не указывается, *какие* люди входили в систему. В отчетах мониторинга отсутствуют сведения о том, какие конкретные люди пользовались сервером Lync Server 2013 (и какие люди не пользовались). Тем не менее с помощью отчета об активности пользователей можно получить грубую оценку пользовательской информации.

При предоставлении сведений о входах пользователей в систему в отчете о регистрации пользователей делается два важных разграничения. Во-первых, в отчете входы в систему разбиваются на две основные категории: внутренние и внешние входы в систему. Внутренние входы представляют пользователей, вошедших в систему с внутренней стороны брандмауэра организации (то есть, с компьютера, подключенного к корпоративной сети). Внешние входы представляют пользователей, вошедших в систему с внешней стороны брандмауэра через сервер (например, пользователь, вошедший в систему из интернет-кафе, подсчитывается как внешний вход). Если необходимо узнать, сколько пользователей входит в систему с внешней стороны брандмауэра, эти сведения можно найти в отчете о регистрации пользователей.

Кроме того, в отчете о регистрации пользователей отмечается, сколько *активных* пользователей присутствовало в течение заданного периода времени. Активный пользователь – это пользователь, обменивающийся мгновенными сообщениями (IM), участвующий в собрании Собрание Lync, выполняющий или принимающий телефонные вызовы либо использующий иным образом сервер Lync Server в течение этого периода времени. Такой пользователь отличается от пользователя, вошедшего в систему, но не проявлявшего никакой активности в системе.

## Доступ к отчету о регистрации пользователей

Доступ к отчету о регистрации пользователей предоставляется только на домашней странице отчетов мониторинга. Отчет о регистрации пользователей не связан с какими-либо другими отчетами.

## Оптимальное использование отчета о регистрации пользователей

После развертывания Lync Server часто возникает следующий вопрос: как узнать, применяют ли пользователи эту новую технологию? Хотя в этом отношении есть определенные ограничения, отчет о регистрации пользователей позволяет ответить на этот вопрос. Чтобы определить, применяют ли пользователи Lync Server, необходимо выполнить две операции. Во-первых, нужно получить значение показателя уникальных входов пользователей из отчета о регистрации пользователей. Это значение говорит, сколько различных пользователей вошли в систему Lync Server.

Для сравнения, показатель общего числа входов отражает общее количество входов, выполненных пользователями на сервере Lync Server. Например, предположим, что Кен Майер заходил в систему на сервере Lync Server пять раз в течение дня. В этом случае для Кен Майера было бы подсчитано пять отдельных сеансов входа в показателе общего числа входов, но лишь один зарегистрированный пользователь в показателе уникальных зарегистрированных пользователей. Аналогично, пользователи нередко входят в систему с нескольких устройств или из нескольких мест. Например, пользователь может войти в систему, пользуясь своим настольным компьютером, ноутбуком, и к тому же, у него может быть IP-телефон, который автоматически регистрируется на сервере Lync Server. В этом примере имеется один уникальный пользователь с тремя входами в систему.

Для дальнейшего пояснения разницы между общим количеством входов и уникальными входами рассмотрим входы в систему для заданного периода времени, приведенные в следующей таблице.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>User</th>
<th>Время входа</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Артем Кузнецов</p></td>
<td><p>7/7/2012 08:45:00</p></td>
</tr>
<tr class="even">
<td><p>Артем Кузнецов</p></td>
<td><p>7/7/2012 08:46:00</p></td>
</tr>
<tr class="odd">
<td><p>Ольга Зуева</p></td>
<td><p>7/7/2012 09:17:00</p></td>
</tr>
<tr class="even">
<td><p>Артем Кузнецов</p></td>
<td><p>7/7/2012 09:22:00</p></td>
</tr>
<tr class="odd">
<td><p>Ольга Зуева</p></td>
<td><p>7/7/2012 09:31:00</p></td>
</tr>
</tbody>
</table>


Обратите внимание, что общее количество входов в систему равно пяти; однако существует только два уникальных регистрировавшихся пользователя: Кен Майер (входивший в систему три раза) и Пилар Аккерман (заходивший в систему дважды). В этом разница между входами в систему и уникальными регистрировавшимися пользователями.

Помимо знания числа уникальных входов в систему необходимо знать общее число пользователей, активированных для Lync Server. Это значение можно получить, открыв командная консоль Lync Server 2013 и выполнив следующую команду Windows PowerShell:

    (Get-CsUser).Count

Если предыдущая команда возвращает значение 1236, а показателем количества уникальных регистрировавшихся пользователей возвращается среднее значение 667, это наводит на мысль, что чуть больше половины пользователей, поддерживаемых Lync, фактически входят в систему каждый день (то есть, 667 разделить на 1236, что приблизительно равно 54%).

<table>
<thead>
<tr class="header">
<th><img src="images/Gg412910.warning(OCS.15).gif" title="warning" alt="warning" />Предупреждение</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Следует иметь в виду, что показателями входов учитываются пользователи, которые на самом деле входили в систему в указанный период времени. Они не учитывают пользователей, которые уже были зарегистрированы в системе. Например, если показатель количества уникальных регистрировавшихся пользователей равен 667 и имеется 1236 пользователей, это свидетельствует о том, что около половины пользователей входят в систему. Однако предположим, что 300 пользователей уже находились в системе на момент, когда началась проверка данных о регистрации. Это означало бы, что фактически почти 1000 пользователей вошли в систему Lync Server, что в свою очередь означало бы, что в систему вошли близко к 80% пользователей.</td>
</tr>
</tbody>
</table>


Следует также сравнить значение показателя количества уникальных регистрировавшихся пользователей со значением показателя количества уникальных активных пользователей. Показатель количества уникальных активных пользователей сообщает, сколько уникальных пользователей действительно пользовались Lync Server: они выполняли телефонные вызовы, присоединялись к собранию Собрание Lync или участвовали в сеансе обмена мгновенными сообщениями. Это полезная информация, поскольку приложение Microsoft Lync 2013 может быть настроено так, чтобы запускаться каждый раз, когда пользователь запускает ОС Windows. По этой причине может быть большое число пользователей, которые автоматически регистрируются в Lync, когда они входят в Windows каждый день, но затем никогда не используют Lync Server в течение этого периода времени.

Кроме того, показатель количества уникальных активных пользователей предоставляет более содержательные данные в организации, где пользователи обычно не выходят из Windows в конце дня. Вместо этого они просто блокируют свои компьютеры и оставляют ОС Windows и Lync в рабочем состоянии. В подобной ситуации каждый день может происходить всего несколько входов в систему, так как пользователи зарегистрировались несколько дней назад и с тех пор не выходили из системы. Однако показатель количества уникальных активных пользователей сообщает, активно ли пользователи работали с Lync или другим клиентом Lync Server.

## Фильтры

Фильтры предоставляют способ, позволяющий возвращать более точно подобранные множества данных или просматривать возвращенные данные в разных представлениях. Например, отчет о регистрации пользователей позволяет просматривать данные для всех пулов пул регистраторов и серверов сервер либо просматривать данные для отдельного пула. Можно также выбрать порядок группирования данных. В этом случае регистрации группируются по времени, дням, неделям или месяцам.

В следующей таблице приведены фильтры, которые можно использовать с отчетом о регистрации пользователей.

### Фильтры отчета о регистрации пользователей

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>From</strong> (От)</p></td>
<td><p>Начальная дата и начальное время для диапазона времени. Чтобы просмотреть данные по часам, введите начальную дату и начальное время в следующем формате:</p>
<p>7/7/2012 13:00</p>
<p>Если вы не вводите начальное время, отчет автоматически начинается с 24:00 указанного дня. Чтобы просмотреть данные по дням, просто введите дату:</p>
<p>7/7/2012</p>
<p>Чтобы просмотреть данные за неделю или месяц, введите дату, выпадающую на любое время в рамках недели или месяца, которые вы хотите просмотреть (вам не требуется вводить первый день недели или месяца):</p>
<p>7/3/2012</p>
<p>Недели всегда отсчитываются с воскресенья по субботу.</p></td>
</tr>
<tr class="even">
<td><p><strong>To</strong> (До)</p></td>
<td><p>Конечная дата и конечное время для диапазона времени. Чтобы просмотреть данные по часам, введите конечную дату и конечное время в следующем формате:</p>
<p>7/7/2012 13:00</p>
<p>Если вы не вводите конечное время, отчет автоматически заканчивается в 24:00 указанного дня. Чтобы просмотреть данные по дням, просто введите дату:</p>
<p>7/7/2012</p>
<p>Чтобы просмотреть данные за неделю или месяц, введите дату, выпадающую на любое время в рамках недели или месяца, которые вы хотите просмотреть (вам не требуется вводить первый день недели или месяца):</p>
<p>7/3/2012</p>
<p>Недели всегда отсчитываются с воскресенья по субботу.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Interval</strong> (Интервал)</p></td>
<td><p>Временной интервал. Выберите одно из следующих значений:</p>
<ul>
<li><p>Hourly (По часам) (можно отобразить не более 25 часов)</p></li>
<li><p>Daily (По дням) (можно отобразить не более 31 дня)</p></li>
<li><p>Weekly (По неделям) (можно отобразить не более 12 недель)</p></li>
<li><p>Monthly (По месяцам) (можно отобразить не более 12 месяцев)</p></li>
</ul>
<p>Если число значений между начальной и конечной датами превышает максимальное допустимое для выбранного интервала, отображается максимальное возможное число значений (с начальной даты). Например, если вы выбрали интервал &quot;Ежедневно&quot; с начальной датой 07.07.2012 и конечной датой 28.02.2012, будут показаны данные для периода с 07.08.2012 24:00 до 07.09.2012 24:00 (то есть для 31 дня).</p></td>
</tr>
<tr class="even">
<td><p><strong>Pool</strong> (Пул)</p></td>
<td><p>Полное доменное имя (FQDN) пул регистраторов или сервер. Можно выбрать отдельный пул или выбрать <strong>[Все]</strong> , чтобы просмотреть данные для всех пулов. Данный раскрывающийся список заполняется автоматически на основе записей, имеющихся в базе данных.</p></td>
</tr>
</tbody>
</table>


## Показатели

В следующей таблице представлены сведения, приведенные в отчете о регистрации пользователей.

### Показатели отчета о регистрации пользователей

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя</th>
<th>Поддержка сортировки</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Ежечасно</strong></p>
<p><strong>Ежедневно</strong></p>
<p><strong>Еженедельно</strong></p>
<p><strong>Ежемесячно</strong></p></td>
<td><p>Нет</p></td>
<td><p>Указывает на временной интервал, выбранной на панели фильтров. Вы можете щелкнуть временной интервал, чтобы просмотреть подробные сведения для него, если они доступны. Например, если используется интервал &quot;Ежедневно&quot;, то при щелчке по дате 07.07.2012 вы увидите почасовые сведения о регистрации пользователей за эту дату.</p></td>
</tr>
<tr class="even">
<td><p><strong>Общее количество входов</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество успешных сеансов входа.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Количество внутренних входов</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество входов в систему в пределах внутренней сети.</p></td>
</tr>
<tr class="even">
<td><p><strong>Количество внешних входов</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество входов в систему из внешних сетей с использованием пограничного сервера.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Количество уникальных входов пользователей</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество пользователей хотя бы с одним сеансом входа. Пользователь с несколькими сеансами входа считается как один пользователь, так же, как и пользователь с одним сеансом входа.</p></td>
</tr>
<tr class="even">
<td><p><strong>Количество активных пользователей</strong></p></td>
<td><p>Нет</p></td>
<td><p>Общее количество пользователей, участвующих в одноранговом сеансе или сеансе конференции. Пользователь с несколькими сеансами считается как один пользователь, так же, как и пользователь с одним сеансом входа.</p></td>
</tr>
</tbody>
</table>
