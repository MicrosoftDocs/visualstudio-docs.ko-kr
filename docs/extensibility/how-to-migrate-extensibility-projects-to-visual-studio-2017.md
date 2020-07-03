---
title: '방법: 확장성 프로젝트를 Visual Studio 2017로 마이그레이션 | Microsoft Docs'
ms.date: 11/09/2016
ms.topic: how-to
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 37f7259c1133ea51e004b5f6b2061427ff71dea0
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905843"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>방법: 확장성 프로젝트를 Visual Studio 2017로 마이그레이션

이 문서에서는 확장성 프로젝트를 Visual Studio 2017로 업그레이드 하는 방법을 설명 합니다. 프로젝트 파일을 업데이트 하는 방법을 설명 하는 것 외에도 확장 매니페스트 버전 2 (VSIX v2)에서 새 버전 3 VSIX 매니페스트 형식 (VSIX v3)으로 업그레이드 하는 방법에 대해서도 설명 합니다.

## <a name="install-visual-studio-2017-with-required-workloads"></a>필수 워크 로드를 사용 하 여 Visual Studio 2017 설치

설치에 다음 워크 로드가 포함 되어 있는지 확인 합니다.

* .NET 데스크톱 개발
* Visual Studio 확장 개발

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Visual Studio 2017에서 VSIX 솔루션 열기

모든 VSIX 프로젝트에는 Visual Studio 2017에 대 한 주 버전의 단방향 업그레이드가 필요 합니다.

프로젝트 파일 (예: **.csproj*)이 업데이트 됩니다.

* MinimumVisualStudioVersion-이제 15.0로 설정 됩니다.
* OldToolsVersion (이전에 존재 하는 경우)-이제 14.0로 설정

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Microsoft.. n a m a. n a m a. n a m a 패키지 업데이트

> [!Note]
> 솔루션이 Microsoft. n e t. n e t. n e t.

새 VSIX v3 (버전 3) 형식으로 확장을 빌드하려면 솔루션을 새 고 대 여 진한 빌드 도구로 빌드해야 합니다. 이는 Visual Studio 2017와 함께 설치 되지만 VSIX v2 확장에서 NuGet을 통해 이전 버전에 대 한 참조를 보유 하 고 있을 수 있습니다. 그렇다면 솔루션에 대해 Microsoft.. n a m a. n a m a. n a m a 패키지의 업데이트를 수동으로 설치 해야 합니다.

NuGet 참조를 Microsoft .로 업데이트 하려면 다음을 수행 합니다.

* 솔루션을 마우스 오른쪽 단추로 클릭 하 고 **솔루션용 NuGet 패키지 관리**를 선택 합니다.
* **업데이트** 탭으로 이동 합니다.
* **Microsoft (최신 버전)** 를 선택 합니다.
* **업데이트**를 누릅니다.

![인은 진한 빌드 도구](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>VSIX 확장 매니페스트를 변경 합니다.

확장을 실행 하는 데 필요한 모든 어셈블리가 사용자의 Visual Studio 설치에 포함 되도록 하려면 확장 매니페스트 파일에 모든 필수 구성 요소 또는 패키지를 지정 합니다. 사용자가 확장을 설치 하려고 하면 VSIXInstaller는 모든 필수 구성 요소가 설치 되어 있는지 확인 합니다. 일부 누락 된 경우 확장 설치 프로세스의 일부로 누락 된 구성 요소를 설치 하 라는 메시지가 표시 됩니다.

> [!Note]
> 최소한 모든 확장에서 Visual Studio 핵심 편집기 구성 요소를 필수 구성 요소로 지정 해야 합니다.

* 확장 매니페스트 파일을 편집 합니다 (일반적으로 *source.extension.vsixmanifest*이라고 함).
* `InstallationTarget`15.0이 포함 되어 있는지 확인 합니다.
* 필요한 설치 필수 구성 요소를 추가 합니다 (아래 예제 참조).
  * 설치 필수 구성 요소에 대 한 구성 요소 Id만 지정 하는 것이 좋습니다.
  * [구성 요소 id를 식별 하는 방법](#find-component-ids)에 대 한 지침은이 문서의 끝 부분에 있는 섹션을 참조 하세요.

예:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>옵션: 디자이너를 사용 하 여 VSIX 확장 매니페스트를 변경 합니다.

매니페스트 XML을 직접 편집 하는 대신 매니페스트 디자이너의 새 **필수 구성 요소** 탭을 사용 하 여 필수 구성 요소를 선택할 수 있으며 XML이 업데이트 됩니다.

> [!Note]
> 매니페스트 디자이너를 사용 하면 현재 Visual Studio 인스턴스에 설치 된 구성 요소 (작업 또는 패키지 아님)만 선택할 수 있습니다. 현재 설치 되어 있지 않은 작업, 패키지 또는 구성 요소에 대 한 필수 구성 요소를 추가 해야 하는 경우 매니페스트 XML을 직접 편집 합니다.

* *Source.extension.vsixmanifest [Design]* 파일을 엽니다.
* **필수 구성 요소** 탭을 선택 하 고 **새로 만들기** 단추를 누릅니다.

   ![VSIX 매니페스트 디자이너](media/vsix-manifest-designer.png)

* **새 필수 구성 요소 추가** 창이 열립니다.

   ![vsix 필수 구성 요소 추가](media/add-vsix-prerequisite.png)

* **이름** 드롭다운을 클릭 하 고 원하는 필수 구성 요소를 선택 합니다.
* 필요한 경우 버전을 업데이트 합니다.

   > [!Note]
   > 버전 필드는 현재 설치 되어 있는 구성 요소의 버전으로 미리 채워지며, 범위는 구성 요소의 다음 주 버전까지 포함 됩니다 (포함 하지 않음).

   ![roslyn 필수 구성 요소 추가](media/add-roslyn-prerequisite.png)

* **확인**을 누릅니다.

## <a name="update-debug-settings-for-the-project"></a>프로젝트에 대 한 디버그 설정 업데이트

Visual studio의 실험적 인스턴스에서 확장을 디버깅 하려는 경우 **디버그**시작 동작에 대 한 프로젝트 설정에  >  **Start action** **시작 외부 프로그램:** 값이 visual studio 2017 설치의 *devenv.exe* 파일로 설정 되어 있는지 확인 합니다.

*C:\Program files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe* 와 같을 수 있습니다.

![시작 외부 프로그램](media/start-external-program.png)

> [!Note]
> 디버그 시작 동작은 일반적으로 *.csproj 사용자* 파일에 저장 됩니다. 이 파일은 일반적으로 *.gitignore* 파일에 포함 되어 있으므로 소스 제어에 커밋될 때 일반적으로 다른 프로젝트 파일과 함께 저장 되지 않습니다. 따라서 소스 제어에서 솔루션을 새로 끌어온 경우 프로젝트에 시작 동작에 대 한 값이 설정 되어 있지 않을 수 있습니다. Visual Studio 2017을 사용 하 여 만든 새 VSIX 프로젝트에는 현재 Visual Studio 설치 디렉터리를 가리키는 기본값이 포함 된 *.csproj. 사용자* 파일이 생성 됩니다. 그러나 VSIX v2 확장을 마이그레이션하는 경우에는 *.csproj 사용자* 파일에 이전 Visual Studio 버전의 설치 디렉터리에 대 한 참조가 포함 될 수 있습니다. **디버그**시작 동작에 대 한 값을 설정 하면  >  **Start action** 확장을 디버깅 하려고 할 때 올바른 Visual Studio 실험적 인스턴스를 시작할 수 있습니다.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>확장이 올바르게 빌드되는지 확인 합니다 (VSIX v3로).

* VSIX 프로젝트를 빌드합니다.
* 생성 된 VSIX의 압축을 풉니다.
  * 기본적으로 VSIX 파일은 *bin/Debug* 또는 *bin/Release* (해당 *customextension] .vsix)* 내에 있습니다.
  * 콘텐츠를 쉽게 보려면 *.vsix* 를 *.zip* 으로 바꿉니다.
* 세 개의 파일이 있는지 확인 합니다.
  * *source.extension.vsixmanifest*
  * *manifest.js*
  * *catalog.js*

## <a name="check-when-all-required-prerequisites-are-installed"></a>필요한 모든 필수 구성 요소가 설치 되어 있는지 확인

필요한 모든 필수 구성 요소가 설치 된 컴퓨터에 VSIX가 성공적으로 설치 되었는지 테스트 합니다.

> [!Note]
> 확장을 설치 하기 전에 Visual Studio의 모든 인스턴스를 종료 하세요.

확장을 설치 하려고 시도 합니다.

* Visual Studio 2017

![Visual Studio 2017의 VSIX 설치 관리자](media/vsixinstaller-vs-2017.png)

* 선택 사항: 이전 버전의 Visual Studio를 확인 합니다.
  * 이전 버전과의 호환성을 증명 합니다.
  * Visual Studio 2012, Visual Studio 2013, Visual Studio 2015에 대해 작동 해야 합니다.
* 선택 사항: VSIX 설치 관리자 버전 검사기에서 선택 된 버전을 제공 하는지 확인 합니다.
  * 에는 이전 버전의 Visual Studio (설치 된 경우)가 포함 되어 있습니다.
  * Visual Studio 2017를 포함 합니다.

Visual Studio를 최근에 연 경우 다음과 같은 대화 상자가 표시 될 수 있습니다.

![vs 실행 중인 프로세스](media/vs-running-processes.png)

프로세스가 종료 될 때까지 기다리거나 작업을 수동으로 종료 하십시오. 나열 된 이름이 나 괄호에 나열 된 PID를 사용 하 여 프로세스를 찾을 수 있습니다.

> [!Note]
> 이러한 프로세스는 Visual Studio의 인스턴스가 실행 되는 동안 자동으로 종료 되지 않습니다. 다른 사용자의 컴퓨터를 포함 하 여 모든 Visual Studio 인스턴스를 컴퓨터에서 종료 했는지 확인 한 후 다시 시도 하세요.

## <a name="check-when-missing-the-required-prerequisites"></a>필수 구성 요소가 누락 된 경우 확인

* 필수 구성 요소 (위)에 정의 된 모든 구성 요소를 포함 하지 않는 Visual Studio 2017을 사용 하 여 컴퓨터에 확장을 설치 하려고 합니다.
* 설치에서 누락 된 구성 요소를 식별 하 고 해당 구성 요소를 VSIXInstaller의 필수 구성 요소로 표시 하는지 확인 합니다.
* 참고: 확장을 사용 하 여 필수 구성 요소를 설치 해야 하는 경우 권한 상승이 필요 합니다.

![필수 구성 요소가 누락 vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>구성 요소 결정

종속성을 조회할 때 하나의 종속성이 여러 구성 요소에 매핑될 수 있습니다. 필수 구성 요소로 지정 해야 하는 종속성을 결정 하려면 확장과 비슷한 기능을 포함 하는 구성 요소를 선택 하 고 사용자가 설치 하거나 설치할 수 없는 구성 요소 유형을 선택 하는 것이 좋습니다. 또한 필요한 필수 구성 요소가 확장 프로그램을 실행할 수 있을 뿐 아니라 특정 구성 요소가 검색 되지 않는 경우 추가 기능에 대 한 유휴 상태를 충족 하는 경우에만 확장을 빌드하는 것이 좋습니다.

추가 지침을 제공 하기 위해 몇 가지 일반적인 확장 유형 및 제안 된 필수 구성 요소를 확인 했습니다.

확장 유형 | 표시 이름 | ID
--- | --- | ---
편집기 | Visual Studio 핵심 편집기 | Microsoft.VisualStudio.Component.CoreEditor
Roslyn | C# 및 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | 관리되는 데스크톱 워크로드 핵심 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
디버거 | Just-In-Time 디버거 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>구성 요소 Id 찾기

Visual Studio 제품을 기준으로 정렬 된 구성 요소 목록은 [Visual studio 2017 워크 로드 및 구성 요소 id](/visualstudio/install/workload-and-component-ids?view=vs-2019)에 있습니다. 매니페스트에서 필수 구성 요소 Id에 이러한 구성 요소 Id를 사용 합니다.

특정 이진 파일을 포함 하는 구성 요소가 확실 하지 않으면 [구성 요소 > 이진 매핑 스프레드시트](https://aka.ms/vs2017componentid-binaries)를 다운로드 합니다.

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-ComponentBinaryMapping.xlsx

Excel 시트에는 **구성 요소 이름, 구성 요소** **,** **버전**및 **이진/파일 이름**이라는 4 개의 열이 있습니다.  필터를 사용 하 여 특정 구성 요소 및 이진 파일을 검색 하 고 찾을 수 있습니다.

모든 참조에 대해 먼저 핵심 편집기 (VisualStudio. CoreEditor) 구성 요소에 있는 항목을 확인 합니다.  최소한 핵심 편집기 구성 요소를 모든 확장의 필수 구성 요소로 지정 해야 합니다. 핵심 편집기에 없는 왼쪽에 있는 참조의 경우 **이진 파일/파일 이름** 섹션에 필터를 추가 하 여 해당 참조의 하위 집합이 있는 구성 요소를 찾습니다.

예:

* 디버거 확장이 있고 프로젝트에 *VSDebugEng.dll* 및 *VSDebug.dll*에 대 한 참조가 있음을 알고 있는 경우 **이진 파일/파일 이름** 헤더에서 필터 단추를 클릭 합니다.  "VSDebugEng.dll"을 검색 하 고 *확인을*선택 합니다.  그런 다음 **이진 파일/파일 이름** 헤더에서 필터 단추를 다시 클릭 하 고 "VSDebug.dll"를 검색 합니다.  **필터링 할 현재 선택 항목 추가** 확인란을 선택 하 고 **확인**을 선택 합니다.  이제 **구성 요소 이름을** 살펴보고 확장 형식과 가장 관련이 있는 구성 요소를 찾습니다. 이 예제에서는 Just-in-time 디버거를 선택 하 고 source.extension.vsixmanifest에 추가 합니다.
* 프로젝트가 디버거 요소를 처리 하는 것을 알고 있는 경우 필터 검색 상자에서 "디버거"를 검색 하 여 해당 이름에 디버거가 포함 된 구성 요소를 확인할 수 있습니다.

## <a name="specify-a-visual-studio-2017-release"></a>Visual Studio 2017 릴리스 지정

확장에 특정 버전의 Visual Studio 2017가 필요한 경우 (예: 15.3에서 릴리스된 기능에 따라 달라 지는 경우) VSIX **설치 대상**에서 빌드 번호를 지정 해야 합니다. 예를 들어 릴리스 15.3의 빌드 번호는 ' 15.0.26730.3 '입니다. [여기](../install/visual-studio-build-numbers-and-release-dates.md)에서 빌드 번호에 대 한 릴리스 매핑을 볼 수 있습니다. 릴리스 번호 ' 15.3 '을 사용 하면 제대로 작동 하지 않습니다.

확장에 15.3 이상이 필요한 경우 **설치 대상 버전** 을 [15.0.26730.3, 16.0)로 선언 합니다.

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
