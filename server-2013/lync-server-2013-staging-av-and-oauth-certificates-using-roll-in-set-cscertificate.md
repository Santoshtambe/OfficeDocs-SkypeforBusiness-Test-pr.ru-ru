﻿---
title: Этапы сертифицирования AV и OAuth с использованием -Roll in Set-CsCertificate в Lync Server 2013
TOCTitle: Этапы сертифицирования AV и OAuth с использованием -Roll in Set-CsCertificate в Lync Server 2013
ms:assetid: 22dec3cc-4b6b-4df2-b269-5b35df4731a7
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ660292(v=OCS.15)
ms:contentKeyID: 49887901
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Этапы сертифицирования AV и OAuth с использованием -Roll in Set-CsCertificate в Lync Server 2013

 

_**Дата изменения раздела:** 2012-11-13_

Обмен данными аудио- и видеоконференций представляет собой ключевой компонент Microsoft Lync Server 2013. Такие функции, как общий доступ к приложениям, а также аудио- и видеоконференции используют сертификаты, назначенные для службы аудио- и видеоконференций, в частности, службы проверки подлинности аудио- и видеоконференций.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol>
<li><p>Этот новый компонент предназначен для работы с сертификатом службы аудио- и видеоконференций и <em>OAuthTokenIssuer</em>. Наряду с сертификатами службы аудио- и видеоконференций и OAuth можно предоставить и другие сертификаты, однако, при использовать все преимущества одновременной работы может только сертификат аудио- и видеоконференций.</p></li>
<li><p>Командлеты PowerShell Командная консоль Lync Server, используемые для управления сертификатами Microsoft Lync Server 2013, ссылаются на сертификат аудио- и видеоконференций как на тип сертификата <em>AudioVideoAuthentication</em> и на сертификат OAuthServer как на тип <em>OAuthTokenIssuer</em>. Далее в тексте этого раздела в целях уникальной идентификации сертификатов для ссылки на них будут указываться те же типы идентификатора (<em>AudioVideoAuthentication</em> и <em>OAuthTokenIssuer</em>).</p></li>
</ol></td>
</tr>
</tbody>
</table>


Служба проверки подлинности аудио- и видеоконференций отвечает за выдачу маркеров, используемых клиентами и другими пользователями аудио- и видеоконференций. Маркеры создаются на основе атрибутов сертификата, и по истечении срока действия сертификата, происходит разрыв соединения или отображается запрос на повторное подключение с использованием нового маркера, созданного новым сертификатом. Новый компонент Lync Server 2013 решает эту проблему путем размещения нового сертификата для промежуточного хранения до истечения срока действия старого, что обеспечивает одновременное действие обоих сертификатов в течение определенного времени. Этот компонент использует обновленные функции командлета Set-CsCertificate Командная консоль Lync Server. Новый параметр –Roll вместе с текущим параметром –EffectiveDate помещает новый сертификат AudioVideoAuthentication в хранилище сертификатов. Предыдущий сертификат AudioVideoAuthentication по-прежнему действует для проверки выданных маркеров. С момента размещения нового сертификата AudioVideoAuthentication возникают следующие наборы событий:


> [!TIP]
> Если для управления сертификатами используются командлеты Командная консоль Lync Server, можно запросить отдельные уникально идентифицируемые сертификаты для всех назначений сертификатов на сервере сервер. С помощью мастера сертификатов в развертывания Lync Server можно создавать сертификаты, однако, эти сертификаты стандартно принадлежат к типу <STRONG>default</STRONG>, который объединяет все используемые сертификаты, используемые сервер, в единый сертификат. Если планируется применение компонента последовательных сертификатов, рекомендуется отделить сертификат AudioVideoAuthentication от других назначений сертификата. Можно предоставить и разместить сертификат типа Default для промежуточного хранения, однако, только часть AudioVideoAuthentication объединенного сертификата сможет максимально эффективно использовать преимущества промежуточного хранения. Пользователь, участвующий, например, в обмене мгновенными сообщениями должен по истечении срока действия сертификата выполнить выход и повторный вход в систему, чтобы использовать новый сертификат, связанный с доступа. То же самое происходит с пользователем, который участвует в веб-конференции, используя службу веб-конференций. Сертификат OAuthTokenIssuer представляет собой отдельный тип, общий доступ к которому предоставляется для всех серверов. Создание и управление сертификатом осуществляется в одном расположении, и для всех остальных серверов сертификат хранится в службе управления.



Для полного понимания возможностей и условий использования командлета Set-CsCertificate и использования его для промежуточного хранения сертификатов до истечения срока действия текущего сертификата требуются дополнительные данные. Параметр –Roll имеет критически важное значение, но в целом, выполняет одну-единственную задачу. Если он определен как параметр, этим командлету Set-CsCertificate сообщается, что планируется предоставлять данные затронутого сертификата, определенного параметром –Type (например, AudioVideoAuthentication и OAuthTokenIssuer), когда действие сертификата вступит в силу в соответствии с параметром –EffectiveDate.

**-Roll**. Параметр –Roll является обязательным и содержит зависимости, которые необходимо предоставлять наряду с этим параметром. Эти параметры являются обязательными для полного определения затронутых сертификатов и способов их применения:

**-EffectiveDate**. Параметр –EffectiveDate определяет время активации нового сертификата параллельно с текущим сертификатом. Значение параметра –EffectiveDate может быть приближено ко времени истечения срока действия текущего сертификата, или же для параметра можно задать более продолжительный период. Рекомендуемое минимальное значение параметра –EffectiveDate для сертификата AudioVideoAuthentication — 8 часов, то есть, срок действия по умолчанию для маркера службы AV Edge, используемого сертификатом AudioVideoAuthentication.

При размещении сертификатов OAuthTokenIssuer для промежуточного хранения действуют различные требования в отношении времени упреждения, прежде чем действие сертификата вступит в силу. Минимальное время упреждения для сертификата OAuthTokenIssuer составляет 24 часа до истечения срока действия текущего сертификата. Увеличение времени упреждения для совместной работы применяется в связи с тем, что другие роли сервера, зависимые от сертификата OAuthTokenIssuer (например, Exchange Server), для которых предусматривается более продолжительный срок хранения сертификатов, создают данные проверки подлинности и ключа шифрования.

**-Thumbprint**. Отпечаток представляет собой атрибут сертификата, который является уникальным для данного сертификата. Параметр –Thumbprint используется для идентификации сертификата, затронутого действиями командлета Set-CsCertificate.

**-Type**. Параметр –Type может принимать один тип использования сертификата или список типов использования сертификата с разделением запятыми. Типами сертификата являются те типы, которые идентифицируют назначение сертификата для командлета и сервера. Например, тип AudioVideoAuthentication используется службой аудио- и видеоконференций и службой проверки подлинности аудио- и видеоконференций. Если планируется одновременно размещать для промежуточного хранения и предоставлять сертификаты другого типа, рекомендуется выбрать самое большое минимальное время упреждения для сертификатов. Например, потребуется разместить для промежуточного хранения сертификаты типа AudioVideoAuthentication и OAuthTokenIssuer. Необходимо использовать наибольшее минимальное значение параметра –EffectiveDate из содержащихся в сертификатах (в данном случае это будет сертификат OAuthTokenIssuer, содержащий минимальное значение времени упреждения "24 часа"). Если размещение для промежуточного хранения сертификата AudioVideoAuthentication со значением времени упреждения "24 часа" нежелательно, разместите его для промежуточного хранения отдельно с параметром EffectiveDate, который больше подходит для данной задачи.

## Обновление или продление сертификата аудио- и видеоконференций с помощью параметров –Roll и -EffectiveDate

1.  Войдите на локальный компьютер как член группы "Администраторы".

2.  Запросите продление сертификата или новый сертификат AudioVideoAuthentication с экспортируемым закрытым ключом для текущего сертификата службы аудио- и видеоконференций.

3.  Импортируйте новый сертификат AudioVideoAuthentication в роль сервер и остальные роли сервер в пуле (при наличии развернутого пула).

4.  Настройте импортированный сертификат с помощью командлета Set-CsCertificate и используйте параметр –Roll вместе с параметром –EffectiveDate. Дата вступления в силу определяется как время истечения срока действия текущего сертификата (14:00:00 или 14:00:00) за вычетом срока действия маркера (по умолчанию — восемь часов). Таким образом, мы получаем время активации сертификата (–EffectiveDate \<string\>: "22.07.12 6:00:00").
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Для пула пул необходимо наличие всех сертификатов AudioVideoAuthentication, развернутых и предоставленных до даты и времени, определенных параметром –EffectiveDate на первом развернутом сертификате во избежание возможных сбоев обмена данными аудио- и видеоконференций вследствие истечения срока действия старых сертификатов до продления всех клиентских и пользовательских маркеров с помощью нового сертификата.</td>
    </tr>
    </tbody>
    </table>
    
    Команда Set-CsCertificate с параметрами –Roll и –EffectiveTime:
    
        Set-CsCertificate -Type AudioVideoAuthentication -Thumbprint <thumb print of new certificate> -Roll -EffectiveDate <date and time for certificate to become active>
    
    Пример команды Set-CsCertificate:
    
        Set-CsCertificate -Type AudioVideoAuthentication -Thumbprint "B142918E463981A76503828BB1278391B716280987B" -Roll -EffectiveDate "7/22/2012 6:00:00 AM"
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Параметр EffectiveDate должен быть отформатирован в соответствии с региональными и языковыми параметрами американского английского.</td>
    </tr>
    </tbody>
    </table>


Визуальная временная шкала эффективна для более полного понимания процедуры, используемой командлетом Set-CsCertificate, параметрами -Roll и -EffectiveDate для размещения новых сертификатов для промежуточного хранения в целях выдачи новых маркеров AudioVideoAuthentication при одновременном использовании существующего сертификата для проверки AudioVideoAuthentication, используемого пользователями.

В следующем примере администратор определяет, что срок действия сертификата аудио- и видеоконференций истекает в 14:00:00 07/22/2012. Он запрашивает и получает новый сертификат и импортирует его в каждую из ролей сервер в своем пуле. В 2:00 07/22/2012 он начинает запуск командлета Get-CsCertificate, где значения параметров –Roll, -Thumbprint равны значениям строки отпечатка нового сертификата, а значение времени в параметре –EffectiveTime установлено как "07/22/2012 6:00:00 утра". Он запускает эту команду для каждой роли сервер.

![Использование параметров Roll и EffectiveDate.](images/JJ660292.21d51a76-0d03-4ed7-a37e-a7c14940265f(OCS.15).jpg "Использование параметров Roll и EffectiveDate.")

По достижении заданного времени (7/22/2012 6:00:00 утра) все новые маркеры выпускаются новым сертификатом. Сначала выполняется проверка маркеров новым сертификатом. Если проверка не пройдена, маркеры проверяются старым сертификатом. Процедура проверки новым сертификатом и возврат к старому продолжается до тех пор, пока не истечет срок действия старого сертификата. По истечении срока действия старого сертификата (7/22/2012 14:00:00) маркеры будут проверяться только новым сертификатом. Старый сертификат можно удалить с помощью командлета Remove-CsCertificate с параметром –Previous.

    Remove-CsCertificate -Type AudioVideoAuthentication -Previous

## Обновление и продление действия сертификата OAuthTokenIssuer с помощью параметров –Roll и -EffectiveDate

1.  Войдите на локальный компьютер как член группы "Администраторы".

2.  Запросите продление сертификата или новый сертификат OAuthTokenIssuer с экспортируемым закрытым ключом для текущего сертификата службы аудио- и видеоконференций.

3.  Импортируйте новый сертификат OAuthTokenIssuer в роль переднего плана в своем пуле (при наличии развернутого пула). Сертификат OAuthTokenIssuer реплицируется глобально, после чего требуется только его обновление и продление на всех серверах в текущей среде. В качестве примера используется роль переднего плана.

4.  Настройте импортированный сертификат с помощью командлета Set-CsCertificate и используйте параметр –Roll вместе с параметром –EffectiveDate. Дата вступления в силу определяется как время истечения срока действия текущего сертификата (14:00:00 или 2:00:00 дня) за вычетом не менее 24 часов.
    
    Команда Set-CsCertificate с параметрами –Roll и –EffectiveTime:
    
        Set-CsCertificate -Type OAuthTokenIssuer -Thumbprint <thumb print of new certificate> -Roll -EffectiveDate <date and time for certificate to become active>
    
    Пример команды Set-CsCertificate:
    
        Set-CsCertificate -Type OAuthTokenIssuer -Thumbprint "B142918E463981A76503828BB1278391B716280987B" -Roll -EffectiveDate "7/21/2012 1:00:00 PM"
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Параметр EffectiveDate должен быть отформатирован в соответствии с региональными и языковыми параметрами американского английского.</td>
    </tr>
    </tbody>
    </table>


По достижении заданного времени (7/21/2012 1:00:00 ночи) все новые маркеры выпускаются новым сертификатом. Сначала выполняется проверка маркеров новым сертификатом. Если проверка не пройдена, маркеры проверяются старым сертификатом. Процедура проверки новым сертификатом и возврат к старому продолжается до тех пор, пока не истечет срок действия старого сертификата. По истечении срока действия старого сертификата (7/22/2012 14:00:00) маркеры будут проверяться только новым сертификатом. Старый сертификат можно удалить с помощью командлета Remove-CsCertificate с параметром –Previous.

    Remove-CsCertificate -Type OAuthTokenIssuer -Previous

## См. также

#### Концепции

[Планирование сертификатов пограничного сервера в Lync Server 2013](lync-server-2013-plan-for-edge-server-certificates.md)  
[Управление проверкой подлинности между серверами (OAuth) и партнерскими приложениями в Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md)  

#### Другие ресурсы

[Настройка сертификатов пограничного сервера для Lync Server 2013](lync-server-2013-set-up-edge-certificates.md)  
[Set-CsCertificate](set-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)
