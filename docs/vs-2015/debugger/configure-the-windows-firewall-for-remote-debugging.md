---
title: 원격 디버깅을 위해 Windows 방화벽 구성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f232446ed699bd7cc034e4b6d6148b665830cf2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535527"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>원격 디버깅을 위해 Windows 방화벽 구성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 다음 운영 체제를 실행하는 컴퓨터에서 원격 디버깅을 사용하도록 방화벽을 구성하는 방법을 설명합니다.  
  
- Windows 7  
  
- Windows 8/8.1  
  
- Windows 10  
  
- Windows Server 2008(R2)  
  
- Windows Server 2012  
  
- Windows Server 2012 R2  
  
  디버그 중인 네트워크가 방화벽으로 보호되지 않는 경우에는 이 구성이 필요하지 않습니다. 그렇지 않은 경우 Visual Studio를 호스트하는 컴퓨터와 디버그해야 하는 원격 컴퓨터 둘 다에서 방화벽 구성을 변경해야 합니다.  
  
  **IPSec** 네트워크에서 IPSec을 사용하여 통신을 수행해야 하는 경우 Visual Studio 호스트 컴퓨터와 원격 컴퓨터 둘 다에서 추가 포트를 열어야 합니다.  
  
  **웹 서버** 원격 웹 서버를 디버그하는 경우 원격 컴퓨터에서 추가 포트를 열어야 합니다.  
  
  두 컴퓨터에서 동일한 운영 체제를 실행할 필요는 없습니다. 예를 들어 Visual Studio 컴퓨터는 Windows 10을 실행하고 원격 컴퓨터는 Windows Server 2012 R2를 실행할 수 있습니다.  
  
## <a name="to-configure-windows-firewall-on-the-visual-studio-computer"></a>Visual Studio 컴퓨터에서 Windows 방화벽을 구성하려면  
 Windows 방화벽을 구성하기 위한 지침은 운영 체제마다 약간 다릅니다. Windows 7 또는 Windows Server 2008에서는 **프로그램** 이란 단어가 사용되고, Windows 8/8.1, Windows 10 및 Windows Server 2012에서는 **앱** 이란 단어가 사용됩니다.  다음 단계에서는 **앱**이란 단어를 사용합니다.  
  
1. Windows 방화벽 페이지를 엽니다. **시작** 메뉴 검색 상자에 **Windows 방화벽**을 입력합니다.  
  
2. **Windows 방화벽을 통해 앱 또는 기능 허용**을 클릭합니다.  
  
3. **허용된 앱 및 기능** 목록에서 **Visual Studio 원격 디버거 검색**을 찾습니다. 표시되는 경우 선택되었으며 하나 이상의 네트워크 종류도 선택되었는지 확인합니다.  
  
4. **Visual Studio 원격 디버거 검색** 이 표시되지 않는 경우 **다른 앱 허용**을 클릭합니다. 그래도 **앱 추가** 창에 표시 되지 않는 경우 **찾아보기** 를 클릭 하 고 ** \<Visual Studio installation directory> \Common7\IDE\Remote Debugger**로 이동 합니다. 애플리케이션에 대한 적절한 폴더(x86, x64, Appx)를 찾은 다음 **msvsmon.exe**를 선택합니다. 그런 다음, **추가**를 클릭합니다.  
  
5. **허용된 앱 및 기능** 목록에서 **Visual Studio 원격 디버깅 모니터**를 선택합니다. 원격 디버깅 모니터에서 통신하려는 네트워크 종류(**도메인, 홈/회사(개인), 공용**)를 하나 이상 선택합니다. 종류는 Visual Studio 컴퓨터가 연결된 네트워크를 포함해야 합니다.  
  
## <a name="to-open-a-port-on-the-visual-studio-computer-to-enable-discovery"></a>검색을 사용할 수 있도록 Visual Studio 컴퓨터에서 포트를 열려면  
 원격 디버거를 실행하는 컴퓨터의 검색을 허용하려면 UDP 포트 3702 수신을 허용해야 합니다. 추가하려면 방화벽에서 포트를 구성하는 방법을 참조하세요.  
  
## <a name="to-configure-the-windows-firewall-of-the-remote-computer-for-remote-debugging"></a>원격 디버깅을 위해 원격 컴퓨터의 Windows 방화벽을 구성하려면  
 원격 디버깅 구성 요소는 원격 컴퓨터에 설치하거나 공유 디렉터리에서 실행할 수 있습니다. 두 경우 모두 원격 컴퓨터의 방화벽을 구성해야 합니다. 원격 디버깅 구성 요소는 다음 위치에 있습니다.  
  
 **\<Visual Studio installation directory>\Common7\IDE\Remote 디버거**  
  
 Windows 방화벽을 구성하기 위한 지침은 운영 체제마다 약간 다릅니다. Windows 7 또는 Windows Server 2008에서는 **프로그램** 이란 단어가 사용되고, Windows 8/8.1, Windows 10 및 Windows Server 2012에서는 **앱** 이란 단어가 사용됩니다.  다음 단계에서는 **앱**이란 단어를 사용합니다.  
  
1. Windows 방화벽 페이지를 엽니다. **시작** 메뉴 검색 상자에 **Windows 방화벽**을 입력합니다.  
  
2. **Windows 방화벽을 통해 앱 또는 기능 허용**을 클릭합니다.  
  
3. **허용된 앱 및 기능** 목록에서 **Visual Studio 원격 디버깅 모니터**를 찾습니다. 표시되는 경우 선택되었으며 하나 이상의 네트워크 종류도 선택되었는지 확인합니다.  
  
4. **Visual Studio 원격 디버깅 모니터** 가 표시되지 않는 경우 **다른 앱 허용**을 클릭합니다. 그래도 **앱 추가 창**에 표시 되지 않는 경우 **찾아보기** 를 클릭 하 고 ** \<Visual Studio installation directory> \Common7\IDE\Remote Debugger**로 이동 합니다. 애플리케이션에 대한 적절한 폴더(x86, x64, Appx)를 찾은 다음 **msvsmon.exe**를 선택합니다. 그런 다음, **추가**를 클릭합니다.  
  
5. **허용된 앱** 목록에서 **Visual Studio 원격 디버깅 모니터**를 선택합니다. 원격 디버깅 모니터에서 통신하려는 네트워크 종류(**도메인, 홈/회사(개인), 공용**)를 하나 이상 선택합니다. 종류는 Visual Studio 컴퓨터가 연결된 네트워크를 포함해야 합니다.  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>원격 디버깅을 사용할 수 있도록 하는 원격 컴퓨터의 포트  
  
|**포트**|**들어오는/나가는 포트**|**프로토콜**|**설명**|  
|-|-|-|-|
|3702|나가는 포트|UDP|원격 디버거 검색에 필요합니다.|  
|4020||TCP|VS 2015에 사용됩니다. 포트 번호는 각 Visual Studio 버전마다 2씩 증가합니다. 자세한 내용은 Visual Studio 원격 디버거 포트 할당을 참조하세요.|  
|4021||TCP|VS 2015에 사용됩니다. 포트 번호는 각 Visual Studio 버전마다 2씩 증가합니다. 자세한 내용은 Visual Studio 원격 디버거 포트 할당을 참조하세요.|  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging-with-managed-or-native-compatibility-mode"></a>관리 또는 네이티브 호환성 모드로 원격 디버깅을 사용할 수 있도록 하는 원격 컴퓨터의 포트  
  
|**포트**|**들어오는/나가는 포트**|**프로토콜**|**설명**|  
|-|-|-|-|  
|135, 139, 445|나가는 포트|TCP|필수 요소.|  
|137, 138|나가는 포트|UDP|필수 요소.|  
|500, 4500|나가는 포트|UDP|도메인 정책에 따라 IPSec을 통해 네트워크 통신을 수행해야 하는 경우에 필요합니다.|  
|80|나가는 포트|TCP|웹 서버 디버깅에 필요합니다.|  
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Windows 방화벽에서 포트를 구성하는 방법  
  
1. **시작** 메뉴에서 **고급 보안이 포함된 Windows 방화벽**을 검색합니다.  
  
2. **인바운드 규칙** 또는 **아웃바운드 규칙** 을 클릭한 다음 **작업** 목록에서 **새 규칙** 을 클릭합니다.  
  
3. **규칙 유형** 페이지에서 **포트** 를 선택 하 고 **다음**을 클릭 합니다.  
  
4. **프로토콜 및 포트** 페이지에서 포트 프로토콜(TCP 또는 UDP)을 선택합니다. **특정 로컬 포트** 를 선택하고 프로토콜에 사용하도록 설정할 포트 번호를 하나 이상 입력합니다. 번호를 쉼표로 구분합니다. **다음**을 클릭합니다.  
  
5. **작업** 페이지에서 **연결 허용** 을 선택하고 **다음**을 클릭합니다.  
  
6. **프로필** 페이지에서 포트에 사용하도록 설정할 네트워크 종류를 하나 이상 선택합니다. 선택한 유형은 원격 컴퓨터가 연결된 네트워크를 포함해야 합니다. **다음**을 클릭합니다.  
  
7. **이름** 페이지에서 규칙의 이름을 입력하고 **마침**을 클릭합니다.  
  
8. **인바운드 규칙** 또는 **아웃 바운드 규칙** 목록에 새 규칙이 표시 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [Remote Debugging](../debugger/remote-debugging.md)
