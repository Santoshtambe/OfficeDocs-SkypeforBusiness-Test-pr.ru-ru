﻿---
title: 'Lync Server 2013: развертывание типов IP-адресов на сервере переднего плана'
TOCTitle: Развертывание типов IP-адресов на сервере переднего плана
ms:assetid: b6c8e0f9-ec8e-4a4e-a525-756f9cd6b9d0
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ205191(v=OCS.15)
ms:contentKeyID: 49310936
ms.date: 07/28/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Развертывание типов IP-адресов на сервере переднего плана для Lync Server 2013

 

_**Дата изменения раздела:** 2016-07-28_

Для развертывания типов IP-адресов на переднего плана выполните в топологий следующую процедуру.

## Развертывание типов IP-адресов на сервере переднего плана

1.  В узле **Enterprise Edition Front End pools** (Интерфейсные пулы Enterprise Edition) щелкните правой кнопкой мыши сервер пула и затем выберите команду **Edit Properties** (Изменить свойства). (Либо выберите сервер и затем в меню **Action** (Действие) выберите команду **Edit Properties** (Изменить свойства).)

2.  В диалоговом окне **Edit Properties** (Изменение свойств) выберите тип IP-адреса, который необходимо настроить. Для конфигурации двойного стека установите флажки **Enable IPv4** (Включить IP версии 4) и **Enable IPv6** (Включить IP версии 6).
    
    **Диалоговое окно Edit Properties (Изменение свойств) для пула серверов переднего плана**
    
    ![Диалоговое окно изменения свойств серверов переднего плана](images/JJ205191.737a9d71-c0bc-4a54-9608-9e028dacc814(OCS.15).png "Диалоговое окно изменения свойств серверов переднего плана")
    
      - **Use all configured IP addresses** (Использовать все заданные IP-адреса). Выберите этот параметр, если требуется разрешить использование любых IP-адресов, заданных на компьютере.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Gg398412.note(OCS.15).gif" title="note" alt="note" />Примечание</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Этот параметр рекомендуется использовать для конфигураций IP версии 6 (IPv6).</td>
        </tr>
        </tbody>
        </table>
    
      - **Limit service usage to selected IP addresses** (Разрешить использовать службу только указанным IP-адресам). Выберите этот параметр, чтобы указать адрес, используемый на новом сервере. Если вы выберете этот параметр, потребуется ввести значение в поле **Primary IP address** (Основной IP-адрес).
    
      - **Primary IP address** (Основной IP-адрес). Введите IP-адрес, который будет использовать сервер для всех коммуникаций, за исключением ТСОП. Введенный IP-адрес должен соответствовать формату выбранного типа адресов.
    
      - **PSTN IP address** (IP-адрес ТСОП). Укажите IP-адрес ТСОП, используемый при расположении сервера-посредника на сервере переднего плана. Введенный IP-адрес должен соответствовать формату выбранного типа адресов.

