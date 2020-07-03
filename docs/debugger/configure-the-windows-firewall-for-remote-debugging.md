---
title: 원격 디버깅을 위해 Windows 방화벽 구성 | Microsoft Docs
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fa5d60d7fe662cff31b54bf3a13c203f4b6d8c9
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350695"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>원격 디버깅을 위해 Windows 방화벽 구성

Windows 방화벽으로 보호되는 네트워크에서는 원격 디버깅을 허용하도록 방화벽을 구성해야 합니다. Visual Studio 및 원격 디버깅 도구는 설치나 시작 중 올바른 방화벽 포트를 열려고 하지만 수동으로 포트를 열거나 앱을 허용해야 할 수도 있습니다.

이 항목에서는 Windows 10, 8/8.1 및 7과 Windows Server 2012 R2, 2012 및 2008 R2 컴퓨터에서 원격 디버깅을 사용하도록 Windows 방화벽을 구성하는 방법을 설명합니다. Visual Studio 및 원격 컴퓨터에서 같은 운영 체제를 실행할 필요는 없습니다. 예를 들어 Visual Studio 컴퓨터는 Windows 10을 실행하고 원격 컴퓨터는 Windows Server 2012 R2를 실행할 수 있습니다.

>[!NOTE]
>Windows 방화벽을 구성하는 지침은 다른 운영 체제와 이전 버전의 Windows에서 약간 다릅니다. Windows 8/8.1, Windows 10 및 Windows Server 2012 설정에서는 ‘앱’을 사용하지만 Windows 7 및 Windows Server 2008은 ‘프로그램’을 사용합니다. 

## <a name="configure-ports-for-remote-debugging"></a>원격 디버깅을 위한 포트 구성

Visual Studio와 원격 디버거는 설치나 시작 중 올바른 포트를 열려고 합니다. 그러나 타사 방화벽과 같은 일부 시나리오에서는 포트를 수동으로 열어야 할 수도 있습니다.

**포트를 열려면**

1. Windows **시작** 메뉴에서 **고급 보안이 포함된 Windows 방화벽**을 검색하여 엽니다. Windows 10에서는 **Windows Defender Firewall with Advanced Security**(고급 보안이 포함된 Windows Defender 방화벽)입니다.

1. 새 수신 포트에 대해 **인바운드 규칙** 선택한 다음 **새 규칙**을 선택합니다. 송신 규칙은 대신 **아웃바운드 규칙**을 선택합니다.

1. **새 인바운드 규칙 마법사**에서 **포트**를 선택한 후 **다음**을 선택합니다.

1. 다음 표의 포트 번호에 따라 **TCP** 또는 **UDP**를 선택합니다.

1. **특정 로컬 포트** 아래에 다음 표의 포트 번호를 입력하고 **다음**을 선택합니다.

1. **연결 허용**을 선택한 후 **다음**을 선택합니다.

1. 원격 연결을 위한 네트워크 종류를 포함해 사용할 네트워크 유형을 하나 이상 선택하고 **다음**을 선택합니다.

1. 규칙의 이름(예: **msvsmon**, **IIS** 또는 **웹 배포**)을 추가하고 **마침**을 선택합니다.

   새 규칙이 **인바운드 규칙** 또는 **아웃바운드 규칙** 목록에서 표시되어 선택되어 있어야 합니다.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>원격 디버깅을 사용할 수 있도록 하는 원격 컴퓨터의 포트

원격 디버깅의 경우 원격 컴퓨터에 다음 포트가 열려 있어야 합니다.

::: moniker range="vs-2017"

|**포트**|**들어오는/나가는 포트**|**프로토콜**|**설명**|
|-|-|-|-|
|4022|들어오는|TCP|VS 2017에 사용됩니다. 포트 번호는 Visual Studio 버전마다 2씩 증가합니다. 자세한 내용은 [Visual Studio 원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요.|
|4023|수신|TCP|VS 2017에 사용됩니다. 포트 번호는 Visual Studio 버전마다 2씩 증가합니다. 이 포트는 원격 디버거의 64비트 버전에서 32비트 프로세스를 원격으로 디버그하는 데만 사용됩니다. 자세한 내용은 [Visual Studio 원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요.|
|3702|나가는 포트|UDP|(선택 사항) 원격 디버거 검색에 필요합니다.|

::: moniker-end

::: moniker range=">= vs-2019"

|**포트**|**들어오는/나가는 포트**|**프로토콜**|**설명**|
|-|-|-|-|
|4024|수신|TCP|VS 2019에 사용됩니다. 포트 번호는 Visual Studio 버전마다 2씩 증가합니다. 자세한 내용은 [Visual Studio 원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요.|
|4025|수신|TCP|VS 2019에 사용됩니다. 포트 번호는 Visual Studio 버전마다 2씩 증가합니다. 이 포트는 원격 디버거의 64비트 버전에서 32비트 프로세스를 원격으로 디버그하는 데만 사용됩니다. 자세한 내용은 [Visual Studio 원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)을 참조하세요.|
|3702|나가는 포트|UDP|(선택 사항) 원격 디버거 검색에 필요합니다.|

::: moniker-end

**도구** > **옵션** > **디버깅**에서 **관리형 호환성 모드 사용**을 선택한 경우 이러한 추가 원격 디버거 포트를 엽니다. 디버거 관리형 호환성 모드를 사용하면 레거시 Visual Studio 2010 버전의 디버거를 사용할 수 있습니다.

|**포트**|**들어오는/나가는 포트**|**프로토콜**|**설명**|
|-|-|-|-|
|135, 139, 445|나가는 포트|TCP|필수 요소.|
|137, 138|나가는 포트|UDP|필수 요소.|

도메인 정책에 따라 IPSec을 통해 네트워크 통신을 수행해야 하는 경우 Visual Studio 및 원격 컴퓨터 둘 다에서 추가 포트를 열어야 합니다. 원격 IIS 웹 서버에서 디버그하려면 원격 컴퓨터에서 80 포트를 엽니다.

|**포트**|**들어오는/나가는 포트**|**프로토콜**|**설명**|
|-|-|-|-|
|500, 4500|나가는 포트|UDP|도메인 정책에 따라 IPSec을 통해 네트워크 통신을 수행해야 하는 경우에 필요합니다.|
|80|나가는 포트|TCP|웹 서버 디버깅에 필요합니다.|

Windows 방화벽을 통해 특정 앱을 허용하려면 [Windows 방화벽을 통해 원격 디버깅 구성](#configure-remote-debugging-through-windows-firewall)을 참조하세요.

## <a name="configure-remote-debugging-through-windows-firewall"></a>Windows 방화벽을 통해 원격 디버깅 구성

원격 디버깅 도구를 원격 컴퓨터에 설치하거나 공유 폴더에서 실행할 수 있습니다. 두 경우 모두 원격 컴퓨터 방화벽을 올바르게 구성해야 합니다.

원격 컴퓨터에서 원격 디버깅 도구는 다음 위치에 있습니다.

*\<Visual Studio installation directory\>\\Common7\\IDE\\Remote Debugger\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Windows 방화벽을 통해 원격 디버거 허용 및 구성

1. Windows **시작** 메뉴에서 **Windows 방화벽** 또는 **Windows Defender 방화벽**을 검색하여 열거나 합니다.

1. **Windows 방화벽에서 앱 허용**을 선택합니다.

1. **원격 디버거** 또는 **Visual Studio 원격 디버거**가 **허용되는 앱 및 기능**에 표시되지 않는 경우 **설정 변경**을 선택한 다음 **다른 앱 허용**을 선택합니다.

1. **앱 추가** 대화 상자에 원격 디버거 앱이 여전히 표시되어 있지 않으면 **찾아보기**를 선택하고 앱에 적절한 아키텍처에 따라 \<Visual Studio installation directory\>\\Common7\\IDE\\Remote Debugger\\\<x86*, *x64*, or *Appx*\>로 이동합니다. *msvsmon.exe*를 선택하고 **추가**를 선택합니다.

1. **앱** 목록에서 방금 추가한 **원격 디버거**를 선택합니다. **네트워크 종류**를 선택한 후 원격 연결을 위한 네트워크 종류를 포함해 하나 이상의 네트워크 종류를 선택합니다.

1. **추가**를 선택한 다음, **확인**을 선택합니다.

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>원격 디버깅 연결 문제 해결

원격 디버거를 사용하여 앱에 연결할 수 없는 경우 원격 디버깅 방화벽 포트, 프로토콜, 네트워크 종류 및 앱 설정이 모두 올바른지 확인합니다.

- Windows **시작** 메뉴에서 **Windows 방화벽**를 검색하여 열고 **Windows 방화벽에서 앱 허용**을 선택합니다. **원격 디버거** 또는 **Visual Studio 원격 디버거**가 **허용되는 앱 및 기능** 목록에 선택된 확인란과 함께 표시되고 올바른 네트워크 종류가 선택되어 있는지 확인합니다. 그렇지 않은 경우 [올바른 앱 및 설정을 추가](#configure-remote-debugging-through-windows-firewall)합니다.

- Windows **시작** 메뉴에서 **고급 보안이 포함된 Windows 방화벽**을 검색하고 엽니다. **원격 디버거** 또는 **Visual Studio 원격 디버거**가 **인바운드 규칙**(및 선택적으로 **아웃바운드 규칙**) 아래에 녹색 확인 표시 아이콘과 함께 표시되고 모든 설정이 올바른지 확인합니다.

  - 규칙 설정을 보거나 변경하려면 목록에서 **원격 디버거** 앱을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **속성** 탭을 사용하여 규칙을 사용 또는 사용하지 않도록 설정하거나 포트 번호, 프로토콜 또는 네트워크 종류를 변경합니다.
  - 원격 디버거 앱이 규칙 목록에 없으면 [올바른 포트를 추가 및 구성](#configure-ports-for-remote-debugging)합니다.

## <a name="see-also"></a>참조

- [원격 디버깅](../debugger/remote-debugging.md)
- [Visual Studio 원격 디버거 포트 할당](../debugger/remote-debugger-port-assignments.md)
