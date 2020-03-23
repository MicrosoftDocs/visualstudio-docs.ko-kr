---
title: VSTO 추가 기능의 성능 향상
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dccff7206aa9ef71596816d34a863695a10aff6b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416551"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>VSTO 추가 기능의 성능 향상
  Office 애플리케이션용으로 만드는 VSTO 추가 기능을 최적화하여 신속하게 시작하고, 종료하고, 항목을 열고, 다른 작업을 수행할 수 있는 향상된 환경을 사용자에게 제공할 수 있습니다. VSTO 추가 기능이 Outlook용인 경우 낮은 성능 때문에 VSTO 추가 기능이 사용하지 않도록 설정될 가능성도 줄일 수 있습니다. 다음 전략을 실행하여 VSTO 추가 기능의 성능을 높일 수 있습니다.

- [요청 시 VSTO 추가 기능 로드](#Load)

- [Windows Installer를 사용하여 Office 솔루션 게시](#Publish)

- [리본 반사를 우회합니다.](#Bypass)

- [별도의 실행 스레드에서 비용이 많이 드는 작업 수행](#Perform)

  Outlook VSTO 추가 기능을 최적화하는 방법에 대한 자세한 내용은 [VSTO 추가 기능을 사용하도록 설정하는 성능 기준을](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled)참조하십시오.

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>요청 시 VSTO 추가 기능 로드
 다음과 같은 경우에만 로드되도록 VSTO 추가 기능을 구성할 수 있습니다.

- VSTO 추가 기능이 설치된 후 사용자가 애플리케이션을 처음으로 시작하는 경우

- 이후에 애플리케이션을 시작한 후 사용자가 VSTO 추가 기능과 처음으로 상호 작용하는 경우

  예를 들어, 사용자가 내 데이터 **Get이라는**레이블이 붙은 사용자 지정 단추를 선택할 때 VSTO 추가 기능이 워크시트에 데이터로 채워질 수 있습니다. 내 **데이터 받기** 버튼이 리본에 표시될 수 있도록 응용 프로그램에서 VSTO 추가 기능을 한 번 이상 로드해야 합니다. 그러나 사용자가 다음에 응용 프로그램을 시작할 때 VSTO 추가 기능이 다시 로드되지 않습니다. VSTO 추가 기능은 사용자가 **내 데이터 가져오기** 단추를 선택할 때만 로드됩니다.

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>요청 시 VSTO 추가 기능을 로드하도록 ClickOnce 솔루션을 구성하려면

1. **솔루션 탐색기**에서 프로젝트 노드를 선택합니다.

2. 메뉴 모음에서 속성 페이지 **보기를** > **선택합니다.**

3. **게시** 탭에서 **옵션** 단추를 선택합니다.

4. **게시 옵션** 대화 상자에서 **Office 설정** 목록 항목을 선택하고 **요청 시 로드** 옵션을 선택한 다음 **확인** 단추를 선택합니다.

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>요청 시 VSTO 추가 기능을 로드하도록 Windows Installer 솔루션을 구성하려면

1. 레지스트리에서 ** _루트_\Software\Microsoft\Office\\_응용 프로그램 이름_\Addins\\추가 기능 ID** 키를 **0x10으로**설정합니다. `LoadBehavior`

     자세한 내용은 [VSTO 추가 기능의 레지스트리 항목을](../vsto/registry-entries-for-vsto-add-ins.md)참조하십시오.

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>솔루션을 디버그하는 동안 요청 시 VSTO 추가 기능을 로드하도록 솔루션을 구성하려면

1. ** _루트_\소프트웨어\Microsoft\Office\\_응용 프로그램 이름_\Addins\\추가 기능 ID** 키를 **0x10으로**설정하는 `LoadBehavior` 스크립트를 만듭니다.

     다음 코드에서는 이 스크립트의 예제를 보여 줍니다.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. 스크립트를 사용하여 레지스트리를 업데이트하는 빌드 후 이벤트를 만듭니다.

     다음 코드에서는 빌드 후 이벤트에 추가할 수 있는 명령 문자열의 예를 보여 줍니다.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     C# 프로젝트에서 빌드 후 이벤트를 만드는 방법에 대한 자세한 내용은 C&#35;&#41;[&#40;빌드 이벤트 지정 방법을 ](../ide/how-to-specify-build-events-csharp.md)참조하십시오.

     Visual Basic 프로젝트에서 빌드 후 이벤트를 만드는 방법에 대한 자세한 내용은 Visual Basic&#41;&#40;[빌드 이벤트 지정 방법을 ](../ide/how-to-specify-build-events-visual-basic.md)참조하십시오.

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>Windows 설치 관리자를 사용하여 Office 솔루션 게시
 Windows Installer를 사용하여 솔루션을 게시하는 경우 VISUAL Studio 2010 Office 용 도구는 VSTO 추가 기능이 로드될 때 다음 단계를 무시합니다.

- 매니페스트 스키마의 유효성 검사

- 자동으로 업데이트 확인

- 배포 매니페스트의 디지털 서명 유효성 검사

  > [!NOTE]
  > 사용자의 컴퓨터의 안전한 위치에 VSTO 추가 기능을 배포하는 경우 이 방법은 필요하지 않습니다.

  자세한 내용은 [Windows 설치 관리자를 사용하여 Office 솔루션 배포를](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)참조하십시오.

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a>리본 반사 를 우회
 을 사용하여 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]솔루션을 빌드하는 경우 사용자가 솔루션을 배포할 때 Office 런타임용 Visual Studio 2010 도구의 최신 버전을 설치했는지 확인합니다. 이전 버전의 VSTO 런타임이 솔루션 어셈블리에 반영되어 리본 사용자 지정을 찾습니다. 이 프로세스로 인해 VSTO 추가 기능이 더 느리게 로드될 수 있습니다.

 또는 Office용 Visual Studio 2010 도구의 모든 버전이 리플렉션을 사용하여 리본 사용자 지정을 식별하지 못하도록 할 수 있습니다. 이 전략을 따르려면 메서드를 `CreateRibbonExtensibility` 재정의하고 리본 개체를 명시적으로 반환합니다. VSTO 추가 기능이 리본 사용자 지정을 포함하지 않는 `null` 경우 메서드 내부로 돌아갑니다.

 다음 예제는 필드 값을 기반으로 리본 개체를 반환합니다.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a>별도의 실행 스레드에서 값비싼 작업을 수행합니다.
 별도의 스레드에서 시간이 많이 걸리는 작업(예: 장기 실행 작업, 데이터베이스 연결 또는 다른 종류의 네트워크 호출)을 수행하는 것이 좋습니다. 자세한 내용은 [Office의 스레딩 지원을](../vsto/threading-support-in-office.md)참조하십시오.

> [!NOTE]
> Office 개체 모델을 호출하는 모든 코드는 주 스레드에서 실행되어야 합니다.

## <a name="see-also"></a>참고 항목

- [수요 로딩 VSTO 추가 기능](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Office 추가 기능에서 CLR 지연 로드](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Visual Studio를 사용하여 Office용 VSTO 추가 기능 만들기](create-vsto-add-ins-for-office-by-using-visual-studio.md)
