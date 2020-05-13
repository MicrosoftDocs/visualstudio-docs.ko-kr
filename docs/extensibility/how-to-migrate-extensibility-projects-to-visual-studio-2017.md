---
title: '방법: 확장성 프로젝트를 비주얼 스튜디오 2017로 마이그레이션 | 마이크로 소프트 문서'
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: b0cae0261b185ee08400e5f3d25735634663f54a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710987"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>방법: 확장성 프로젝트를 Visual Studio 2017로 마이그레이션

이 문서에서는 확장성 프로젝트를 Visual Studio 2017로 업그레이드하는 방법을 설명합니다. 프로젝트 파일을 업데이트하는 방법을 설명하는 것 외에도 확장자 매니페스트 버전 2(VSIX v2)에서 새 버전 3 VSIX 매니페스트 형식(VSIX v3)으로 업그레이드하는 방법도 설명합니다.

## <a name="install-visual-studio-2017-with-required-workloads"></a>필요한 워크로드로 Visual Studio 2017 설치

설치에 다음과 같은 워크로드가 포함되어 있는지 확인합니다.

* .NET 데스크톱 개발
* Visual Studio 확장 개발

## <a name="open-vsix-solution-in-visual-studio-2017"></a>비주얼 스튜디오 2017에서 VSIX 솔루션 열기

모든 VSIX 프로젝트에는 Visual Studio 2017로의 주요 버전 편도 업그레이드가 필요합니다.

프로젝트 파일(예:**.csproj)이*업데이트됩니다.

* 최소비주얼 스튜디오버전 - 이제 15.0으로 설정
* OldTools버전 (이전에 존재하는 경우) - 이제 14.0으로 설정

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>업데이트 마이크로 소프트.VSSDK.BuildTools NuGet 패키지

> [!Note]
> 솔루션이 Microsoft.VSSDK.BuildTools NuGet 패키지를 참조하지 않는 경우 이 단계를 건너뛸 수 있습니다.

새로운 VSIX v3(버전 3) 형식으로 확장을 빌드하려면 새 VSSDK 빌드 도구를 사용하여 솔루션을 빌드해야 합니다. 이것은 Visual Studio 2017과 함께 설치되지만 VSIX v2 확장은 NuGet을 통해 이전 버전에 대한 참조를 보유할 수 있습니다. 그렇다면 솔루션에 대한 Microsoft.VSSDK.BuildTools NuGet 패키지의 업데이트를 수동으로 설치해야 합니다.

NuGet 참조를 업데이트하려면 Microsoft.VSSDK.BuildTools:

* 솔루션을 마우스 오른쪽 단추로 클릭하고 **솔루션에 대한 NuGet 패키지 관리를 선택합니다.**
* **업데이트** 탭으로 이동합니다.
* **마이크로소프트.VSSDK.BuildTools (최신 버전)를**선택합니다.
* 을 눌러 **업데이트 합니다.**

![VSSDK 빌드 도구](media/vssdk-build-tools.png)

## <a name="make-changes-to-the-vsix-extension-manifest"></a>VSIX 확장 매니페스트를 변경합니다.

사용자의 Visual Studio 설치에 확장을 실행하는 데 필요한 모든 어셈블리가 있는지 확인하려면 확장 매니페스트 파일에 모든 필수 구성 요소 또는 패키지를 지정합니다. 사용자가 확장을 설치하려고 하면 VSIXInstaller가 모든 필수 구성 프로그램이 설치되어 있는지 확인합니다. 일부 누락 된 경우 사용자는 확장 설치 프로세스의 일부로 누락 된 구성 요소를 설치 하 라는 메시지가 표시 됩니다.

> [!Note]
> 최소한 모든 확장은 Visual Studio 핵심 편집기 구성 요소를 필수 구성 요소로 지정해야 합니다.

* 확장자 매니페스트 파일(일반적으로 *source.extension.vsixmanifest라고*함)을 편집합니다.
* 15.0을 포함해야 합니다. `InstallationTarget`
* 필요한 설치 필수 구성 조건을 추가합니다(아래 예와 같이).
  * 설치 필수 구성 요소에 대한 구성 요소 아이디만 지정하는 것이 좋습니다.
  * [구성 요소 아이디 식별에 대한 지침은](#find-component-ids)이 문서의 끝에 있는 섹션을 참조하십시오.

예제:

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

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>옵션: 디자이너를 사용하여 VSIX 확장 매니페스트를 변경합니다.

매니페스트 XML을 직접 편집하는 대신 매니페스트 디자이너의 새 **필수 구성 표** 탭을 사용하여 필수 구성 조건을 선택할 수 있으며 XML이 업데이트됩니다.

> [!Note]
> 매니페스트 디자이너는 현재 Visual Studio 인스턴스에 설치된 구성 요소(워크로드 또는 패키지가 아님)만 선택할 수 있도록 허용합니다. 현재 설치되지 않은 워크로드, 패키지 또는 구성 요소에 대한 전제 요소를 추가해야 하는 경우 매니페스트 XML을 직접 편집합니다.

* 오픈 *소스.extension.vsixmanifest [디자인]* 파일.
* **필수 구성 조건** 탭을 선택하고 새 **단추를** 누릅니다.

   ![VSIX 매니페스트 디자이너](media/vsix-manifest-designer.png)

* **새 필수 구성 조건 추가** 창이 열립니다.

   ![vsix 필수 구성 조건 추가](media/add-vsix-prerequisite.png)

* **이름에** 대한 드롭다운을 클릭하고 원하는 전제 를 선택합니다.
* 필요한 경우 버전을 업데이트합니다.

   > [!Note]
   > 버전 필드는 현재 설치된 구성 요소의 버전으로 미리 채워지며 구성 요소의 다음 주 버전까지 범위가 포함됩니다( 포함되지 않음).

   ![로슬린 전제 조건 추가](media/add-roslyn-prerequisite.png)

* **확인**을 누릅니다.

## <a name="update-debug-settings-for-the-project"></a>프로젝트의 디버그 설정 업데이트

Visual Studio의 실험적인 인스턴스에서 확장을 디버깅하려면 **디버그** > **시작 작업에** 대한 프로젝트 설정에 시작 외부 **프로그램인** Visual Studio 2017 설치의 *devenv.exe* 파일로 설정된 값이 있는지 확인합니다.

그것은 처럼 보일 수 있습니다.: *C:\프로그램 파일 (x86)\마이크로소프트 비주얼 스튜디오\2017\엔터프라이즈\Common7\IDE\devenv.exe*

![외부 프로그램 시작](media/start-external-program.png)

> [!Note]
> 디버그 시작 작업은 일반적으로 *.csproj.user* 파일에 저장됩니다. 이 파일은 일반적으로 *.gitignore* 파일에 포함되므로 소스 제어에 커밋할 때 일반적으로 다른 프로젝트 파일과 함께 저장되지 않습니다. 따라서 소스 제어에서 솔루션을 새로 가져온 경우 프로젝트에 시작 작업에 대해 설정된 값이 없을 수 있습니다. Visual Studio 2017로 만든 새 VSIX 프로젝트에는 현재 Visual Studio 설치 디렉토리를 가리키는 기본값으로 만든 *.csproj.user* 파일이 있습니다. 그러나 VSIX v2 확장을 마이그레이션하는 경우 *.csproj.user* 파일에 이전 Visual Studio 버전의 설치 디렉터리에 대한 참조가 포함될 수 있습니다. **디버그** > **시작 작업에** 대한 값을 설정하면 확장을 디버깅하려고 할 때 올바른 Visual Studio 실험 인스턴스가 시작될 수 있습니다.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>확장이 올바르게 빌드되는지 확인합니다(VSIX v3).

* VSIX 프로젝트를 빌드합니다.
* 생성된 VSIX의 압축을 해제합니다.
  * 기본적으로 VSIX 파일은 *[YourCustomExtension].vsix로* *bin/디버그* 또는 *저장소/릴리스* 내부에 있습니다.
  * 내용을 쉽게 볼 수 있도록 *.vsix에서* *.zip으로* 이름을 바꿉니다.
* 세 개의 파일이 있는지 확인합니다.
  * *확장.vsixmanifest*
  * *매니페스트.json*
  * *카탈로그.json*

## <a name="check-when-all-required-prerequisites-are-installed"></a>필요한 모든 필수 구성 조건이 설치되어 있는지 확인

VSIX가 필요한 모든 필수 구성 조건이 설치된 컴퓨터에 성공적으로 설치되어 있는지 테스트합니다.

> [!Note]
> 확장을 설치하기 전에 Visual Studio의 모든 인스턴스를 종료하십시오.

확장을 설치하려고 합니다.

* 비주얼 스튜디오 2017에서

![비주얼 스튜디오 2017에 VSIX 설치 프로그램](media/vsixinstaller-vs-2017.png)

* 선택 사항: 이전 버전의 Visual Studio를 확인합니다.
  * 이전 버전과의 호환성을 증명합니다.
  * 비주얼 스튜디오 2012, 비주얼 스튜디오 2013, 비주얼 스튜디오 2015에서 작동합니다.
* 선택 사항: VSIX 설치 관리자 버전 검사기에서 선택할 수 있는 버전이 있는지 확인합니다.
  * 이전 버전의 Visual Studio(설치된 경우)를 포함합니다.
  * 비주얼 스튜디오 2017이 포함되어 있습니다.

Visual Studio를 최근에 연 경우 다음과 같은 대화 상자가 표시될 수 있습니다.

![프로세스 실행 과](media/vs-running-processes.png)

프로세스가 종료될 때까지 기다리거나 수동으로 작업이 종료됩니다. 나열된 이름으로 또는 괄호 안에 나열된 PID로 프로세스를 찾을 수 있습니다.

> [!Note]
> Visual Studio 의 인스턴스가 실행되는 동안이러한 프로세스는 자동으로 종료되지 않습니다. 다른 사용자의 인스턴스를 포함하여 컴퓨터에서 Visual Studio의 모든 인스턴스를 종료한 다음 다시 시도해야 합니다.

## <a name="check-when-missing-the-required-prerequisites"></a>필요한 필수 구성 조건이 누락된 경우 확인

* 필수 구성 요소(위)에 정의된 모든 구성 요소를 포함하지 않는 Visual Studio 2017이 있는 컴퓨터에 확장을 설치하려고 시도합니다.
* 설치가 누락된 구성 요소/s를 식별하고 VSIXInstaller의 필수 구성 요소로 나열되어 있는지 확인합니다.
* 참고: 확장과 함께 필수 구성 조건을 설치해야 하는 경우 입면이 필요합니다.

![vsixinstaller 누락 된 전제 조건](media/vsixinstaller-missing-prerequisite.png)

## <a name="decide-on-components"></a>구성 요소 결정

종속성을 찾을 때 하나의 종속성이 여러 구성 요소에 매핑될 수 있음을 알게 됩니다. 필수 구성 요소로 지정해야 하는 종속성을 확인하려면 확장과 유사한 기능이 있는 구성 요소를 선택하고 사용자와 설치가능성이 가장 높거나 설치해도 상관없는 구성 요소 유형을 고려하는 것이 좋습니다. 또한 필요한 필수 구성 요소가 확장을 실행할 수 있는 최소값만 충족하고 추가 기능에 대해 특정 구성 요소가 검색되지 않는 경우 확장을 휴면 상태로 만드는 방식으로 확장을 빌드하는 것이 좋습니다.

추가 지침을 제공하기 위해 몇 가지 일반적인 확장 유형과 제안된 전제 조건을 확인했습니다.

확장 유형 | 표시 이름 | ID
--- | --- | ---
편집기 | Visual Studio 핵심 편집기 | Microsoft.VisualStudio.Component.CoreEditor
로슬린 (미국) | C# 및 Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | 관리되는 데스크톱 워크로드 핵심 | Microsoft.VisualStudio.Component.ManagedDesktop.Core
디버거 | Just-In-Time 디버거 | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="find-component-ids"></a>구성 요소 아이디 찾기

Visual Studio 제품으로 정렬된 구성 요소 목록은 [Visual Studio 2017 워크로드 및 구성 요소 ID에 있습니다.](/visualstudio/install/workload-and-component-ids?view=vs-2019) 매니페스트의 필수 구성 요소 아이디에 이러한 구성 요소 아이디를 사용하십시오.

특정 바이너리가 포함된 구성 요소에 대해 잘 모르는 경우 [구성 요소 -> 이진 매핑 스프레드시트를](https://aka.ms/vs2017componentid-binaries)다운로드합니다.

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017-컴포넌트바이너리매핑.xlsx

Excel 시트에는 **구성 요소 이름,** **ComponentId,** **버전**및 이진 / 파일 이름의 네 **가지 열이 있습니다.**  필터를 사용하여 특정 구성요소 및 바이너리를 검색하고 찾을 수 있습니다.

모든 참조에 대해 먼저 핵심 편집기(Microsoft.VisualStudio.Component.CoreEditor) 구성 요소에 있는 내용을 결정합니다.  최소한 핵심 편집기 구성 요소를 모든 확장의 전제 조건으로 지정해야 합니다. 핵심 편집기에 없는 나머지 참조 중 **바이너리/파일 이름** 섹션에 필터를 추가하여 해당 참조의 하위 집합이 있는 구성 요소를 찾습니다.

예제:

* 디버거 확장자가 있고 프로젝트에 *VSDebugEng.dll* 및 *VSDebug.dll에*대한 참조가 있음을 알고 있는 경우 **바이너리 / 파일 이름** 헤더의 필터 단추를 클릭합니다.  "VSDebugEng.dll"을 검색하고 *확인을*선택합니다.  다음으로 **바이너리 / 파일 이름** 헤더의 필터 버튼을 클릭하고 "VSDebug.dll"을 검색하십시오.  확인란을 **선택현재 선택 추가를 필터링하고** **확인을**선택합니다.  이제 구성 **요소 이름을** 살펴보고 확장 유형과 가장 관련이 있는 구성 요소를 찾습니다. 이 예제에서는 Just-In-Time 디버거를 선택하고 vsixmanifest에 추가합니다.
* 프로젝트에서 디버거 요소를 처리하는 경우 필터 검색 상자의 "디버거"를 검색하여 이름에 디버거가 포함된 구성 요소를 확인할 수 있습니다.

## <a name="specify-a-visual-studio-2017-release"></a>비주얼 스튜디오 2017 릴리스 지정

예를 들어 확장에 Visual Studio 2017의 특정 버전이 필요한 경우 15.3에서 릴리스된 기능에 따라 달라지므로 VSIX **InstallationTarget**에서 빌드 번호를 지정해야 합니다. 예를 들어 릴리스 15.3에는 빌드 번호가 '15.0.26730.3'입니다. 여기에서 숫자를 빌드하는 릴리스의 매핑을 볼 수 [있습니다.](../install/visual-studio-build-numbers-and-release-dates.md) 릴리스 번호 '15.3'을 사용하면 제대로 작동하지 않습니다.

확장에 15.3 이상이 필요한 경우 **설치 대상 버전을** [15.0.26730.3, 16.0)으로 선언합니다.

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```
