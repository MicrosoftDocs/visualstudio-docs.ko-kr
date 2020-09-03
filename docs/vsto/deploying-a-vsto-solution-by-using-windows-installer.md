---
title: Windows Installer를 사용 하 여 Visual Studio Tools for Office 솔루션 배포
ms.date: 08/18/2010
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, setup project
- Office development in Visual Studio, MSI
- deploying applications [Office development in Visual Studio], setup project
- deploying applications [Office development in Visual Studio], MSI
- ClickOnce deployment [Office development in Visual Studio], MSI
- publishing Office solutions [Office development in Visual Studio], setup project
- Office applications [Office development in Visual Studio], MSI
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 46bfa808cbf99e942d7aadd2802f51eecfcefae8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444908"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>Windows Installer를 사용 하 여 Visual Studio Tools for Office 솔루션 배포

## <a name="summary"></a>요약

Visual Studio 설치 관리자 프로젝트를 사용 하 여 VSTO (Microsoft Visual Studio Tools for Office) 추가 기능 또는 문서 수준 솔루션을 배포 하는 방법에 대해 알아봅니다.

Wouter van Vugt, 코드 자문 위원

Ted Pattison, Ted Pattison Group

이 문서는 Microsoft에서 원래 작성자의 권한으로 업데이트 했습니다.

**적용 대상:** Visual Studio Tools for Office, Microsoft Office, Microsoft Visual Studio.

## <a name="overview"></a>개요

VSTO 솔루션을 개발 하 고 Windows Installer 패키지를 사용 하 여 솔루션을 배포할 수 있습니다. 이 설명에는 간단한 Office 추가 기능을 배포 하는 단계가 포함 되어 있습니다.

## <a name="deployment-methods"></a>배포 방법

ClickOnce를 사용 하면 추가 기능 및 솔루션에 대 한 프로그램을 쉽게 만들 수 있습니다. 그러나 컴퓨터 수준 추가 기능과 같은 관리 권한이 필요한 추가 기능을 설치할 수 없습니다.

Windows Installer를 사용 하 여 관리 권한이 필요한 추가 기능을 설치할 수 있지만 설치를 만들려면 더 많은 작업이 필요 합니다.

ClickOnce를 사용 하 여 VSTO 솔루션을 배포 하는 방법에 대 한 개요는 [clickonce를 사용 하 여 Office 솔루션 배포](deploying-an-office-solution-by-using-clickonce.md)를 참조 하세요.

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>VSTO 런타임을 대상으로 하는 Office 솔루션 배포

ClickOnce 및 Windows Installer 패키지는 Office 솔루션을 설치할 때 동일한 기초적인 작업을 수행 해야 합니다.

1. 사용자 컴퓨터에 필수 구성 요소를 설치 합니다.
2. 솔루션에 대 한 특정 구성 요소를 배포 합니다.
3. 추가 기능에 대 한 레지스트리 항목을 만듭니다.
4. 솔루션을 신뢰 하 여 실행할 수 있습니다.

### <a name="required-prerequisite-components-on-the-target-computer"></a>대상 컴퓨터에 필수 구성 요소 구성 요소

다음은 VSTO 솔루션을 실행 하기 위해 컴퓨터에 설치 해야 하는 소프트웨어 목록입니다.

- Microsoft Office 2010 이상.
- Microsoft .NET Framework 4 이상
- Microsoft Visual Studio 2010 Tools for Office Runtime.
  런타임은 추가 기능과 문서 수준 솔루션을 관리 하는 환경을 제공 합니다. 런타임 버전은 Microsoft Office와 함께 제공 되지만 추가 기능을 사용 하 여 특정 버전을 재배포할 수 있습니다.
- 포함 된 Interop 형식을 사용 하지 않는 경우 Microsoft Office의 주 Interop 어셈블리
- 프로젝트에서 참조 하는 유틸리티 어셈블리

### <a name="specific-components-for-the-solution"></a>솔루션에 대 한 특정 구성 요소

설치 관리자 패키지에서 사용자의 컴퓨터에 이러한 구성 요소를 설치 해야 합니다.

- 문서 수준 솔루션을 만드는 경우 Microsoft Office 문서입니다.
- 사용자 지정 어셈블리 및 필요한 어셈블리
- 구성 파일 등의 추가 구성 요소
- 응용 프로그램 매니페스트 (.manifest)입니다.
- 배포 매니페스트 (.vsto)

### <a name="registry-entries-for-add-ins"></a>추가 기능에 대 한 레지스트리 항목

Microsoft Office는 레지스트리 항목을 사용 하 여 추가 기능을 찾고 로드 합니다. 이러한 레지스트리 항목은 배포 프로세스의 일부로 만들어야 합니다. 이러한 레지스트리 항목에 대 한 자세한 내용은 [VSTO 추가 기능에 대 한 레지스트리 항목](registry-entries-for-vsto-add-ins.md)을 참조 하세요.

사용자 지정 양식 영역을 표시 하는 Outlook 추가 기능에는 양식 영역을 식별 하는 데 사용할 수 있는 추가 레지스트리 항목이 필요 합니다. 레지스트리 항목에 대 한 자세한 내용은 [Outlook 양식 영역에 대 한 레지스트리 항목](registry-entries-for-vsto-add-ins.md#OutlookEntries)을 참조 하세요.

문서 수준 솔루션에는 레지스트리 항목이 필요 하지 않습니다. 대신 문서 내의 속성이 사용자 지정을 찾는 데 사용 됩니다. 이러한 속성에 대 한 자세한 내용은 [사용자 지정 문서 속성 개요](custom-document-properties-overview.md)를 참조 하세요.

### <a name="trusting-the-vsto-solution"></a>VSTO 솔루션 신뢰

사용자 지정을 실행 하려면 컴퓨터에서 솔루션을 신뢰 해야 합니다. 인증서를 사용 하 여 매니페스트에 서명 하거나 포함 목록을 사용 하 여 트러스트 관계를 만들거나 컴퓨터의 신뢰할 수 있는 위치에 설치 하 여 추가 기능을 신뢰할 수 있습니다.

서명할 인증서를 가져오는 방법에 대 한 자세한 내용은 [ClickOnce 배포 및 Authenticode](../deployment/clickonce-and-authenticode.md)를 참조 하세요. 솔루션을 신뢰 하는 방법에 대 한 자세한 내용은 [포함 목록을 사용 하 여 Office 솔루션 신뢰](trusting-office-solutions-by-using-inclusion-lists.md)를 참조 하세요. Windows Installer 파일에 사용자 지정 작업을 포함 하는 포함 목록 항목을 추가할 수 있습니다. 포함 목록을 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [방법: 포함 목록 보안 구성](how-to-configure-inclusion-list-security.md)을 참조 하세요.

두 옵션을 모두 사용 하지 않으면 사용자에 게 솔루션을 신뢰할지 여부를 결정할 수 있는 신뢰 프롬프트가 표시 됩니다.

문서 수준 솔루션과 관련 된 보안에 대 한 자세한 내용은 [문서에 신뢰 부여](granting-trust-to-documents.md)를 참조 하세요.

## <a name="creating-a-basic-installer"></a>기본 설치 관리자 만들기

설치 및 배포 프로젝트 템플릿은 다운로드할 수 있는 [Microsoft Visual Studio 설치 관리자 프로젝트](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) 확장에 포함 되어 있습니다.

Office 솔루션에 대 한 설치 관리자를 만들려면 다음 작업을 수행 해야 합니다.

- 배포 될 Office 솔루션의 구성 요소를 추가 합니다.
- 응용 프로그램 수준 추가 기능의 경우 레지스트리 키를 구성 합니다.
- 최종 사용자 컴퓨터에 설치할 수 있도록 필수 구성 요소를 구성 합니다.
- 시작 조건을 구성 하 여 필수 구성 요소를 사용할 수 있는지 확인 합니다. 모든 필수 구성 요소가 설치 되지 않은 경우 시작 조건을 사용 하 여 설치를 차단할 수 있습니다.

첫 번째 단계는 설치 프로젝트를 만드는 것입니다.

### <a name="to-create-the-addin-setup-project"></a>추가 기능 설치 프로젝트를 만들려면

1. 배포 하려는 Office 추가 기능 프로젝트를 엽니다. 이 예에서는 Excel 추가 기능을 사용 하 고 있습니다.
2. Office 프로젝트를 연 상태에서 **파일** 메뉴에서 **추가** 를 확장 하 고 **새 프로젝트** 를 클릭 하 여 새 프로젝트를 추가 합니다.
::: moniker range="=vs-2017"
3. **새 프로젝트 추가** 대화 상자의 **프로젝트 형식** 창에서 **기타 프로젝트 형식** 을 확장 하 고 **설치 및 배포** 를 확장 한 다음 **Visual Studio 설치 관리자**를 선택 합니다.
4. **템플릿** 창의 **Visual Studio에 설치** 된 템플릿 그룹에서 **설치 프로젝트** 를 선택 합니다.
::: moniker-end
::: moniker range="=vs-2019"
3. **새 프로젝트 추가** 대화 상자에서 **설치 프로젝트** 템플릿을 선택 합니다.
4. **다음**을 클릭합니다.
::: moniker-end

5. **이름** 상자에을 (를) 입력 **합니다.**
::: moniker range="=vs-2017"
6. **열기** 를 클릭 하 여 새 설치 프로젝트를 만듭니다.
::: moniker-end
::: moniker range="=vs-2019"
6. **만들기** 를 클릭 하 여 새 설치 프로젝트를 만듭니다.
::: moniker-end

Visual Studio에서 새 설치 프로젝트에 대 한 파일 시스템 탐색기를 엽니다. 파일 시스템 탐색기를 사용 하 여 설치 프로젝트에 파일을 추가할 수 있습니다.

   ![설치 프로젝트에 대 한 파일 시스템 탐색기의 스크린샷](media/setup-project-figure-1.png)

   **그림 1: 설치 프로젝트용 파일 시스템 탐색기**

설치 프로젝트는 Excel 추가 기능을 배포 해야 합니다. 설치 프로젝트에 추가 기능 프로젝트 출력을 추가 하 여이 작업에 대 한 설치 프로젝트를 구성할 수 있습니다.

### <a name="to-add-the-exceladdin-project-output"></a>S\addin 프로젝트 출력을 추가 하려면

1. **솔루션 탐색기**에서를 마우스 오른쪽 **단추로 클릭 하**고, **추가** 를 클릭 한 다음 **프로젝트 출력**을 클릭 합니다.
2. **프로젝트 출력 그룹 추가** 대화 상자의 프로젝트 목록에서 **excel 추가 기능** 및 **기본 출력**을 선택 합니다.
3. **확인** 을 클릭 하 여 프로젝트 출력을 설치 프로젝트에 추가 합니다.

    ![설치 프로젝트 프로젝트 출력 그룹 추가 대화 상자의 스크린샷](media/setup-project-figure-2.png)

    **그림 2: 프로젝트 설치 프로젝트 출력 그룹 추가 대화 상자**

설치 프로젝트는 배포 매니페스트 및 응용 프로그램 매니페스트를 배포 해야 합니다. 이러한 두 파일을 설치 프로젝트의 출력 폴더에 있는 독립 실행형 파일로 설치 프로젝트에 추가 합니다.

### <a name="to-add-the-deployment-and-application-manifests"></a>배포 및 응용 프로그램 매니페스트를 추가 하려면

1. **솔루션 탐색기**에서, 파일을 마우스 오른쪽 **단추로 클릭 하**고 **추가**를 클릭 한 다음 **파일**을 클릭 합니다.
2. **파일 추가** 대화 상자에서 **excel 추가 기능** 출력 디렉터리로 이동 합니다. 일반적으로 출력 디렉터리는 선택한 빌드 구성에 따라 프로젝트 루트 디렉터리의 **bin \\ 릴리스** 하위 폴더입니다.
3. 이 두 파일을 설치 프로젝트에 추가 하려면이 파일을 **ExcelAddIn.dll** 선택 하 고 [ **열기** ]를 클릭 하 고 [열기]를 **클릭 하십시오.**

    ![솔루션 탐색기에서 응용 프로그램 및 배포 매니페스트의 스크린샷](media/setup-project-figure-3.jpg)

    **그림 3: 솔루션 탐색기의 추가 기능에 대 한 응용 프로그램 및 배포 매니페스트**

이 추가 기능을 참조 하려면 추가 기능에 필요한 모든 구성 요소가 포함 됩니다. 이러한 구성 요소를 올바르게 등록 하려면 필수 구성 요소 패키지를 사용 하 여 제외 하 고 배포 해야 합니다. 또한 설치를 시작 하기 전에 소프트웨어 사용 조건을 표시 하 고 승인 해야 합니다.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>추가 기능 프로젝트 종속성을 제외 하려면

1. **솔루션 탐색기**에서, **Microsoft .NET Framework** 를 **제외 하 고** **검색 된 종속성** 항목 아래의 모든 종속성 항목을 선택 하 고 ** \*.Utilities.dll**로 끝나는 모든 어셈블리를 선택 합니다. 유틸리티 어셈블리는 응용 프로그램과 함께 배포 됩니다.
2. 그룹을 마우스 오른쪽 단추로 클릭 하 고 **속성**을 선택 합니다.
3. **속성** 창에서 **제외** 속성을 **True** 로 변경 하 여 설치 프로젝트에서 종속 어셈블리를 제외 합니다. 유틸리티 어셈블리를 제외 하지 않아야 합니다.

    ![제외할 종속성을 보여 주는 솔루션 탐색기의 스크린샷](media/setup-project-figure-4.jpg)

    **그림 4: 종속성 제외**

부트스트래퍼 라고도 하는 설치 프로그램을 추가 하 여 필수 구성 요소를 설치 하도록 Windows Installer 패키지를 구성할 수 있습니다. 이 설치 프로그램은 부트스트래핑 이라는 프로세스를 필수 구성 요소를 설치할 수 있습니다.

추가 기능을 올바르게 실행 하려면 추가 **기능을 설치 해야 합니다.**

- Office 솔루션에서 대상으로 하는 Microsoft .NET Framework 버전입니다.
- Microsoft Visual Studio 2010 Tools for Office 런타임입니다.

종속 구성 요소를 필수 조건으로 구성 하려면

1. **솔루션 탐색기**에서, 프로젝트를 마우스 오른쪽 단추로 **클릭 하 고** **속성**을 선택 합니다.
2. 이 **속성 페이지** 대화 상자가 표시 됩니다.
3. **필수 구성 요소** 단추를 클릭 합니다.
4. 필수 구성 요소 대화 상자에서 올바른 버전의 .NET Framework 및 Microsoft Visual Studio Tools for Office Runtime을 선택 합니다.

    ![필수 구성 요소 대화 상자의 스크린샷](media/setup-project-figure-5.png)

    **그림 5: 필수 구성 요소 대화 상자**

    > [!NOTE]
    >Visual Studio 설치 프로젝트에서 구성 된 필수 구성 요소 패키지 중 일부는 선택한 빌드 구성에 따라 달라 집니다. 사용 하는 각 빌드 구성에 적합 한 필수 구성 요소를 선택 해야 합니다.

Microsoft Office은 레지스트리 키를 사용 하 여 추가 기능을 찾습니다. HKEY \_ 현재 사용자 hive의 키는 \_ 각 개별 사용자에 대 한 추가 기능을 등록 하는 데 사용 됩니다. HKEY \_ 로컬 컴퓨터 hive 아래의 키는 \_ 컴퓨터의 모든 사용자에 대 한 추가 기능을 등록 하는 데 사용 됩니다. 레지스트리 키에 대 한 자세한 내용은 [VSTO 추가 기능에 대 한 레지스트리 항목](registry-entries-for-vsto-add-ins.md)을 참조 하세요.

### <a name="to-configure-the-registry"></a>레지스트리를 구성 하려면

1. **솔루션 탐색기**에서,을 마우스 오른쪽 단추로 클릭 하 **여.**
2. **뷰**를 확장 합니다.
3. 레지스트리 **를 클릭 하 여 레지스트리** 편집기 창을 엽니다.
4. **레지스트리 (HKEY Addinsetup)** 편집기에서 ** \_ 로컬 \_ 컴퓨터** 를 확장 한 다음 **소프트웨어**를 확장 합니다.
5. **HKEY \_ 로컬 \_ 컴퓨터 \\ 소프트웨어**아래에 있는 ** \[ 제조업체 \] **의 키를 삭제 합니다.
6. **HKEY \_ 현재 \_ 사용자** 및 **소프트웨어**를 차례로 확장 합니다.
7. **HKEY \_ 현재 \_ 사용자 \\ 소프트웨어**아래에 있는 ** \[ 제조업체 \] ** 키를 삭제 합니다.
8. 추가 기능 설치에 대 한 레지스트리 키를 추가 하려면 **사용자/컴퓨터 Hive** 키를 마우스 오른쪽 단추로 클릭 하 고 **새 키**를 선택 합니다. 새 키의 이름으로 텍스트 **소프트웨어** 를 사용 합니다. 새로 만든 **소프트웨어** 키를 마우스 오른쪽 단추로 클릭 하 고 **Microsoft**텍스트를 사용 하 여 새 키를 만듭니다.
9. 비슷한 프로세스를 사용 하 여 추가 기능 등록에 필요한 전체 키 계층 구조를 만듭니다.

    **사용자/컴퓨터 Hive \\ 소프트웨어 \\ Microsoft \\ Office \\ Excel \\ 추가 \\ 기능 samplecompany.exceladdin**

    회사 이름은 고유성을 제공 하기 위해 추가 기능 이름의 접두사로 사용 되는 경우가 많습니다.

10. **Samplecompany.exceladdin** 키를 마우스 오른쪽 단추로 클릭 하 고 **새로 만들기**를 선택한 다음 **문자열 값**을 클릭 합니다. 이름에 대해 텍스트 **설명을** 사용 합니다.
11. 이 단계를 사용 하 여 세 개 이상의 값을 추가 합니다.
    - **문자열** 형식의 **FriendlyName**
    - **DWORD** 형식의 **LoadBehavior**
    - **문자열** 형식의 **매니페스트**

12. 레지스트리 편집기에서 **설명** 값을 마우스 오른쪽 단추로 클릭 하 고 **속성 창**을 클릭 합니다. **속성 창**에서 Value 속성에 대해 **Excel Demo 추가 기능** 을 입력 합니다.
13. 레지스트리 편집기에서 **FriendlyName** 키를 선택 합니다. **속성 창**에서 **Value** 속성을 **Excel Demo AddIn**으로 변경 합니다.
14. 레지스트리 편집기에서 **LoadBehavior** 키를 선택 합니다. **속성 창**에서 **Value** 속성을 3으로 변경 합니다 **.** LoadBehavior에 대 한 값 3은 호스트 응용 프로그램을 시작할 때 추가 기능을 로드 해야 함을 나타냅니다. 로드 동작에 대 한 자세한 내용은 [VSTO 추가 기능에 대 한 레지스트리 항목](registry-entries-for-vsto-add-ins.md)을 참조 하세요.

15. 레지스트리 편집기에서 **매니페스트** 키를 선택 합니다. **속성 창**에서 **Value** 속성을 **file:///[TARGETDIR] s\addin | vstolocal** 로 변경 합니다.

    ![레지스트리 편집기의 스크린샷](media/setup-project-figure-6.png)

    **그림 6: 레지스트리 키 설정**

      VSTO 런타임은이 레지스트리 키를 사용 하 여 배포 매니페스트를 찾습니다. [TARGETDIR] 매크로는 추가 기능이 설치 된 폴더로 바뀝니다. 매크로는 후행 \ 문자를 포함 하므로 배포 매니페스트의 파일 이름에는 \ 문자를 포함 하지 않는 추가 기능을 사용 해야 합니다.
      **Vstolocal** 후에는 VSTO 런타임에 추가 기능이 ClickOnce 캐시 대신이 위치에서 로드 되도록 VSTO 런타임에 지시 합니다. 이 후 위를 제거 하면 런타임에서 사용자 지정을 ClickOnce 캐시로 복사 합니다.

   >[!WARNING]
   >Visual Studio의 레지스트리 편집기에 주의 해야 합니다. 예를 들어 잘못 된 키에 대해 DeleteAtUninstall을 실수로 설정한 경우에는 레지스트리의 활성 부분을 삭제 하 여 사용자 컴퓨터가 일관 되지 않거나 손상 되지 않은 상태로 유지 될 수 있습니다.

64 비트 버전의 Office는 64 비트 레지스트리 하이브를 사용 하 여 추가 기능을 찾습니다. 64 비트 레지스트리 하이브에 추가 기능을 등록 하려면 설치 프로젝트의 대상 플랫폼을 64 비트 전용으로 설정 해야 합니다.

1. 솔루션 탐색기에서 솔루션 탐색기에서 솔루션 탐색기를 **선택 합니다.**
2. **속성** 창으로 이동 하 고 **targetplatform** 속성을 x **64**로 설정 합니다.

32 비트 및 64 비트 버전의 Office에 대 한 추가 기능을 설치 하려면 별도의 두 MSI 패키지를 만들어야 합니다. 하나는 32 비트이 고 다른 하나는 64 비트입니다.

  ![64 비트 Office를 사용 하 여 추가 기능을 등록 하기 위한 대상 플랫폼을 보여 주는 속성 창의 스크린샷](media/setup-project-figure-7.jpg)

  **그림 7:64 비트 Office를 사용 하 여 추가 기능을 등록 하기 위한 대상 플랫폼**

MSI 패키지를 사용 하 여 추가 기능 또는 솔루션을 설치 하는 경우 필수 구성 요소를 설치 하지 않고도 설치할 수 있습니다. 필수 구성 요소가 설치 되지 않은 경우 MSI에서 시작 조건을 사용 하 여 추가 기능이 설치 되지 않도록 차단할 수 있습니다.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>VSTO 런타임을 검색 하는 시작 조건 구성

1. **솔루션 탐색기**에서,을 마우스 오른쪽 단추로 클릭 하 **여.**
2. **뷰**를 확장 합니다.
3. **시작 조건**을 클릭 합니다.
4. **시작 조건 (내 컴퓨터 Addinsetup)** 편집기에서 **대상 컴퓨터의 요구 사항**을 마우스 오른쪽 단추로 클릭 한 다음 **레지스트리 시작 조건 추가**를 클릭 합니다. 이 검색 조건은 VSTO 런타임이 설치 하는 키에 대해 레지스트리를 검색할 수 있습니다. 그런 다음 명명 된 속성을 통해 설치 관리자의 다양 한 부분에서 키 값을 사용할 수 있습니다. 시작 조건은 검색 조건에 정의 된 속성을 사용 하 여 특정 값을 확인 합니다.
5. **시작 조건 (RegistryEntry1 Addinsetup)** 편집기에서 **검색 조건 검색** 조건을 선택 하 고 조건을 마우스 오른쪽 단추로 클릭 한 다음 **속성 창**을 선택 합니다.

6. **속성** 창에서 다음 속성을 설정 합니다.
   1. **(이름)** 의 값을 설정 하 여 **VSTO 2010 런타임을 검색**합니다.
   2. **속성** 의 값을 Vstorunvreststststststststststststv **VSTORUNTIMEREDIST**
   3. **RegKey** 의 값을 **SOFTWARE \\ Microsoft \\ VSTO Runtime Setup \\ v4R** 로 설정 합니다.
   4. **Root** 속성을 **Vsdrrhklm**로 설정 된 상태로 둡니다.
   5. **Value** 속성을 **Version**로 변경 합니다.

7. **시작 조건 (Condition1 Addinsetup)** 편집기에서 시작 조건을 선택 **Condition1** 하 고 조건을 마우스 오른쪽 단추로 클릭 한 다음 **속성 창**을 선택 합니다.
8. 속성 창에서 다음 속성을 설정합니다.
   1. **VSTO 2010 런타임 가용성을 확인**하려면 **(이름)** 을 설정 합니다.
   2. **조건** 값을 **Vstorunvreststststststststststststststststststv \> **
   3. **InstallURL** 속성은 비워 둡니다.
   4. **Message** **Visual Studio 2010 Tools for Office Runtime이 설치 되어 있지 않은 메시지를 설정 합니다. Setup.exe를 실행 하 여 추가 기능을 설치 하세요**.

        ![런타임 가용성 확인 시작 조건에 대 한 속성 창의 스크린샷](media/setup-project-figure-8.jpg)

        **그림 8: 런타임 가용성 확인 시작 조건에 대 한 속성 창**

 위의 시작 조건은 부트스트래퍼 패키지에 의해 설치 될 때 VSTO 런타임이 있는지 명시적으로 확인 합니다.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Office에서 설치한 VSTO 런타임을 검색 하는 시작 조건 구성

1. **시작 조건 (사이 Addinsetup)** 편집기에서 **대상 컴퓨터 검색**을 마우스 오른쪽 단추로 클릭 한 다음 **레지스트리 검색 추가**를 클릭 합니다.
2. **RegistryEntry1** 검색 조건을 선택 하 고 조건을 마우스 오른쪽 단추로 클릭 한 다음 **속성 창**을 선택 합니다.
3. **속성** 창에서 다음 속성을 설정 합니다.
    1. **(Name)** 값을 설정 하 여 **Office VSTO Runtime을 검색**합니다.
    2. **속성** 의 값을 **OfficeRuntime**로 변경 합니다.
    3. **RegKey** 의 값을 **SOFTWARE \\ Microsoft \\ VSTO Runtime Setup \\ v4**로 설정 합니다.
    4. **Root** 속성을 **Vsdrrhklm**로 설정 된 상태로 둡니다.
    5. **Value** 속성을 **Version**로 변경 합니다.

4. **시작 조건 (창 고 Addinsetup)** 편집기에서 앞에서 정의한 **VSTO 2010 런타임 가용성** 시작 조건을 선택 하 고 조건을 마우스 오른쪽 단추로 클릭 한 다음 **속성 창**을 선택 합니다.

5. **Condition** 속성의 값을 Vstorun10.0.30319 ststststststv= ** \> "" 또는 OFFICERUNTIME \> = "10.0.21022"** 로 변경 합니다. 버전 번호는 추가 기능에 필요한 런타임 버전에 따라 다를 수 있습니다.

    ![시작 조건에 대 한 속성 창의 스크린샷](media/setup-project-figure-9.jpg)
  
    **그림 9: Redist 또는 Office 시작 조건을 통해 런타임 가용성 확인을 위한 속성 창**

추가 기능이 .NET Framework 4 이상 버전을 대상으로 하는 경우 참조 되는 PIA (주 Interop 어셈블리) 내의 형식을 VSTO 어셈블리에 포함할 수 있습니다.

다음 단계를 수행 하 여 Interop 형식이 추가 기능에 포함 되는지 확인 합니다.

1. 솔루션 탐색기에서 참조 노드를 확장 합니다.
2. PIA 참조 중 하나를 선택 합니다 (예: **Office**).
3. F4 또는 어셈블리 상황에 맞는 메뉴에서 속성을 선택 하 여 속성 창을 봅니다.
4. 속성 **포함 Interop 형식의**값을 확인 합니다.

값이 **True**로 설정 된 경우에는 형식이 포함 되 고,로 건너뛰어 [**설치 프로젝트**](#to-build-the-setup-project) 섹션을 빌드할 수 있습니다.

자세한 내용은 [형식 동등 및 포함 된 Interop 형식](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types) 을 참조 하세요.

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>시작 조건을 구성 하 여 Office Pia에 대해 검색 하려면

1. **시작 조건 (사이에 Addinsetup)** 편집기에서 **대상 컴퓨터의 요구 사항을**마우스 오른쪽 단추로 클릭 한 다음 **Windows Installer 시작 조건 추가를 클릭**합니다. 이 시작 조건은 특정 구성 요소 ID를 검색 하 여 Office PIA를 검색 합니다.
2. **Component1 검색** 을 마우스 오른쪽 단추로 클릭 하 고 **속성 창** 을 클릭 하 여 시작 조건의 속성을 표시 합니다.
3. **속성 창**에서 다음 속성을 설정 합니다.

    1. **(Name)** 속성 값을 변경 하 여 **Office 공유 PIA를 검색** 합니다.
    2. 구성 요소의 값을 사용 하는 Office 구성 요소에 대 한 구성 요소 **Id로 변경** 합니다. 아래 표에서 구성 요소 Id 목록을 찾을 수 있습니다 (예: **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}**).
    3. **Property** 속성의 값을 **hassharedpia**로 변경 합니다.

4. **시작 조건 (Condition1 Addinsetup)** 편집기에서 마우스 오른쪽 단추를 클릭 **Condition1** 한 다음 **속성 창** 을 클릭 하 여 시작 조건의 속성을 표시 합니다.

5. **Condition1**의 다음 속성을 변경 합니다.

    1. **(이름)** 을 변경 하 여 **Office 공유 PIA 사용 가능**여부를 확인 합니다.
    2. **조건을** **hassharedpia**로 변경 합니다.
    3. **InstallUrl** 을 비워 둡니다.
    4. **Message** **Excel과의 상호 작용을 위한 필수 구성 요소로 메시지를 변경 하는 것은 불가능 합니다. setup.exe를 실행 하십시오 **.

    ![Office 공유 PIA 시작 조건 확인에 대 한 속성 창의 스크린샷](media/setup-project-figure-10.jpg)
  
    **그림 10: Office 공유 PIA 시작 조건의 속성 창**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Microsoft Office에 대 한 주 Interop 어셈블리의 구성 요소 Id

|주 interop 어셈블리|Office 2010|Office 2013|Office 2013 (64 비트)|Office 2016|Office 2016 (64 비트)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153732-D670-4E44-8AB7-500F2B57686}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-B5B8022333E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|Microsoft Forms 2.0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Smart Tag(스마트 태그)|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|Office 공유|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|{625F5772-C1B3-497E-8ABE-7254EDB00506}|
|프로젝트|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![최종 시작 조건의 스크린샷](media/setup-project-figure-11.jpg)

  **그림 11: 최종 시작 조건**

추가 기능 설치에 대 한 시작 조건을 구체적으로 구체화할 수 있습니다. 예를 들어 실제 대상 Office 응용 프로그램이 설치 되어 있는지 확인 하는 것이 유용할 수 있습니다.

### <a name="to-build-the-setup-project"></a>설치 프로젝트를 빌드하려면

1. **솔루션 탐색기**에서, 팀 간 **addinsetup** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **빌드**를 클릭 합니다.
2. **Windows 탐색기**를 사용 하 여 **폴더의 출력** 디렉터리로 이동 하 고, 선택한 빌드 구성에 따라 릴리스 또는 디버그 폴더로 이동 합니다. 폴더의 모든 파일을 사용자가 액세스할 수 있는 위치에 복사 합니다.

Excel 추가 기능 설치를 테스트 하려면

1. 지역에서 **Addinaddinsetup** 을 복사한 위치로 이동 합니다.
2. setup.exe 파일을 두 번 클릭 하 여이 기능을 **설치 합니다.** 표시 되는 모든 소프트웨어 사용 조건을 수락 하 고 설치 마법사를 완료 하 여 사용자 컴퓨터에 추가 기능을 설치 합니다.

Excel Office 솔루션은 설치 중에 지정 된 위치에서 설치 하 고 실행 해야 합니다.

## <a name="additional-requirements-for-document-level-solutions"></a>문서 수준 솔루션에 대 한 추가 요구 사항

문서 수준 솔루션을 배포 하려면 Windows Installer 설치 프로젝트에서 몇 가지 구성 단계가 필요 합니다.

다음은 문서 수준 솔루션을 배포 하는 데 필요한 기본 단계 목록입니다.

- Visual Studio 설치 프로젝트를 만듭니다.
- 문서 수준 솔루션의 기본 출력을 추가 합니다. 기본 출력에는 Microsoft Office 문서도 포함 됩니다.
- 배포 및 응용 프로그램 매니페스트를 느슨한 파일로 추가 합니다.
- 설치 관리자 패키지 (유틸리티 어셈블리 제외)에서 종속 구성 요소를 제외 합니다.
- 필수 구성 요소 패키지를 구성 합니다.
- 시작 조건을 구성 합니다.
- 설치 프로젝트를 빌드하고 배포 위치에 결과를 복사 합니다.
- 설치 프로그램을 실행 하 여 사용자 컴퓨터에 문서 수준 솔루션을 배포 합니다.
- 필요한 경우 사용자 지정 문서 속성을 업데이트 합니다.

### <a name="changing-the-location-of-the-deployed-document"></a>배포 된 문서의 위치 변경

Office 문서 내의 속성은 문서 수준 솔루션을 찾는 데 사용 됩니다. 문서가 VSTO 어셈블리와 동일한 폴더에 설치 된 경우에는 변경이 필요 하지 않습니다. 그러나 다른 폴더에 설치 된 경우에는 설치 중에 이러한 속성을 업데이트 해야 합니다.

이러한 문서 속성에 대 한 자세한 내용은 [사용자 지정 문서 속성 개요](custom-document-properties-overview.md)를 참조 하세요.

이러한 속성을 변경 하려면 설치 하는 동안 사용자 지정 작업을 사용 해야 합니다.

다음 예제에서는 라는 문서 수준 솔루션을 사용 하 고,이 솔루션을 사용 합니다. 이 경우 레지스트리 키를 설정 하는 것을 제외 하 고 위에 설명 된 것과 동일한 단계를 사용 하 여이 설치 프로젝트를 구성 합니다.

Visual Studio 솔루션에 사용자 지정 작업 프로젝트를 추가 하려면

1. **솔루션 탐색기** 에서 **Office 문서 배포 프로젝트** 를 마우스 오른쪽 단추로 클릭 하 여 새 .net 콘솔 프로젝트를 솔루션에 추가 합니다.
2. **추가** 를 확장 하 고 **새 프로젝트**를 클릭 합니다.
3. 콘솔 앱 템플릿을 선택 하 고 프로젝트 이름을 **AddCustomizationCustomAction**로 선택 합니다.

    ![솔루션 탐색기의 스크린샷 AddCustomizationCustomAction](media/setup-project-figure-15.jpg)
  
    **그림 12: 솔루션 탐색기 AddCustomizationCustomAction**

4. 이러한 어셈블리에 대 한 참조를 추가 합니다.
    1. System.ComponentModel
    2. System.Configuration.Install
    3. VisualStudio.
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. 이 코드를 Program.cs 또는 Program에 복사 합니다.

```csharp
    using System;
    using System.IO;
    using System.Collections;
    using System.ComponentModel;
    using System.Configuration.Install;
    using Microsoft.VisualStudio.Tools.Applications;
    using Microsoft.VisualStudio.Tools.Applications.Runtime;

    namespace AddCustomizationCustomAction
    {
        [RunInstaller(true)]
        public class AddCustomizations : Installer
        {
            public AddCustomizations() : base() { }

            public override void Install(IDictionary savedState)
            {
                base.Install(savedState);

                //Get the CustomActionData Parameters
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;
                string assemblyLocation = Context.Parameters.ContainsKey("assemblyLocation") ? Context.Parameters["assemblyLocation"] : String.Empty;
                string deploymentManifestLocation = Context.Parameters.ContainsKey("deploymentManifestLocation") ? Context.Parameters["deploymentManifestLocation"] : String.Empty;
                Guid solutionID = Context.Parameters.ContainsKey("solutionID") ? new Guid(Context.Parameters["solutionID"]) : new Guid();

                string newDocLocation = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation));

                try
                {
                    //Move the file and set the Customizations
                    if (Uri.TryCreate(deploymentManifestLocation, UriKind.Absolute, out Uri docManifestLocationUri))
                    {
                        File.Move(documentLocation, newDocLocation);
                        ServerDocument.RemoveCustomization(newDocLocation);
                        ServerDocument.AddCustomization(newDocLocation, assemblyLocation,
                                                        solutionID, docManifestLocationUri,
                                                        true, out string[] nonpublicCachedDataMembers);
                    }
                    else
                    {
                        LogMessage("The document could not be customized.");
                    }
                }
                catch (ArgumentException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (DocumentNotCustomizedException)
                {
                    LogMessage("The document could not be customized.");
                }
                catch (InvalidOperationException)
                {
                    LogMessage("The customization could not be removed.");
                }
                catch (IOException)
                {
                    LogMessage("The document does not exist or is read-only.");
                }
            }

            public override void Rollback(IDictionary savedState)
            {
                base.Rollback(savedState);
                DeleteDocument();
            }
            public override void Uninstall(IDictionary savedState)
            {
                base.Uninstall(savedState);
                DeleteDocument();
            }
            private void DeleteDocument()
            {
                string documentLocation = Context.Parameters.ContainsKey("documentLocation") ? Context.Parameters["documentLocation"] : String.Empty;

                try
                {
                    File.Delete(Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), Path.GetFileName(documentLocation)));
                }
                catch (Exception)
                {
                    LogMessage("The document doesn't exist or is read-only.");
                }
            }
            private void LogMessage(string Message)
            {
                if (Context.Parameters.ContainsKey("LogFile"))
                {
                    Context.LogMessage(Message);
                }
            }

            static void Main() { }
            }
    }
```

문서에 사용자 지정을 추가 하려면 VSTO 문서 수준 솔루션의 솔루션 ID가 있어야 합니다. 이 값은 Visual Studio 프로젝트 파일에서 검색 됩니다.

솔루션 ID를 검색 하려면

1. **빌드** 메뉴에서 **솔루션 빌드** 를 클릭 하 여 문서 수준 솔루션을 빌드하고 솔루션 ID 속성을 프로젝트 파일에 추가 합니다.
2. **솔루션 탐색기**에서 문서 **수준 프로젝트의 문서 수준 프로젝트를** 마우스 오른쪽 단추로 클릭 합니다.
3. **UnloadProject** 을 클릭 하 여 Visual Studio 내에서 프로젝트 파일에 액세스 합니다.

    ![Excel 문서 솔루션을 언로드하 솔루션 탐색기의 스크린샷](media/setup-project-figure-16.jpg)

    **그림 13: Excel 문서 솔루션 언로드**

4. **솔루션 탐색기**에서 마우스 오른쪽 단추를 클릭 **하 고,** 마우스 오른쪽 단추로 클릭 하 여 **편집** **합니다.**
5. **PropertyGroup** 요소 **ExcelWorkbookProject** 내에서 **솔루션 id** 요소를 찾습니다.
6. 이 요소의 GUID 값을 복사 합니다.

    ![솔루션 Id 검색](media/setup-project-figure-17.jpg)

    **그림 14: 솔루션 Id 검색**

7. **솔루션 탐색기**에서 마우스 오른쪽 단추를 클릭 **하 여** 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **프로젝트 다시 로드**를 클릭 합니다.
8. 표시 되는 대화 상자에서 **예** 를 클릭 하 여 **excel 프로젝트** 편집기를 닫습니다.
9. **솔루션 ID** 는 설치 사용자 지정 작업에 사용 됩니다.

마지막 단계는 **설치** 및 **제거** 단계에 대 한 사용자 지정 작업을 구성 하는 것입니다.

### <a name="to-configure-the-setup-project"></a>설치 프로젝트를 구성 하려면

1. **솔루션 탐색기**에서 마우스 오른쪽 단추 **를 클릭 하**고, **추가** 를 확장 하 고, **프로젝트 출력**을 클릭 합니다.
2. **프로젝트 출력 그룹 추가** 대화 상자의 **프로젝트** 목록에서 **AddCustomizationCustomAction**를 클릭 합니다.
3. **기본 출력** 을 선택 하 고 **확인** 을 클릭 하 여 대화 상자를 닫고 사용자 지정 작업을 포함 하는 어셈블리를 설치 프로젝트에 추가 합니다.

    ![문서 매니페스트 사용자 지정 작업-프로젝트 출력 그룹 추가 창의 스크린샷](media/setup-project-figure-18.jpg)

    **그림 15: 문서 매니페스트 사용자 지정 작업-프로젝트 출력 그룹 추가**

4. **솔루션 탐색기**에서 마우스 오른쪽 단추로 클릭 하 여 **excel 통합 프로그램 설치**합니다.
5. **보기** 를 확장 하 고 **사용자 지정 작업**을 클릭 합니다.
6. **사용자 지정 작업 (Excel 통합 프로그램 설정)** 편집기에서 **사용자 지정 작업** 을 마우스 오른쪽 단추로 클릭 하 고 **사용자 지정 작업 추가**를 클릭 합니다.
7. **프로젝트에서 항목 선택** 대화 상자의 **찾는 위치** 목록에서 **응용 프로그램 폴더**를 클릭 합니다. **AddCustomizationCustomAction (활성)에서 기본 출력** 을 선택 하 고 **확인** 을 클릭 하 여 설치 단계에 사용자 지정 작업을 추가 합니다.
8. **설치 노드**아래에서 **AddCustomizationCustomAction (Active)의 기본 출력**을 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 합니다. 사용자 지정 작업의 이름을 **내 문서에 복사 하 고 사용자 지정을 첨부**합니다.
9. **제거 노드**아래에서 **AddCustomizationCustomAction (Active)의 기본 출력** 을 마우스 오른쪽 단추로 클릭 하 고 **이름 바꾸기**를 클릭 합니다. **문서 폴더에서**사용자 지정 작업의 이름을 지정 합니다.

    ![문서 매니페스트 사용자 지정 작업 창의 스크린샷](media/setup-project-figure-19.jpg)

    **그림 16: 문서 매니페스트 사용자 지정 작업**

10. **사용자 지정 작업 (Excel 통합 문서 설정)** 편집기에서 **내 문서에 문서 복사 및 사용자 지정 연결** 을 마우스 오른쪽 단추로 클릭 하 고 **속성 창**을 클릭 합니다.
11. **CustomActionData** **속성** 창에서 사용자 지정 DLL의 위치, 배포 매니페스트 및 Microsoft Office 문서의 위치를 입력 합니다. 또한 솔루션 Id가 필요 합니다.
12. 설치 오류를 파일에 기록 하려면 로그 파일 매개 변수를 포함 합니다.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![문서를 내 문서에 복사 하는 사용자 지정 작업의 스크린샷 속성 창](media/setup-project-figure-20.jpg)

    **그림 17: 문서를 내 문서에 복사 하는 사용자 지정 작업**

13. 제거에 대 한 사용자 지정 작업을 수행 하려면 문서 이름이 필요 합니다. 그러면 **CustomActionData** 에서 동일한 documentlocation 매개 변수를 사용 하 여 제공할 수 있습니다.

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. 프로젝트를 컴파일하고 배포 **합니다.**
15. **내 문서** 폴더를 확인 하 고 ExcelWorkbookProject.xlsx 파일을 엽니다.

## <a name="additional-resources"></a>추가 리소스

[방법: Visual Studio Tools for Office 런타임 설치](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Office 주 Interop 어셈블리](office-primary-interop-assemblies.md)

[VSTO 추가 기능에 대 한 레지스트리 항목](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[Windows 레지스트리에 양식 영역 지정](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[문서에 신뢰 부여](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>저자 정보

Wouter van Vugt는 Office Open XML 기술을 사용 하는 Microsoft MVP 이며, SharePoint, Microsoft Office 및 관련 .NET 기술로 Oba (Office Business Applications)를 만드는 데 초점을 맞춘 독립적인 컨설턴트입니다.
Wouter는 [MSDN](/previous-versions/office/developer/office-2007/bb879915(v=office.12))과 같은 개발자 커뮤니티 사이트에 대 한 빈번한 참가자입니다. 그는 여러 백서와 문서를 게시 하 여 Open XML: 문서에 설명 된 문서를 제공 합니다.
Wouter는 다양 한 채널을 통해 최첨단 기술 콘텐츠를 제공 하는 것에 초점을 맞춘 창립자 (자문 위원)의 코드입니다. 블로그를 읽어 Wouter에 대해 자세히 알아볼 수 있습니다.

Ted Pattison는 SharePoint MVP, 저자, 강사 및 Ted Pattison 그룹의 창립자입니다. 2005에 도달 하 여 Microsoft의 개발자 플랫폼 Evangelism 그룹이 Windows SharePoint Services 3.0 및 Microsoft Office SharePoint Server 2007에 대 한 Ascend 개발자 교육 교육 과정을 작성 했습니다. 그 이후에는 Ted가 SharePoint 2007 기술에 대 한 전문 개발자의 교육에 전적으로 집중 했습니다. Ted는 비즈니스 솔루션을 빌드하기 위한 개발 플랫폼으로 SharePoint를 사용 하는 방법에 중점을 둔 Microsoft Press for Microsoft Press를 Windows SharePoint Services 3.0 내부에 작성 했습니다. 또한 Ted는 MSDN Magazine의 Office 공간에 대 한 개발자 중심의 열을 작성 합니다.
