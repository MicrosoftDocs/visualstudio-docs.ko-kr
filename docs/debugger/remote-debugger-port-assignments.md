---
title: 원격 디버거 포트 할당 | Microsoft Docs
ms.custom: ''
ms.date: 05/18/2018
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fcd0159e5bd315009c1c468dc7a19b5ba5a9c61
ms.sourcegitcommit: d97d72308ef306e7f28c3a76913caee4ff450bbb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90713505"
---
# <a name="remote-debugger-port-assignments"></a>원격 디버거 포트 할당
Visual Studio 원격 디버거는 애플리케이션 또는 백그라운드 서비스로 실행할 수 있습니다. 애플리케이션으로 실행되는 경우 다음과 같이 기본적으로 할당되는 포트를 사용합니다.
::: moniker range=">=vs-2019"
- Visual Studio 2019: 4024
::: moniker-end
- Visual Studio 2017: 4022

- Visual Studio 2015: 4020

- Visual Studio 2013: 4018

- Visual Studio 2012: 4016

즉, 원격 디버거에 할당되는 포트 번호가 각 릴리스마다 2씩 증가합니다. 필요한 경우 다른 포트 번호를 설정할 수 있습니다. 이후 섹션에서 포트 번호를 설정하는 방법을 설명합니다.

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>32비트 운영 체제의 원격 디버거 포트

::: moniker range=">=vs-2019"
 TCP 4024(Visual Studio 2019)는 기본 포트이며 모든 시나리오에 필요합니다. 명령줄 또는 원격 디버거 창에서 구성할 수 있습니다.
::: moniker-end
::: moniker range="vs-2017"
 TCP 4022(Visual Studio 2017)는 기본 포트이며 모든 시나리오에 필요합니다. 명령줄 또는 원격 디버거 창에서 구성할 수 있습니다.
::: moniker-end

 원격 디버거 창에서 **도구 > 옵션**을 클릭하고 TCP/IP 포트 번호를 설정합니다.

 명령줄에서 **/port** 스위치를 사용하여 원격 디버거를 시작합니다(**msvsmon /port \<port number>** ).

 원격 디버깅 도움말에서 모든 원격 디버거 명령줄 스위치를 찾을 수 있습니다(원격 디버거 창에서 **F1** 키를 누르거나 **도움말 > 사용법** 클릭).

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>64비트 운영 체제의 원격 디버거 포트
::: moniker range=">=vs-2019"
 64비트 버전의 원격 디버거가 시작되면 기본적으로 기본 포트(4024)를 사용합니다.  32비트 프로세스를 디버그하는 경우 64비트 버전의 원격 디버거가 4025 포트(1씩 증가하는 기본 포트 번호)에서 32비트 버전의 원격 디버거를 시작합니다. 32비트 원격 디버거를 실행하는 경우 해당 디버거에서 4024를 사용하며 4025는 사용하지 않습니다.
::: moniker-end
::: moniker range="vs-2017"
 64비트 버전의 원격 디버거가 시작되면 기본적으로 기본 포트(4022)를 사용합니다.  32비트 프로세스를 디버그하는 경우 64비트 버전의 원격 디버거가 4023 포트(1씩 증가하는 기본 포트 번호)에서 32비트 버전의 원격 디버거를 시작합니다. 32비트 원격 디버거를 실행하는 경우 4022를 사용하며 4023은 사용되지 않습니다.
:::moniker-end

 이 포트는 명령줄 **Msvsmon /wow64port \<port number>** .

## <a name="the-discovery-port"></a>검색 포트
 UDP 3702는 네트워크에서 실행 중인 원격 디버거 인스턴스를 찾는 데 사용됩니다(예: **프로세스에 연결** 대화 상자의 **찾기** 대화 상자). 원격 디버거를 실행하는 컴퓨터를 검색하는 용도로만 사용되므로 대상 컴퓨터의 컴퓨터 이름 또는 IP 주소를 확인하는 다른 방법이 있을 경우 선택 사항입니다. 이는 검색에 사용되는 표준 포트이므로 포트 번호를 구성할 수 없습니다.

 검색을 사용하지 않으려는 경우 검색을 사용하지 않도록 설정하여 명령줄  **Msvsmon /nodiscovery**에서 msvsmon을 시작할 수 있습니다.

## <a name="remote-debugger-ports-on-azure"></a>Azure의 원격 디버거 포트
 Azure의 원격 디버거에서 사용되는 포트는 다음과 같습니다. 클라우드 서비스의 포트는 개별 VM의 포트에 매핑됩니다. 모든 포트는 TCP입니다.

|연결|클라우드 서비스의 포트|VM의 포트|
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarderx86|31401|31399|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|

## <a name="see-also"></a>참조
- [Remote Debugging](../debugger/remote-debugging.md)
