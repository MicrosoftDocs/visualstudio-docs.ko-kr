---
title: Windows 설치 관리자를 사용하여 Office 솔루션을 위한 Visual Studio 도구 배포
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
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444908"
---
# <a name="deploying-a-visual-studio-tools-for-office-solution-using-windows-installer"></a>Windows 설치 관리자를 사용하여 Office 솔루션을 위한 Visual Studio 도구 배포

## <a name="summary"></a>요약

Visual Studio Installer 프로젝트를 사용하여 VSTO(추가 기능) 추가 기능 또는 문서 수준 솔루션을 배포하는 방법에 대해 알아봅니다.

우터 반 부그트, 코드 고문

테드 패티슨, 테드 패티슨 그룹

이 문서는 원래 작성자의 허가를 받아 Microsoft에서 업데이트했습니다.

**다음에 적용됩니다.** 사무실, 마이크로 소프트 오피스, 마이크로 소프트 비주얼 스튜디오를위한 비주얼 스튜디오 도구.

## <a name="overview"></a>개요

VSTO 솔루션을 개발하고 Windows Installer 패키지를 사용하여 솔루션을 배포할 수 있습니다. 이 설명에서는 간단한 Office 추가 기능을 배포하기 위한 단계가 포함되어 있습니다.

## <a name="deployment-methods"></a>배포 방법

ClickOnce쉽게 추가 기능 및 솔루션에 대한 설정을 만드는 데 사용할 수 있습니다. 그러나 컴퓨터 수준 추가 기능과 같은 관리 권한이 필요한 추가 기능을 설치할 수는 없습니다.

관리 권한이 필요한 추가 기능을 Windows Installer를 사용하여 설치할 수 있지만 설치를 만들기 위해 더 많은 노력이 필요합니다.

ClickOnce를 사용하여 VSTO 솔루션을 배포하는 방법에 대한 개요는 ClickOnce 를 [사용하여 Office 솔루션 배포를](deploying-an-office-solution-by-using-clickonce.md)참조하세요.

## <a name="deploying-office-solutions-that-target-the-vsto-runtime"></a>VSTO 런타임을 대상으로 하는 Office 솔루션 배포

ClickOnce 및 Windows 설치 관리자 패키지Office 솔루션을 설치할 때 동일한 기본 작업을 수행 해야 합니다.

1. 사용자 컴퓨터에 필수 구성 요소를 설치합니다.
2. 솔루션에 대한 특정 구성 요소를 배포합니다.
3. 추가 기능의 경우 레지스트리 항목을 만듭니다.
4. 솔루션을 신뢰하여 실행할 수 있습니다.

### <a name="required-prerequisite-components-on-the-target-computer"></a>대상 컴퓨터의 필수 필수 구성 요소

VSTO 솔루션을 실행하기 위해 컴퓨터에 설치해야 하는 소프트웨어 목록은 다음과 같습니다.

- 마이크로 소프트 오피스 2010 이상.
- 마이크로 소프트 .NET 프레임 워크 4 이상.
- Microsoft Visual Studio 2010 Tools for Office Runtime.
  런타임은 추가 기능 및 문서 수준 솔루션을 관리하는 환경을 제공합니다. 런타임 버전은 Microsoft Office와 함께 제공되지만 추가 기능을 사용하여 특정 버전을 재배포할 수 있습니다.
- 임베디드 Interop 형식을 사용하지 않는 경우 Microsoft Office의 기본 Interop 어셈블리입니다.
- 프로젝트에서 참조하는 모든 유틸리티 어셈블리입니다.

### <a name="specific-components-for-the-solution"></a>솔루션의 특정 구성 요소

설치 관리자 패키지는 사용자의 컴퓨터에 다음 구성 요소를 설치해야 합니다.

- 문서 수준 솔루션을 만드는 경우 Microsoft Office 문서입니다.
- 사용자 지정 어셈블리 및 필요한 모든 어셈블리입니다.
- 구성 파일과 같은 추가 구성 요소입니다.
- 응용 프로그램 매니페스트(.manifest)입니다.
- 배포 매니페스트(.vsto)입니다.

### <a name="registry-entries-for-add-ins"></a>추가 기능에 대한 레지스트리 항목

Microsoft Office는 레지스트리 항목을 사용하여 추가 기능을 찾고 로드합니다. 이러한 레지스트리 항목은 배포 프로세스의 일부로 만들어야 합니다. 이러한 레지스트리 항목에 대한 자세한 내용은 [VSTO 추가 기능의 레지스트리 항목을](registry-entries-for-vsto-add-ins.md)참조하십시오.

사용자 지정 양식 영역을 표시하는 Outlook 추가 기능에는 양식 영역을 식별할 수 있는 추가 레지스트리 항목이 필요합니다. 레지스트리 항목에 대한 자세한 내용은 [Outlook 양식 영역에 대한 레지스트리 항목을](registry-entries-for-vsto-add-ins.md#OutlookEntries)참조하십시오.

문서 수준 솔루션에는 레지스트리 항목이 필요하지 않습니다. 대신 문서 내부의 속성이 사용자 지정을 찾는 데 사용됩니다. 이러한 속성에 대한 자세한 내용은 [사용자 지정 문서 속성 개요를](custom-document-properties-overview.md)참조하십시오.

### <a name="trusting-the-vsto-solution"></a>VSTO 솔루션 신뢰

사용자 지정을 실행하려면 컴퓨터에서 솔루션을 신뢰할 수 있어야 합니다. 추가 기능을 인증서로 매니페스트에 서명하거나 포함 목록과 트러스트 관계를 만들거나 컴퓨터의 신뢰할 수 있는 위치에 설치하여 관리자를 신뢰할 수 있습니다.

서명인증서를 얻는 방법에 대한 자세한 내용은 [ClickOnce 배포 및 Authenticode](../deployment/clickonce-and-authenticode.md)를 참조하십시오. 트러스트 솔루션에 대한 자세한 내용은 [포함 목록을 사용하여 Office 솔루션 신뢰](trusting-office-solutions-by-using-inclusion-lists.md)를 참조하십시오. Windows 설치 관리자 파일에 사용자 지정 작업이 있는 포함 목록 항목을 추가할 수 있습니다. 포함 목록을 사용하도록 설정하는 방법에 대한 자세한 내용은 [포함 목록 보안 구성 방법을](how-to-configure-inclusion-list-security.md)참조하십시오.

두 옵션을 모두 사용하지 않으면 사용자가 솔루션을 신뢰할지 여부를 결정할 수 있도록 신뢰 프롬프트가 사용자에게 표시됩니다.

문서 수준 솔루션과 관련된 보안에 대한 자세한 내용은 [문서에 대한 신뢰 부여 를](granting-trust-to-documents.md)참조하십시오.

## <a name="creating-a-basic-installer"></a>기본 설치 관리자 만들기

설치 및 배포 프로젝트 템플릿은 다운로드할 수 있는 [Microsoft Visual Studio 설치 관리자 프로젝트](https://marketplace.visualstudio.com/items?itemName=visualstudioclient.MicrosoftVisualStudio2017InstallerProjects) 확장에 포함되어 있습니다.

Office 솔루션에 대한 설치 관리자를 만들려면 다음 작업을 수행해야 합니다.

- 배포할 Office 솔루션의 구성 요소를 추가합니다.
- 응용 프로그램 수준 추가 기능의 경우 레지스트리 키를 구성합니다.
- 최종 사용자 컴퓨터에 설치할 수 있도록 필수 구성 요소를 구성합니다.
- 시작 조건을 구성하여 필요한 필수 구성 요소를 사용할 수 있는지 확인합니다. 필요한 모든 필수 구성 프로그램이 설치되지 않은 경우 시작 조건을 사용하여 설치를 차단할 수 있습니다.

첫 번째 단계는 설치 프로젝트를 만드는 것입니다.

### <a name="to-create-the-addin-setup-project"></a>AddIn 설치 설정 프로젝트를 만들려면

1. 배포할 Office AddIn 프로젝트를 엽니다. 이 예제에서는 ExcelAddIn이라는 Excel 추가 기능을 사용하고 있습니다.
2. Office 프로젝트를 열려면 **파일** 메뉴에서 **추가를** 확장하고 **새 프로젝트를** 클릭하여 새 프로젝트를 추가합니다.
::: moniker range="=vs-2017"
3. 새 **프로젝트 추가** 대화 상자에서 프로젝트 **유형** 창에서 **다른 프로젝트 유형을** 확장한 다음 설치 및 **배포를** 확장한 다음 **Visual Studio 설치 관리자를**선택합니다.
4. **템플릿** 창에서 **Visual Studio에 설치된** 템플릿 그룹에서 설치 **프로젝트를** 선택합니다.
::: moniker-end
::: moniker range="=vs-2019"
3. 새 **프로젝트 추가** 대화 상자에서 **설치 프로젝트** 템플릿을 선택합니다.
4. **다음**을 클릭합니다.
::: moniker-end

5. **이름** 상자에서 **OfficeAddInSetup**을 입력합니다.
::: moniker range="=vs-2017"
6. **열기를** 클릭하여 새 설치 프로젝트를 만듭니다.
::: moniker-end
::: moniker range="=vs-2019"
6. 새 설치 프로젝트를 만들려면 **만들기를** 클릭합니다.
::: moniker-end

Visual Studio에서 새 설치 프로젝트에 대한 파일 시스템 탐색기를 엽니다. 파일 시스템 탐색기를 사용하면 설치 프로젝트에 파일을 추가할 수 있습니다.

   ![설치 프로젝트에 대한 파일 시스템 탐색기의 스크린샷](media/setup-project-figure-1.png)

   **그림 1: 설치 프로젝트에 대한 파일 시스템 탐색기**

설치 프로젝트는 ExcelAddIn을 배포해야 합니다. 설치 프로젝트에 ExcelAddIn 프로젝트 출력을 추가하여 이 작업에 대한 설치 프로젝트를 구성할 수 있습니다.

### <a name="to-add-the-exceladdin-project-output"></a>ExcelAddIn 프로젝트 출력을 추가하려면

1. 솔루션 **탐색기에서** **OfficeAddInSetup을**마우스 오른쪽 단추로 **클릭한** 다음 **프로젝트 출력**을 클릭합니다.
2. 프로젝트 **출력 그룹 추가** 대화 상자에서 프로젝트 목록에서 **ExcelAddIn** 및 **기본 출력을 선택합니다.**
3. **확인을** 클릭하여 설치 프로젝트에 프로젝트 출력을 추가합니다.

    ![설치 프로젝트 추가 프로젝트 출력 그룹 대화 상자의 스크린샷](media/setup-project-figure-2.png)

    **그림 2: 설치 프로젝트 프로젝트 프로젝트 출력 그룹 대화 상자 추가**

설치 프로젝트는 배포 매니페스트 및 응용 프로그램 매니페스트를 배포해야 합니다. 이 두 파일을 ExcelAddIn 프로젝트의 출력 폴더에서 독립 실행형 파일로 설치 프로젝트에 추가합니다.

### <a name="to-add-the-deployment-and-application-manifests"></a>배포 및 응용 프로그램 매니페스트를 추가하려면

1. 솔루션 **탐색기에서** **OfficeAddInSetup을**마우스 오른쪽 단추로 클릭하고 **추가를**클릭하고 **파일을**클릭합니다.
2. 파일 **추가** 대화 상자에서 **ExcelAddIn** 출력 디렉토리로 이동합니다. 일반적으로 출력 디렉터리는 선택한 빌드 구성에 따라 프로젝트 루트 디렉터리의 **bin\\릴리스** 하위 폴더입니다.
3. **ExcelAddIn.vsto** 및 **ExcelAddIn.dll.manifest** 파일을 선택하고 **열기를** 클릭하여 이 두 파일을 설치 프로젝트에 추가합니다.

    ![솔루션 탐색기에서 응용 프로그램 및 배포 매니페스트의 스크린샷](media/setup-project-figure-3.jpg)

    **그림 3: 솔루션 탐색기의 추가 기능 탐색기용 응용 프로그램 및 배포 매니페스트**

ExcelAddIn을 참조하는 것은 ExcelAddIn에 필요한 모든 구성 요소를 포함합니다. 이러한 구성 요소는 올바르게 등록할 수 있도록 필수 구성 요소를 사용하여 제외하고 배포해야 합니다. 또한 설치가 시작되기 전에 소프트웨어 라이센스 약관을 표시하고 수락해야 합니다.

### <a name="to-exclude-the-exceladdin-project-dependencies"></a>ExcelAddIn 프로젝트 종속성을 제외하려면

1. 솔루션 **탐색기에서** **OfficeAddInSetup** 노드에서 **Microsoft .NET Framework** 또는 **Detected Dependencies** ** \*로 끝나는 모든 어셈블리를 제외한 검색된 종속성 항목 아래에 있는 모든 종속성 항목을 선택합니다. 유틸리티.dll**. 유틸리티 어셈블리는 응용 프로그램과 함께 배포되어야 합니다.
2. 그룹을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
3. **속성** 창에서 설정 프로젝트에서 종속 어셈블리를 제외하려면 **속성 제외를** **True로** 변경합니다. 유틸리티 어셈블리를 제외하지 않도록 합니다.

    ![제외할 종속성을 보여주는 솔루션 탐색기의 스크린샷](media/setup-project-figure-4.jpg)

    **그림 4: 종속성 제외**

부트스트래퍼라고도 하는 설치 프로그램을 추가하여 필수 구성 요소를 설치하도록 Windows Installer 패키지를 구성할 수 있습니다. 이 설치 프로그램은 부트스트래핑이라는 프로세스인 필수 구성 요소를 설치할 수 있습니다.

**ExcelAddIn의**경우 추가 기능을 올바르게 실행하려면 먼저 이러한 필수 구성 조건을 설치해야 합니다.

- Office 솔루션에서 대상으로 하는 Microsoft .NET 프레임워크 버전입니다.
- Microsoft Visual Studio 2010 Tools for Office 런타임입니다.

종속 구성 요소를 필수 구성 요소로 구성하려면

1. 솔루션 **탐색기에서** **OfficeAddInSetup** 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성을**선택합니다.
2. **OfficeAddInSetup 속성 페이지** 대화 상자가 나타납니다.
3. 필수 **구성 조건** 단추를 클릭합니다.
4. 필수 구성 조건 대화 상자에서 .NET 프레임워크의 올바른 버전과 Office 런타임용 Microsoft Visual Studio 도구를 선택합니다.

    ![필수 구성 조건 대화 상자의 스크린샷](media/setup-project-figure-5.png)

    **그림 5: 전제 조건 대화 상자**

    > [!NOTE]
    >Visual Studio 설치 프로젝트에서 구성된 필수 구성 항목 패키지 중 일부는 선택한 빌드 구성에 따라 다릅니다. 사용하는 각 빌드 구성에 적합한 필수 구성 요소를 선택해야 합니다.

Microsoft Office는 레지스트리 키를 사용하여 추가 기능을 찾습니다. HKEY\_현재\_사용자 하이브의 키는 각 개별 사용자에 대한 추가 기능을 등록하는 데 사용됩니다. HKEY\_LOCAL\_MACHINE 하이브 아래의 키는 컴퓨터의 모든 사용자에 대한 추가 기능을 등록하는 데 사용됩니다. 레지스트리 키에 대한 자세한 내용은 [VSTO 추가 기능의 레지스트리 항목을](registry-entries-for-vsto-add-ins.md)참조하십시오.

### <a name="to-configure-the-registry"></a>레지스트리를 구성하려면

1. 솔루션 **탐색기에서** **OfficeAddInSetup**을 마우스 오른쪽 단추로 클릭합니다.
2. **보기를 확장합니다.**
3. **레지스트리 편집기를** 열려면 레지스트리를 클릭합니다.
4. **레지스트리(OfficeAddInSetup)** 편집기에서 **HKEY\_로컬\_컴퓨터를** 확장한 다음 **소프트웨어를**확장합니다.
5. **HKEY\_로컬\_\\기계 소프트웨어에서**발견 된 ** \[제조업체\]**?키를 삭제합니다.
6. **HKEY\_현재\_사용자를** 확장한 다음 **소프트웨어.**
7. **HKEY\_현재\_\\사용자 소프트웨어**에서 찾을 ** \[수 있는 제조업체\] ** 키를 삭제합니다.
8. 추가 기능 설치에 대한 레지스트리 키를 추가하려면 **사용자/기기 하이브** 키를 마우스 오른쪽 단추로 클릭하여 **새 키를**선택합니다. 새 키의 이름에 **소프트웨어** 텍스트를 사용합니다. 새로 만든 **소프트웨어** 키를 마우스 오른쪽 버튼으로 클릭하고 텍스트 **마이크로 소프트**.
9. 비슷한 프로세스를 사용하여 추가 기능 등록에 필요한 전체 키 계층 구조를 만듭니다.

    **사용자/기계\\하이브\\\\소프트웨어\\\\마이크로 소프트\\오피스 엑셀 애드인 샘플Company.ExcelAddIn**

    회사 이름은 고유성을 제공하기 위해 추가 기능 의 이름에 대한 접두사로 자주 사용됩니다.

10. **SampleCompany.ExcelAddIn** 키를 마우스 오른쪽 단추로 클릭하고 **새**키를 선택하고 **문자열 값을 클릭합니다.** 이름에 대한 텍스트 **설명을** 사용합니다.
11. 이 단계를 사용하여 세 가지 값을 더 추가합니다.
    - **친용이름** **문자열** 형식
    - **DWORD** 형식의 **로드비헤이비어**
    - 형식 **문자열의** **매니페스트**

12. 레지스트리 편집기에서 **설명** 값을 마우스 오른쪽 단추로 클릭하고 **속성 창을**클릭합니다. 속성 **창에서**Value 속성에 대해 **Excel 데모 추가 기능을** 입력합니다.
13. 레지스트리 편집기에서 **FriendlyName** 키를 선택합니다. 속성 **창에서** **Value** 속성을 **Excel 데모 AddIn으로**변경합니다.
14. 레지스트리 편집기에서 **LoadBehavior** 키를 선택합니다. 속성 **창에서** **Value** 속성을 **3으로 변경합니다.** LoadBehavior에 대한 값 3은 호스트 응용 프로그램을 시작할 때 추가 기능이 로드되어야 함을 나타냅니다. 로드 동작에 대한 자세한 내용은 [VSTO 추가 기능의 레지스트리 항목을](registry-entries-for-vsto-add-ins.md)참조하십시오.

15. 레지스트리 편집기에서 **매니페스트** 키를 선택합니다. 속성 **창에서** **값** 속성을 **파일로 변경합니다:///[TARGETDIR]ExcelAddIn.vsto|vstolocal**

    ![레지스트리 편집기의 스크린샷](media/setup-project-figure-6.png)

    **그림 6: 레지스트리 키 설정**

      VSTO 런타임은 이 레지스트리 키를 사용하여 배포 매니페스트를 찾습니다. [TARGETDIR] 매크로는 추가 기능이 설치된 폴더로 바뀝습니다. 매크로에는 후행 \ 문자가 포함되므로 배포 매니페스트의 파일 이름은 \문자가 없는 ExcelAddIn.vsto여야 합니다.
      **vstolocal** 접두사는 VSTO 런타임에 추가 기능이 ClickOnce 캐시 대신 이 위치에서 로드되어야 함을 알려줍니다. 이 접두사를 제거하면 런타임이 ClickOnce 캐시에 사용자 지정을 복사합니다.

   >[!WARNING]
   >Visual Studio의 레지스트리 편집기는 매우 주의해야 합니다. 예를 들어 실수로 DeleteAtUninstall를 잘못된 키에 대해 설정한 경우 레지스트리의 활성 부분을 삭제하여 사용자 컴퓨터가 일관되지 않거나 더 나쁜 상태로 남을 수 있습니다.

64비트 버전의 Office는 64비트 레지스트리 하이브를 사용하여 추가 기능을 찾습니다. 64비트 레지스트리 하이브 아래에 추가 기능을 등록하려면 설치 프로젝트의 대상 플랫폼을 64비트로만 설정해야 합니다.

1. 솔루션 탐색기에서 **OfficeAddInSetup** 프로젝트를 선택합니다.
2. **속성** 창으로 이동하여 **TargetPlatform** 속성을 **x64로**설정합니다.

Office의 32비트 및 64비트 버전 모두에 대해 추가 기능을 설치하려면 두 개의 별도의 MSI 패키지를 만들어야 합니다. 하나는 32비트, 64비트용입니다.

  ![64비트 Office에서 추가 기능을 등록하기 위한 대상 플랫폼을 보여주는 속성 창의 스크린샷](media/setup-project-figure-7.jpg)

  **그림 7: 64비트 Office에서 추가 기능 등록을 위한 대상 플랫폼**

MSI 패키지를 사용하여 추가 기능 또는 솔루션을 설치하는 경우 필요한 필수 구성 요소 없이 설치할 수 있습니다. MSI에서 시작 조건을 사용하여 필수 구성 프로그램이 설치되지 않은 경우 추가 기능이 설치되지 않도록 차단할 수 있습니다.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime"></a>VSTO 런타임을 감지하도록 시작 조건을 구성합니다.

1. 솔루션 **탐색기에서** **OfficeAddInSetup**을 마우스 오른쪽 단추로 클릭합니다.
2. **보기를 확장합니다.**
3. **실행 조건을 클릭합니다.**
4. 실행 **조건(OfficeAddInSetup)** 편집기에서 **대상 컴퓨터에서 요구 사항을**마우스 오른쪽 단추로 클릭한 다음 레지스트리 실행 조건 **추가를**클릭합니다. 이 검색 조건은 VSTO 런타임이 설치하는 키에 대해 레지스트리를 검색할 수 있습니다. 그런 다음 명명된 속성을 통해 설치 관리자의 다양한 조각에서 키 값을 사용할 수 있습니다. 시작 조건은 검색 조건에 의해 정의된 속성을 사용하여 특정 값을 확인합니다.
5. 시작 **조건(OfficeAddInSetup)** 편집기에서 **레지스트리Entry1** 검색 조건에 대한 검색을 선택하고 조건을 마우스 오른쪽 단추로 클릭하고 **속성 창을 선택합니다.**

6. **속성** 창에서 다음 속성을 설정합니다.
   1. **VSTO 2010 런타임을 검색할** **수 있는 (이름)** 값을 설정합니다.
   2. **속성** 값을 **VSTORUNTIMEREDIST로**변경합니다.
   3. 소프트웨어 **\\\\마이크로 소프트 VSTO 런타임 설치\\v4R에** **RegKey의** 값을 설정
   4. **루트** 속성을 **vsdrrHKLM으로**설정된 상태로 둡니다.
   5. **Value** 속성을 **버전으로**변경합니다.

7. 시작 **조건(OfficeAddInSetup)** 편집기에서 **조건1** 시작 조건을 선택하고 조건을 마우스 오른쪽 단추로 클릭하고 **속성 창을 선택합니다.**
8. 속성 창에서 다음 속성을 설정합니다.
   1. **VSTO 2010 런타임 가용성을 확인하려면** **(이름)을** 설정합니다.
   2. **조건** 값을 **VSTORUNTIMEREDIST\>="10.0.30319"로 변경합니다.**
   3. **InstallURL** 속성을 비워 둡니다.
   4. Office **Message** **런타임용 Visual Studio 2010 도구에 대한 메시지 설정이 설치되어 있지 않습니다. 설치.exe를 실행하여 추가 기능을 설치하십시오.**

        ![런타임 가용성 실행 조건 확인에 대한 속성 창의 스크린샷](media/setup-project-figure-8.jpg)

        **그림 8: 런타임 가용성 실행 조건 확인에 대한 속성 창**

 위의 시작 조건은 bootstrapper 패키지에 의해 설치될 때 VSTO 런타임의 존재를 명시적으로 확인합니다.

### <a name="configure-a-launch-condition-to-detect-the-vsto-runtime-installed-by-office"></a>Office에서 설치한 VSTO 런타임을 검색하도록 시작 조건을 구성합니다.

1. 시작 **조건(OfficeAddInSetup)** 편집기에서 **대상 컴퓨터 검색을**마우스 오른쪽 단추로 클릭한 다음 레지스트리 검색 **추가를**클릭합니다.
2. **레지스트리Entry1** 검색 조건을 선택하, 조건을 마우스 오른쪽 단추로 클릭 하 고 **속성 창을**선택 합니다.
3. **속성** 창에서 다음 속성을 설정합니다.
    1. **Office VSTO 런타임** **검색에 (이름)** 값을 설정합니다.
    2. **속성** 값을 **OfficeRuntime으로**변경합니다.
    3. 소프트웨어 **\\마이크로 소프트\\VSTO 런타임 설치\\v4에** **RegKey의** 값을 설정합니다 .
    4. **루트** 속성을 **vsdrrHKLM으로**설정된 상태로 둡니다.
    5. **Value** 속성을 **버전으로**변경합니다.

4. 시작 **조건(OfficeAddInSetup)** 편집기에서 이전에 정의된 **VSTO 2010 런타임 가용성** 시작 조건 확인을 선택하고 조건을 마우스 오른쪽 단추로 클릭하고 **속성 창을 선택합니다.**

5. **조건** 속성값을 **VSTORUNTIMEREDIST \>="10.0.30319" 또는 OFFICERUNTIME\>="10.0.21022"로**변경합니다. 버전 번호는 추가 기능이 요구하는 런타임 버전에 따라 다를 수 있습니다.

    ![시작 조건에 대 한 속성 창의 스크린샷](media/setup-project-figure-9.jpg)
  
    **그림 9: Redist 또는 Office 시작 조건을 통해 런타임 가용성 확인에 대 한 속성 Windows**

추가 기능이 .NET Framework 4 또는 최신 을 대상으로 하는 경우 참조되는 기본 Interop 어셈블리(PIA) 내의 형식을 VSTO 어셈블리에 임베드할 수 있습니다.

다음 단계를 수행하여 Interop 유형이 추가 프로그램에 포함될지 확인하려면 다음 단계를 수행합니다.

1. 솔루션 탐색기에서 참조 노드 확장
2. PIA 참조 중 하나를 선택합니다(예: **Office**.
3. F4를 누르거나 어셈블리 컨텍스트 메뉴에서 속성을 선택하여 속성 창을 봅니다.
4. 속성 **포함 interop 형식의**값을 확인합니다.

값이 **True로**설정된 경우 Type이 포함되고 [**설치 프로젝트 작성하기**](#to-build-the-setup-project) 섹션으로 건너뛸 수 있습니다.

자세한 내용은 [유형 동등성 및 임베디드 Interop 형식을](/dotnet/framework/interop/type-equivalence-and-embedded-interop-types) 참조하십시오.

### <a name="to-configure-launch-conditions-to-detect-that-for-office-pias"></a>Office PIA에 대해 이를 감지하도록 시작 조건을 구성하려면

1. 실행 **조건(OfficeAddInSetup)** 편집기에서 **대상 컴퓨터에서 요구 사항을**마우스 오른쪽 단추로 클릭한 다음 Windows 설치 관리자 실행 조건 **추가를 클릭합니다.** 이 시작 조건은 특정 구성 요소 ID를 검색하여 Office PIA를 검색합니다.
2. **구성 요소 1 검색을** 마우스 오른쪽 단추로 클릭하고 속성 **창을** 클릭하여 시작 조건의 속성을 표시합니다.
3. 속성 **창에서**다음 속성을 설정합니다.

    1. **(이름)** 속성의 값을 **Office 공유 PIA 검색으로** 변경합니다.
    2. 사용 중Office 구성 요소에 대한 **ComponentID** 값을 구성 요소 ID로 변경합니다. 아래 표에서 **{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}** 등 구성 요소 ID 목록을 찾을 수 있습니다.
    3. **속성** 의 값을 **HASSHAREDPIA로**변경합니다.

4. 시작 **조건(OfficeAddInSetup)** 편집기에서 **조건1을** 마우스 오른쪽 단추로 클릭하고 **속성 창을** 클릭하여 시작 조건의 속성을 표시합니다.

5. **조건1의**이러한 속성을 변경합니다.

    1. **(이름)을** Office **공유 PIA 가용성 확인으로**변경합니다.
    2. **조건을** **하스쉐피아로**변경합니다.
    3. **InstallUrl을** 비워 둡니다.
    4. Excel과 상호 작용하는 데 필요한 구성 요소로 **메시지를** 변경할 **수 없습니다. 설치 를 실행하십시오.exe**.

    ![확인 사무실 공유 PIA 시작 조건에 대 한 속성 창의 스크린샷](media/setup-project-figure-10.jpg)
  
    **그림 10: 확인 사무실 공유 PIA 시작 조건에 대 한 속성 창**

### <a name="component-ids-of-the-primary-interop-assemblies-for-microsoft-office"></a>Microsoft Office용 기본 interop 어셈블리의 구성 요소 아이디

|기본 인터옵 어셈블리|Office 2010|Office 2013|사무실 2013 (64 비트)|Office 2016|사무실 2016 (64 비트)|
|------------------------|------------------------|------------------------|------------------------|------------------------|------------------------|
|Excel|{EA7564AC-C67D-4868-BE5C-26E4FC2223FF}|{C8A65ABE-3270-4FD7-B854-50C8082C8F39}|{E3BD1151-B9CA-4D45-A77E-51A6E0ED322A}|C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|{C4ACE6DB-AA99-401F-8BE6-8784BD09F003}|
|InfoPath|{4153F732-D670-4E44-8AB7-500F2B576BDA}|{0F825A16-25B2-4771-A497-FC8AF3B355D8}|{C5BBD36E-B320-47EF-A512-556B99CB7E41}|-|-|
|Outlook|{1D844339-3DAE-413E-BC13-62D6A52816B2}|{F9F828D5-9F0B-46F9-9E3E-9C59F3C5E136}|{7824A03F-28CC-4371-BC54-93D15EFC1E7F}|{7C6D92EF-7B45-46E5-8670-819663220E4E4E}|{7C6D92EF-7B45-46E5-8670-819663220E4E4E}|
|PowerPoint|{EECBA6B8-3A62-44AD-99EB-8666265466F9}|{813139AD-6DAB-4DDD-8C6D-0CA30D073B41}|{05758318-BCFD-4288-AD8D-81185841C235}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|{E0A76492-0FD5-4EC2-8570-AE1BAA61DC88}|
|Visio|{3EA123B5-6316-452E-9D51-A489E06E2347}|{C1713368-12A8-41F1-ACA1-934B01AD6EEB}|{2CC0B221-22D2-4C15-A9FB-DE818E51AF75}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|{2D4540EC-2C88-4C28-AE88-2614B5460648}|
|Word|{8B74A499-37F8-4DEA-B5A0-D72FC501CEFA}|{9FE736B7-B1EE-410C-8D07-082891C3DAC8}|{13C07AF5-B206-4A48-BB5B-B802233E3E3CA}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|{DC5CCACD-A7AC-4FD3-9F70-9454B5DE5161}|
|마이크로소프트 양식 2.0|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{B2279272-3FD2-434D-B94E-E4E0F8561AC4}|{A5A30117-2D2A-4C5C-B3C8-8897AC32C2AC}|-|-|
|Microsoft Graph|{011B9112-EBB1-4A6C-86CB-C2FDC9EA7B0E}|{52DA4B37-B8EB-4B7F-89C1-824654CE4C70}|{24706F33-F0CE-4EB4-BC91-9E935394F510}|-|-|
|Smart Tag(스마트 태그)|{7102C98C-EF47-4F04-A227-FE33650BF954}|{487A7921-EB3A-4262-BB5B-A5736B732486}|{74EFC1F9-747D-4867-B951-EFCF29F51AF7}|-|-|
|사무실 공유|{64E2917E-AA13-4CA4-BFFE-EA6EDA3AFCB4}|{6A174BDB-0049-4D1C-86EF-3114CB0C4C4E}|{76601EBB-44A7-49EE-8DE3-7B7B9D7EBB05}|{625F5772-C1B3-497E-8ABE-7254EDB0506}|{625F5772-C1B3-497E-8ABE-7254EDB0506}|
|프로젝트|{957A4EC0-E67B-4E86-A383-6AF7270B216A}|{1C50E422-24FA-44A9-A120-E88280C8C341}|{706D7F44-8231-489D-9B25-3025ADE9F114}|{107BCD9A-F1DC-4004-A444-33706FC10058}|{107BCD9A-F1DC-4004-A444-33706FC10058}|

  ![최종 발사 조건의 스크린샷](media/setup-project-figure-11.jpg)

  **그림 11: 최종 발사 조건**

ExcelAddIn 설치에 대한 시작 조건을 더 구체화할 수 있습니다. 예를 들어 실제 대상 Office 응용 프로그램이 설치되어 있는지 확인하는 것이 유용할 수 있습니다.

### <a name="to-build-the-setup-project"></a>설치 프로젝트를 빌드하려면

1. 솔루션 **탐색기에서** **OfficeAddInSetup** 프로젝트를 마우스 오른쪽 단추로 클릭하고 **빌드를**클릭합니다.
2. **Windows 탐색기를**사용하여 **OfficeAddInSetup** 프로젝트의 출력 디렉토리로 이동하여 선택한 빌드 구성에 따라 릴리스 또는 디버그 폴더로 이동합니다. 폴더의 모든 파일을 사용자가 액세스할 수 있는 위치로 복사합니다.

ExcelAddIn 설정을 테스트하려면

1. **OfficeAddInSetup을** 복사한 위치로 이동합니다.
2. **OfficeAddInSetup** 추가 기능을 설치하려면 setup.exe 파일을 두 번 클릭합니다. 표시되는 모든 소프트웨어 라이센스 약관에 동의하고 설치 마법사를 완료하여 사용자 컴퓨터에 추가 기능을 설치합니다.

Excel Office 솔루션은 설치 중에 지정된 위치에서 설치하고 실행해야 합니다.

## <a name="additional-requirements-for-document-level-solutions"></a>문서 수준 솔루션에 대한 추가 요구 사항

문서 수준 솔루션을 배포하려면 Windows 설치 관리자 설치 프로젝트에서 몇 가지 다른 구성 단계가 필요합니다.

다음은 문서 수준 솔루션을 배포하는 데 필요한 기본 단계 목록입니다.

- 비주얼 스튜디오 설치 프로젝트를 만듭니다.
- 문서 수준 솔루션의 기본 출력을 추가합니다. 기본 출력에는 Microsoft Office 문서도 포함됩니다.
- 배포 및 응용 프로그램 매니페스트를 느슨한 파일로 추가합니다.
- 설치 관리자 패키지에서 종속 구성 요소를 제외합니다(유틸리티 어셈블리 제외).
- 필수 구성 조건 패키지를 구성합니다.
- 시작 조건을 구성합니다.
- 설치 프로젝트를 빌드하고 결과를 배포 위치에 복사합니다.
- 설정을 실행하여 사용자 컴퓨터에 문서 수준 솔루션을 배포합니다.
- 필요한 경우 사용자 지정 문서 속성을 업데이트합니다.

### <a name="changing-the-location-of-the-deployed-document"></a>배포된 문서의 위치 변경

Office 문서 내부의 속성은 문서 수준 솔루션을 찾는 데 사용됩니다. 문서가 VSTO 어셈블리와 동일한 폴더에 설치된 경우 변경할 필요가 없습니다. 그러나 다른 폴더에 설치 된 경우 이러한 속성을 설정 하는 동안 업데이트 해야 합니다.

이러한 문서 속성에 대한 자세한 내용은 [사용자 지정 문서 속성 개요를](custom-document-properties-overview.md)참조하십시오.

이러한 속성을 변경하려면 설치 중에 사용자 지정 작업을 사용해야 합니다.

다음 예제에서는 ExcelWorkbookProject라는 문서 수준 솔루션과 ExcelWorkbookSetup이라는 설치 프로젝트를 사용합니다. ExcelWorkbookSetup 프로젝트는 레지스트리 키를 설정하는 것을 제외하고 위에서 설명한 것과 동일한 단계를 사용하여 구성됩니다.

Visual Studio 솔루션에 사용자 지정 작업 프로젝트를 추가하려면

1. **솔루션 탐색기에서** **Office 문서 배포 프로젝트를** 마우스 오른쪽 단추로 클릭하여 솔루션에 새 .NET 콘솔 프로젝트를 추가합니다.
2. **추가** 를 확장하고 **새 프로젝트를**클릭합니다.
3. 콘솔 앱 템플릿을 선택하고 프로젝트 **AddCustomization사용자 지정 작업의**이름을 지정합니다.

    ![솔루션 탐색기의 스크린샷 - 사용자 지정 추가 사용자 지정 작업](media/setup-project-figure-15.jpg)
  
    **그림 12: 솔루션 탐색기 - 사용자 지정 추가 사용자 지정 작업**

4. 다음 어셈블리에 참조 추가:
    1. System.ComponentModel
    2. System.Configuration.Install
    3. 마이크로소프트.비주얼 스튜디오.도구.응용 프로그램
    4. Microsoft.VisualStudio.Tools.Applications.ServerDocument

5. 이 코드를 Program.cs 또는 Program.vb로 복사합니다.

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

문서에 사용자 지정을 추가하려면 VSTO 문서 수준 솔루션의 솔루션 ID가 있어야 합니다. 이 값은 Visual Studio 프로젝트 파일에서 검색됩니다.

솔루션 ID를 검색하려면

1. **빌드** 메뉴에서 **솔루션 빌드를** 클릭하여 문서 수준 솔루션을 빌드하고 프로젝트 파일에 솔루션 ID 속성을 추가합니다.
2. 솔루션 **탐색기에서**문서 수준 프로젝트 **ExcelWorkbookProject를** 마우스 오른쪽 단추로 클릭합니다.
3. **[언로드프로젝트]를** 클릭하여 비주얼 스튜디오 내부에서 프로젝트 파일에 액세스합니다.

    ![솔루션 탐색기 언로드 Excel 문서 솔루션의 스크린샷](media/setup-project-figure-16.jpg)

    **그림 13: Excel 문서 솔루션 언로드**

4. 솔루션 **탐색기에서**오른쪽 클릭 **ExcelWorkbookProject를** 클릭하고 **편집 엑셀워크북프로젝트.vbproj** 또는 **편집 엑셀워크북Project.csproj**.
5. **ExcelWorkbookProject** 편집기에서 **속성 그룹** 요소 내에서 **SolutionID** 요소를 찾습니다.
6. 이 요소의 GUID 값을 복사합니다.

    ![솔루션 ID 검색](media/setup-project-figure-17.jpg)

    **그림 14: 솔루션 ID 검색**

7. 솔루션 **탐색기에서** **ExcelWorkbookProject를** 마우스 오른쪽 단추로 클릭하고 **프로젝트 다시로드를**클릭합니다.
8. **ExcelWorkbookProject** 편집기를 닫는 것처럼 보이는 대화 상자에서 **예를** 클릭합니다.
9. **솔루션 ID는** 사용자 지정 설치 작업에 사용됩니다.

마지막 단계는 **설치** 및 **제거** 단계에 대한 사용자 지정 작업을 구성하는 것입니다.

### <a name="to-configure-the-setup-project"></a>설치 프로젝트를 구성하려면

1. 솔루션 **탐색기에서** **ExcelWorkbookSetup을**마우스 오른쪽 단추로 클릭하고 **추가를** 확장하고 **프로젝트 출력을**클릭합니다.
2. 프로젝트 **출력 그룹 추가** 대화 상자에서 **프로젝트** 목록에서 사용자 지정 추가 사용자 **지정 을**클릭합니다.
3. **기본 출력을** 선택하고 **확인을** 클릭하여 대화 상자를 닫고 사용자 지정 작업이 포함된 어셈블리를 설치 프로젝트에 추가합니다.

    ![문서 매니페스트 사용자 지정 작업의 스크린샷 - 프로젝트 출력 그룹 창 추가](media/setup-project-figure-18.jpg)

    **그림 15: 문서 매니페스트 사용자 지정 작업 - 프로젝트 출력 그룹 추가**

4. 솔루션 **탐색기에서** **ExcelWorkbookSetup**을 마우스 오른쪽 단추로 클릭합니다.
5. **보기를** 확장하고 **사용자 지정 작업을**클릭합니다.
6. 사용자 **지정 작업(ExcelWorkbookSetup)** 편집기에서 **사용자 지정 작업을** 마우스 오른쪽 단추로 클릭하고 사용자 지정 작업 **추가를**클릭합니다.
7. **프로젝트에서 항목 선택** 대화 상자에서 **보기** 목록에서 **응용 프로그램 폴더를 클릭합니다.** 추가 사용자 지정 사용자 지정 **작업(활성)에서 기본 출력을** 선택하고 **확인을** 클릭하여 설치 단계에 사용자 지정 작업을 추가합니다.
8. 설치 **노드에서** **사용자 지정 사용자 지정(활성)** 및 **이름 바꾸기에서**기본 출력을 마우스 오른쪽 단추로 클릭합니다. 사용자 지정 작업 내 **문서에 문서 복사 및 사용자 지정 을 연결**합니다.
9. 제거 **노드에서**사용자 지정 **사용자 지정(활성)에서 기본 출력을** 마우스 오른쪽 단추로 클릭하고 **이름 바꾸기를**클릭합니다. 사용자 지정 작업 이름 **문서 폴더에서 문서 제거.**

    ![문서 매니페스트 사용자 지정 작업 창의 스크린샷](media/setup-project-figure-19.jpg)

    **그림 16: 문서 매니페스트 사용자 지정 작업**

10. 사용자 **지정 작업(ExcelWorkbookSetup)** 편집기에서 내 문서에 문서 복사를 마우스 오른쪽 단추로 **클릭하고 사용자 지정을 연결하고** **속성 창을**클릭합니다.
11. 사용자 **지정 작업데이터** **속성** 창에서 사용자 지정 DLL의 위치, 배포 매니페스트 및 Microsoft Office 문서의 위치를 입력합니다. 솔루션ID도 필요합니다.
12. 파일에 설치 오류를 기록하려면 LogFile 매개 변수를 포함하십시오.
s
    ``` text
    /assemblyLocation="[INSTALLDIR]ExcelWorkbookProject.dll" /deploymentManifestLocation="[INSTALLDIR]ExcelWorkbookProject.vsto" /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx" /solutionID="Your Solution ID" /LogFile="[TARGETDIR]Setup.log"
    ```

    ![문서를 내 문서 속성 창으로 복사하는 사용자 지정 작업 스크린샷](media/setup-project-figure-20.jpg)

    **그림 17: 문서를 내 문서에 복사하는 사용자 지정 작업**

13. 제거에 대한 사용자 지정 작업에는 문서 이름이 필요하며 **CustomActionData에서** 동일한 문서위치 매개 변수를 사용하여 이를 제공할 수 있습니다.

    ``` text
    /documentLocation="[INSTALLDIR]ExcelWorkbookProject.xlsx"
    ```

14. **ExcelWorkbookSetup** 프로젝트를 컴파일하고 배포합니다.
15. 내 **문서** 폴더를 보고 ExcelWorkbookProject.xlsx 파일을 엽니다.

## <a name="additional-resources"></a>추가 리소스

[방법: 사무실 런타임을 위한 Visual Studio 도구 설치](how-to-install-the-visual-studio-tools-for-office-runtime-redistributable.md)

[Office 주 Interop 어셈블리](office-primary-interop-assemblies.md)

[VSTO 추가 기능의 레지스트리 항목](registry-entries-for-vsto-add-ins.md)

[Custom Document Properties Overview](custom-document-properties-overview.md)

[Windows 레지스트리에서 양식 영역 지정](/office/vba/outlook/concepts/creating-form-regions/specifying-form-regions-in-the-windows-registry)

[문서에 신뢰 부여](granting-trust-to-documents.md)

## <a name="about-the-authors"></a>저자 정보

Wouter van Vugt는 오피스 오픈 XML 기술을 보유한 Microsoft MVP이며 SharePoint, Microsoft Office 및 관련 .NET 기술을 통해 오피스 비즈니스 응용 프로그램(OBA)을 만드는 데 중점을 둔 독립 컨설턴트입니다.
Wouter는 [MSDN과](/previous-versions/office/developer/office-2007/bb879915(v=office.12))같은 개발자 커뮤니티 사이트에 자주 기여합니다. 그는 여러 백서와 기사뿐만 아니라 오픈 XML : 설명 전자 책이라는 제목의 라인에 사용할 수있는 책을 출판했다.
Wouter는 다양한 채널을 통해 최첨단 기술 콘텐츠를 제공하는 데 중점을 둔 네덜란드 회사인 Code-Counsel의 창립자입니다. Wouter에 대한 자세한 내용은 그의 블로그를 통해 확인할 수 있습니다.

테드 패티슨은 셰어포인트 MVP, 저자, 트레이너, 테드 패티슨 그룹의 창립자입니다. 2005년 가을, 테드는 마이크로소프트의 개발자 플랫폼 전도 그룹에서 Windows SharePoint 서비스 3.0 및 Microsoft Office SharePoint Server 2007에 대한 어센드 개발자 교육 커리큘럼을 작성하도록 고용되었습니다. 그 이후로 Ted는 SharePoint 2007 기술에 대한 전문 개발자 교육에 전적으로 집중해 왔습니다. Ted는 SharePoint를 비즈니스 솔루션 구축을 위한 개발 플랫폼으로 사용하는 방법에 중점을 둔 내부 Windows SharePoint 서비스 3.0이라는 제목의 Microsoft Press용 책을 작성했습니다. 테드는 또한 MSDN 매거진의 오피스 스페이스라는 제목의 개발자 중심 칼럼을 작성합니다.
