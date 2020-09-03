---
title: 원격 디버거 포트 할당 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2628d8929a0d2b6fd3561f88c81cfaa3b62564f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542105"
---
# <a name="remote-debugger-port-assignments"></a>원격 디버거 포트 할당
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 원격 디버거는 애플리케이션 또는 백그라운드 서비스로 실행할 수 있습니다. 애플리케이션으로 실행되는 경우 다음과 같이 기본적으로 할당되는 포트를 사용합니다.  
  
- Visual Studio 2015: 4020  
  
- Visual Studio 2013: 4018  
  
- Visual Studio 2012: 4016  
  
  즉, 원격 디버거에 할당되는 포트 번호가 각 릴리스마다 2씩 증가합니다. 원하는 대로 다른 포트 번호를 설정할 수 있습니다. 이후 섹션에서 포트 번호를 설정하는 방법을 설명합니다.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>32비트 운영 체제의 원격 디버거 포트  
 TCP 4020(Visual Studio 2015)은 기본 포트이며 모든 시나리오에 필요합니다. 명령줄 또는 원격 디버거 창에서 구성할 수 있습니다.  
  
 원격 디버거 창에서 **도구/옵션**을 클릭 하 고 tcp/ip 포트 번호를 설정 합니다.  
  
 명령줄에서 **/port** 스위치: **msvsmon/port \<port number> **을 사용 하 여 원격 디버거를 시작 합니다.  
  
 원격 디버깅 도움말에서 모든 원격 디버거 명령줄 스위치를 찾을 수 있습니다 (원격 디버거 창에서 **F1** 키를 누르거나 **도움말/사용법** 클릭).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>64비트 운영 체제의 원격 디버거 포트  
 64비트 버전의 원격 디버거가 시작되면 기본적으로 4020 포트를 사용합니다.  32비트 프로세스를 디버그하는 경우 64비트 버전의 원격 디버거가 4021 포트에서 32비트 버전의 원격 디버거를 시작합니다. 32비트 원격 디버거를 실행하는 경우 4020을 사용하며 4021은 사용되지 않습니다.  
  
 이 포트는 명령줄에서 구성할 수 있습니다. **Msvsmon/wow64port \<port number> **.  
  
## <a name="the-discovery-port"></a>검색 포트  
 UDP 3702는 네트워크에서 실행 중인 원격 디버거 인스턴스를 찾는 데 사용됩니다(예: **프로세스에 연결** 대화 상자의 **찾기** 대화 상자). 원격 디버거를 실행하는 컴퓨터를 검색하는 용도로만 사용되므로 대상 컴퓨터의 컴퓨터 이름 또는 IP 주소를 확인하는 다른 방법이 있을 경우 선택 사항입니다. 이는 검색에 사용되는 표준 포트이므로 포트 번호를 구성할 수 없습니다.  
  
 검색을 사용하지 않으려는 경우 검색을 사용하지 않도록 설정하여 명령줄  **Msvsmon /nodiscovery**에서 msvsmon을 시작할 수 있습니다.  
  
## <a name="remote-debugger-ports-on-azure"></a>Azure의 원격 디버거 포트  
 Azure의 원격 디버거에서 사용되는 포트는 다음과 같습니다. 클라우드 서비스의 포트는 개별 VM의 포트에 매핑됩니다. 모든 포트는 TCP입니다.  

|**연결**|**클라우드 서비스의 포트**|**VM의 포트**|  
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>관련 항목  
 [Remote Debugging](../debugger/remote-debugging.md)
