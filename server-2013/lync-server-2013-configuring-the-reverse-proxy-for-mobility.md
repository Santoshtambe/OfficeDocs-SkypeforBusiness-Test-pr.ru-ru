﻿---
title: 'Lync Server 2013: настройка обратного прокси-сервера для мобильной работы'
TOCTitle: Настройка обратного прокси-сервера для мобильной работы
ms:assetid: 3f4a9e33-77e4-4c18-a73f-24d4bec8ea9c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Hh690011(v=OCS.15)
ms:contentKeyID: 49309543
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Настройка обратного прокси-сервера для мобильной работы в Lync Server 2013

 

_**Дата изменения раздела:** 2014-03-20_

Если вы хотите использовать автоматическое обнаружение для клиентов мобильных устройств, вам необходимо изменить существующее или создать новое правило веб-публикации для обратного прокси-сервера независимо от того, обновляете ли вы списки альтернативных имен субъектов в сертификатах обратного прокси-сервера.

Если вы хотите использовать HTTPS для исходных запросов службы автообнаружения системы Lync Server 2013 и обновить списки альтернативных имен субъектов в сертификатах обратного прокси-сервера, вам необходимо назначить обновленный общий сертификат прослушивателя SSL на обратном прокси-сервере. Дополнительные сведения о требуемых записях альтернативных имен субъектов см. в разделе [Технические требования для организации мобильной работы в Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md). После этого вам требуется изменить существующий прослушиватель для внешних веб-служб или создать новое правило веб-публикации для внешнего URL-адреса службы автообнаружения. Если у вас еще нет правила веб-публикации для внешнего URL-адреса веб-служб системы Lync Server 2013 для пула переднего плана, вам также потребуется опубликовать такое правила.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Правило публикации и прослушиватель обратного прокси-сервера могут обслуживать как внешние веб-службы, так и служба автообнаружения при условии, что назначенный прослушивателю сертификат содержит необходимое имя субъекта и альтернативные имена субъектов для обоих этих компонентов. Дополнительные сведения о конфигурации по умолчанию для веб-прослушивателя и правила публикации см. в разделе <a href="lync-server-2013-setting-up-reverse-proxy-servers.md">Настройка обратных прокси-серверов для Lync Server 2013</a>.</td>
</tr>
</tbody>
</table>


Если вы решили использовать HTTP для исходных запросов службы автообнаружения, чтобы вам не требовалось обновлять альтернативные имена субъектов для обратного прокси-сервера, вам необходимо создать или изменить правило веб-публикации для порта 80.

В процедурах этого раздела описывается создание и изменение правил веб-публикации в Microsoft Forefront Threat Management Gateway 2010 для реализации автоматического обнаружения.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В этих процедурах предполагается, что вы установили выпуск Standard Edition продукта Forefront Threat Management Gateway (TMG) 2010. Если вы используете другой обратный прокси-сервер, выполняются аналогичные процедуры, однако их требуется привести в соответствие с документацией по этому стороннему продукту.</td>
</tr>
</tbody>
</table>


## Создание правила веб-публикации для внешнего URL-адреса автообнаружения

1.  Нажмите кнопку **Пуск** , выберите **Программы** , **Microsoft Forefront TMG** и затем **Forefront TMG Management** .

2.  На левой панели разверните узел **ServerName** (Имя сервера), щелкните правой кнопкой мыши элемент **Firewall Policy** (Политика брандмауэра), выберите пункт **New** (Создать) и затем щелкните **Web Site Publishing Rule** (Правило публикации веб-сайтов).

3.  На странице **Welcome to the New Web Publishing Rule** (Новое правило веб-публикации) введите отображаемое имя для нового правила публикации (например, LyncDiscoveryURL).

4.  На странице **Выбрать действие правила** выберите пункт **Разрешить** .

5.  На странице **Тип публикации** выберите пункт **Опубликовать один веб-сайт или систему балансировки нагрузки** .

6.  На странице **Безопасность подключения к серверу** выберите пункт **Использовать SSL для подключения к опубликованному веб-серверу или ферме серверов** .

7.  На странице **Internal Publishing Details** (Внутренние сведения публикации) в области **Internal Site name** (Имя внутреннего веб-сайта) введите полное доменное имя пула Директоров (например, lyncdir01.contoso.local). Создавая правило для внешнего URL-адреса веб-служб в пуле переднего плана, введите VIP-адрес аппаратного балансировщика нагрузки (HLB) перед переднего плана.

8.  На странице **Internal Publishing Details** (Сведения о внутренней публикации) в области **Path (optional)** (Путь (необязательно)) введите **/\*** в качестве пути к публикуемой папке, а затем выберите **Forward the original host header** (Пересылать исходный заголовок узла).

9.  На странице **Public Name Details** (Параметры общедоступного имени) выполните следующие действия:
    
      - В области **Accept Requests for** (Принимать запросы для) выберите **This domain name** (Имя этого домена).
    
      - В области **Public Name** (Общедоступное имя) введите **lyncdiscover.** *\<домен SIP\>* (внешний URL-адрес службы автообнаружения). Если вы создаете правило для внешнего URL-адреса веб-служб в пуле переднего плана, введите полное доменное имя внешних веб-служб для этого пула переднего плана (например, lyncwebextpool01.contoso.com).
    
      - В поле **Path** (Путь) введите **/\*** .

10. На странице **Select Web Listener** (Выбрать веб-прослушиватель) в области **Web Listener** (Веб-прослушиватель) выберите существующий прослушиватель SSL с обновленным общим сертификатом.

11. На странице **Делегирование проверки подлинности** выберите пункт **Без делегирования, но клиент может выполнять проверку подлинности напрямую** .

12. На странице **User Set** (Пользовательский набор) выберите **All Users** (Все пользователи).

13. На странице **Завершение работы мастера создания правила веб-публикации** проверьте, верны ли параметры правила веб-публикации, и нажмите кнопку **Готово** .

14. В списке правил веб-публикации Forefront TMG дважды щелкните недавно добавленное новое правило, чтобы открыть окно **Properties** (Свойства).

15. На вкладке **To** (Куда) выполните следующие действия:
    
      - Выберите **Forward the original host header instead of the actual one** (Пересылать исходный заголовок узла вместо действительного).
    
      - Выберите **Requests appear to come from the Forefront TMG computer** (Запросы поступили от компьютера Forefront TMG).

16. На вкладке **Bridging** (Использование моста) настройте следующее:
    
      - Выберите **Web server** (Веб-сервер).
    
      - Выберите **Redirect requests to HTTP port** (Перенаправлять запросы на HTTP-порт) и введите **8080** в качестве номера порта.
    
      - Выберите **Redirect requests to SSL port** (Перенаправлять запросы на SSL-порт) и введите **4443** в качестве номера порта.

17. Нажмите кнопку **ОК** .

18. В области сведений нажмите кнопку **Применить** , чтобы сохранить изменения и обновить конфигурацию.

19. Нажмите кнопку **Test Rule** (Тест правила) чтобы убедиться, что новое правило настроено правильно.

## Изменение существующего правила веб-публикации для добавления внешних альтернативного имени субъекта и URL-адреса автообнаружения

1.  Нажмите кнопку **Пуск** , выберите **Программы** , **Microsoft Forefront TMG** и затем **Forefront TMG Management** .
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ618369.important(OCS.15).gif" title="important" alt="important" />Важно!</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Вы будете повторять это изменение для каждого используемого правила публикации и прослушивателя. Обычно используются одно правило и один прослушиватель для пулов переднего плана и одно правило и один прослушиватель для дополнительных серверов Директор или пулов серверов Директор, если вы развернули их.</td>
    </tr>
    </tbody>
    </table>


2.  На левой панели разверните **ServerName** (Имя сервера) щелкните правой кнопкой мыши элемент **Firewall Policy** (Политика брандмауэра) и выберите нужное правило. На вкладке **Tasks** (Задачи) щелкните элемент **Edit Selected rule** (Изменить выбранное правило).

3.  На вкладке **Public Name** (Общедоступное имя) в области **This rule applies to** (Это правило применяется к) выберите значение **Requests for the following Web sites** (Запросы к следующим веб-сайтам).

4.  Нажмите кнопку **Add** (Добавить), введите имя нового сайта автообнаружения (например, «lyncdiscover.contoso.com») и нажмите кнопку **OK** (ОК).

5.  На вкладке **Listener** (Прослушиватель) щелкните элемент **Select Certificate** (Выбрать сертификат) и назначьте новый сертификат с добавленными записями альтернативного имени субъекта автообнаружения. Закройте свойства прослушивателя и веб-публикации.

6.  В области сведений нажмите кнопку **Применить** , чтобы сохранить изменения и обновить конфигурацию.

7.  Нажмите кнопку **Test Rule** (Тест правила) чтобы убедиться, что новое правило настроено правильно.

## Создание правила веб-публикации для порта 80

1.  Нажмите кнопку **Пуск** , выберите **Программы** , **Microsoft Forefront TMG** и затем **Forefront TMG Management** .

2.  На левой панели разверните узел **ServerName** (Имя сервера), щелкните правой кнопкой мыши элемент **Firewall Policy** (Политика брандмауэра), выберите пункт **New** (Создать) и затем щелкните **Web Site Publishing Rule** (Правило публикации веб-сайтов).

3.  На странице **Welcome to the New Web Publishing Rule** (Новое правило веб-публикации) введите отображаемое имя для нового правила публикации (например, Lync Autodiscover (HTTP)).

4.  На странице **Выбрать действие правила** выберите пункт **Разрешить** .

5.  На странице **Тип публикации** выберите пункт **Опубликовать один веб-сайт или систему балансировки нагрузки** .

6.  На странице **Server Connection Security** (Безопасность подключения к серверу) выберите **Use non-secured connections to connect to the published Web server or server farm** (Использовать SSL для подключения к опубликованному веб-серверу или ферме серверов).

7.  На странице **Internal Publishing Details** (Внутренние сведения публикации) в области **Internal Site name** (Имя внутреннего веб-сайта), введите VIP-адрес введите VIP-адрес аппаратного балансировщика нагрузки (HLB) перед переднего плана.

8.  На странице **Internal Publishing Details** (Сведения о внутренней публикации) в области **Path (optional)** (Путь (необязательно)) введите **/\*** в качестве пути к публикуемой папке, а затем выберите **Forward the original host header instead of the one specified in the Internal site name field** (Пересылать исходный заголовок узла вместо указанного в поле имени внутреннего веб-сайта).

9.  На странице **Public Name Details** (Параметры общедоступного имени) выполните следующие действия:
    
      - В области **Accept Requests for** (Принимать запросы для) выберите **This domain name** (Имя этого домена).
    
      - В области **Public Name** (Общедоступное имя) введите **lyncdiscover.** *\<домен SIP\>* (внешний URL-адрес службы автообнаружения).
    
      - В поле **Path** (Путь) введите **/\*** .

10. На странице **Select Web Listener** (Выбрать веб-прослушиватель) в области **Web Listener** (Веб-прослушиватель) выберите веб-прослушиватель или создайте новый с помощью мастера определения нового веб-прослушивателя.

11. На странице **Authentication Delegation** (Делегирование проверки подлинности) выберите **No delegation, and client cannot authenticate directly** (Без делегирования, клиент не может выполнять проверку подлинности напрямую).

12. На странице **User Set** (Пользовательский набор) выберите **All Users** (Все пользователи).

13. На странице **Завершение работы мастера создания правила веб-публикации** проверьте, верны ли параметры правила веб-публикации, и нажмите кнопку **Готово** .

14. В списке правил веб-публикации Forefront TMG дважды щелкните недавно добавленное новое правило, чтобы открыть окно **Properties** (Свойства).

15. На вкладке **Bridging** (Использование моста) настройте следующее:
    
      - Выберите **Web server** (Веб-сервер).
    
      - Выберите **Redirect requests to HTTP port** (Перенаправлять запросы на HTTP-порт) и введите **8080** в качестве номера порта.
    
      - Убедитесь, что параметр **Redirect requests to SSL port** (Перенаправлять запросы на SSL-порт) не выбран.

16. Нажмите кнопку **ОК** .

17. В области сведений нажмите кнопку **Применить** , чтобы сохранить изменения и обновить конфигурацию.

18. Нажмите кнопку **Test Rule** (Тест правила) чтобы убедиться, что новое правило настроено правильно.

19. Убедитесь, что ни для одного из других правил веб-публикации не определен внешний URL-адрес службы автообнаружения.

## См. также

#### Концепции

[Настройка обратных прокси-серверов для Lync Server 2013](lync-server-2013-setting-up-reverse-proxy-servers.md)  
[Технические требования для организации мобильной работы в Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md)
