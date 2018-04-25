﻿---
title: 'Lync Server 2013: рекомендации по развертыванию для сервера-посредника'
TOCTitle: Рекомендации по развертыванию для сервера-посредника
ms:assetid: 7cc22b87-18d9-45e6-8402-015abd20f2e5
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg398622(v=OCS.15)
ms:contentKeyID: 49310309
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Рекомендации по развертыванию для сервера-посредника в Lync Server 2013

 

_**Дата изменения раздела:** 2016-12-08_

В этой статье даются рекомендации по планированию для развертывания сервера- посредника. После изучения этих рекомендаций используйте средство планирования для создания и просмотра возможных альтернативных топологий, которые могут служить как модели окончательной оптимизированной топологии для развертывания.

## Выровненный или изолированный сервер- посредник?

Сервер- посредник по умолчанию выравнивается на сервере Сервер Standard Edition или на сервере переднего плана в пуле переднего плана на центральных сайтах. Количество вызовов ТСОП, которое может быть обработано, и необходимое количество компьютеров в пуле будет зависеть от следующих факторов:

  - от количества шлюзов, которыми управляет серверов-посредников;

  - от трафика через эти шлюзы в периоды высокой нагрузки;

  - от процента вызовов, которые обходят сервер- посредник.

При планировании убедитесь, что после учета требований обработки для вызовов ТСОП и для аудио- и видеоконференций, которые не настроены для обхода сервера-посредника, а также для обработки, необходимой для взаимодействия по передаче сигналов для того количества вызовов в часы наибольшей нагрузки, которое должно поддерживаться. Если мощности ЦП недостаточно, то необходимо развернуть изолированный пул Серверы-посредники, а шлюзы ТСОП, IP-УАТС и SBC необходимо разделить на подмножества, которые управляются выровненными Серверы-посредники в одном пуле и изолированными Серверы-посредники во одном или нескольких изолированных пулах.

Если развернуты шлюзы ТСОП, IP-УАТС или пограничные контроллеры сеансов, которые не поддерживают правильные возможности взаимодействия с пулом Серверы-посредники, включая следующие, то их придется связать с изолированным пулом, состоящим из единственного сервера- посредника.

  - Выполнять балансировку нагрузки на DNS сетевого уровня по всем серверам Серверы-посредники в пуле (или другим способом равномерно маршрутизировать трафик на все серверы Серверы-посредники в пуле).

  - Принимать трафик от любого сервера- посредника в пуле.

С помощью средства планирования Microsoft Lync Server 2013 можно оценить, в состоянии ли конфигурация совместного размещения сервера-посредника с пулом переднего плана обрабатывать нагрузку. Если ваша среда не может соответствовать этим требованиям, то необходимо развернуть изолированный пул серверов-посредников.

## Некоторые аспекты центрального сайта и сайта филиала

Серверы Серверы-посредники на центральном сайте могут использоваться для маршрутизации вызовов для IP-УАТС или шлюзов ТСОП на сайтах филиалов. Однако если разворачиваются каналы SIP, то необходимо развернуть сервер- посредник на тех сайтах, на которых заканчивается каждый канал. При наличии сервера- посредника на центральном сайте маршрутизации вызовов для IP-УАТС или шлюза ТСОП на сайте филиала не требуется использование обхода сервера-посредника. Однако если есть возможность включить обход сервера-посредника, это рекомендуется сделать, так как это уменьшит задержку пути мультимедиа и в результате улучшит качество мультимедиа, поскольку путь мультимедиа больше не будет должен следовать пути передачи сигналов. Обход сервера-посредника также сократит нагрузку обработки в пуле.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Функция обхода сервера-посредника взаимодействует не со всеми шлюзами ТСОП, IP-УАТС и SBC. Корпорация Майкрософт протестировала набор ТСОП-шлюзов и SBC с сертифицированными партнерами и провела некоторые тесты для Cisco IP-УАТС. Режим обхода сервера-посредника поддерживается только для продуктов и версий из программы Unified Communications Open Interoperability Program – Lync Server по адресу <a href="http://go.microsoft.com/fwlink/p/?linkid=268730">http://go.microsoft.com/fwlink/p/?LinkId=268730</a>.</td>
</tr>
</tbody>
</table>


Если требуется устойчивость сайта филиала, на нем необходимо развернуть устройство для обеспечения связи в филиалах или комбинацию сервера переднего плана, сервера- посредника и шлюза. (Предполагается, что на сайте филиала функция присутствия и конференц-связь неустойчивы.) Рекомендации по планированию голосовой связи на сайте филиала см. в статье [Планирование устойчивости голосовой связи для сайта филиала в Lync Server 2013](lync-server-2013-planning-for-branch-site-voice-resiliency.md).

Что касается взаимодействий с IP-УАТС, если IP-УАТС не в состоянии правильно поддерживать взаимодействия предварительных сигналов и сообщений с несколькими предварительными диалогами и взаимодействия RFC 3960, то для входящих вызовов из IP-УАТС в конечные точки Lync может произойти обрыв первых нескольких слов приветствия. Это поведение может быть более жестким, если сервер- посредник на центральном сайте направляет вызовы для IP-УАТС, когда маршрут заканчивается на сайте филиала, поскольку для выполнения передачи сигнала требуется больше времени. Если вы сталкиваетесь с таким поведением, то единственный способ сократить обрывы при первых словах состоит в развертывании сервера- посредника на сайте филиала.

Наконец, если на центральном сайте имеется УАТС с временным мультиплексированием, или если ваша IP-УАТС не устраняет необходимость в шлюзе ТСОП, то необходимо развернуть шлюз в маршруте вызова, связывающем сервер- посредник и УАТС.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Чтобы улучшить производительность автономного сервера-посредника, следует включить масштабирование на принимающей стороне (RSS) в сетевых адаптерах на этих серверах. RSS поддерживает параллельную обработку входящих пакетов несколькими процессорами сервера. Дополнительные сведения см. в статье об улучшениях масштабирования на стороне приема в Windows Server 2008 по адресу <a href="http://go.microsoft.com/fwlink/p/?linkid=268731">http://go.microsoft.com/fwlink/p/?LinkId=268731</a>. Сведения о том, как включить RSS, см. в документации сетевого адаптера.</td>
</tr>
</tbody>
</table>
