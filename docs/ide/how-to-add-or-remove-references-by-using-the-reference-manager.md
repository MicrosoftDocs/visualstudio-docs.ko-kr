---
title: 참조 관리자에서 참조 추가
ms.date: 08/02/2019
ms.topic: how-to
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f67c41f860417a27a6003a19672d4cd617d37a6
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284728"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>방법: 참조 관리자를 사용하여 참조 추가 또는 제거

참조 관리자 대화 상자를 사용하여 사용자가 개발했거나 Microsoft 또는 타사에서 개발한 구성 요소에 대한 참조를 추가하고 관리할 수 있습니다. 유니버설 Windows 앱을 개발하는 경우 프로젝트에서 올바른 모든 Windows SDK DLL을 자동으로 참조합니다. .NET 애플리케이션을 개발하는 경우 프로젝트에서 자동으로 *mscorlib.dll*을 참조합니다. 일부 .NET API는 수동으로 추가해야 하는 구성 요소에서 노출됩니다. COM 구성 요소 또는 사용자 지정 구성 요소에 대한 참조를 수동으로 추가해야 합니다.

## <a name="reference-manager-dialog-box"></a>참조 관리자 대화 상자

프로젝트 형식에 따라 참조 관리자 대화 상자의 왼쪽에 다음과 같은 다양한 범주가 표시됩니다.

- **어셈블리**에는 **프레임워크** 및 **확장** 하위 그룹이 포함됩니다.

- **COM**에는 참조에 사용할 수 있는 모든 COM 구성 요소가 나열됩니다.

- **프로젝트**

- **공유 프로젝트**

- **Windows**에는 **핵심** 및 **확장** 하위 그룹이 포함됩니다. **개체 브라우저**를 사용하여 Windows SDK 또는 확장명 SDK에서 참조를 탐색할 수 있습니다.

- **찾아보기**에는 **최근 항목** 하위 그룹이 포함됩니다.

## <a name="add-a-reference"></a>참조 추가

1. **솔루션 탐색기**에서 **참조** 또는 **종속성** 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **참조**를 선택합니다.

   **참조 관리자**가 열리고 사용 가능한 참조 목록이 그룹별로 나열됩니다.

2. 추가할 참조를 지정한 다음, **확인**을 선택합니다.

## <a name="assemblies-tab"></a>어셈블리 탭

**어셈블리** 탭은 참조에 사용할 수 있는 .NET 어셈블리를 모두 나열합니다. **어셈블리** 탭에는 GAC(전역 어셈블리 캐시)의 어셈블리는 표시되지 않습니다. GAC의 어셈블리는 런타임 환경의 일부이기 때문입니다. GAC에 등록된 어셈블리에 대한 참조가 포함된 애플리케이션을 배포하거나 복사하는 경우, 이 어셈블리는 **로컬 복사** 설정과 관계없이 애플리케이션과 함께 배포되거나 복사되지 않습니다. 자세한 내용은 [프로젝트의 참조 관리](../ide/managing-references-in-a-project.md)를 참조하세요.

EnvDTE 네임스페이스(<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a> 또는 <xref:EnvDTE100>)에 대한 참조를 수동으로 추가할 때는 **속성** 창에서 참조의 **Interop 형식 포함** 속성을 **False**로 설정합니다. 이 속성을 **True**로 설정하면 포함할 수 없는 특정 EnvDTE 속성으로 인해 빌드 문제가 발생할 수 있습니다.

모든 데스크톱 프로젝트에는 **mscorlib**에 대한 암시적 참조가 포함되어 있습니다. Visual Basic 프로젝트에는 <xref:Microsoft.VisualBasic>에 대한 암시적 참조가 포함되어 있습니다. System.Core가 참조 목록에서 제거되더라도 모든 프로젝트에 **System.Core**에 대한 암시적 참조가 포함되어 있습니다.

프로젝트 형식이 어셈블리를 지원하지 않으면 참조 관리자 대화 상자에 이 탭이 나타나지 않습니다.

**어셈블리** 탭은 다음 두 개의 하위 탭으로 구성됩니다.

1. **프레임워크** 탭에는 대상 프레임워크를 구성하는 모든 어셈블리가 나열됩니다.

   .NET Core 또는 유니버셜 Windows 플랫폼을 대상으로 하지 않는 프로젝트의 경우 **프레임워크** 탭은 대상 프레임워크에서 어셈블리를 열거합니다. 사용자는 애플리케이션에서 필요한 모든 참조를 추가해야 합니다.

   범용 Windows 프로젝트에는 기본적으로 대상 프레임워크의 모든 어셈블리에 대한 참조가 포함됩니다. 관리 프로젝트에서 **솔루션 탐색기**의 **참조** 폴더 아래에 있는 읽기 전용 노드는 전체 프레임워크에 대한 참조를 나타냅니다. 따라서 **프레임워크** 탭은 프레임워크의 어떠한 어셈블리도 열거하지 않고 대신 다음과 같은 메시지를 표시합니다. "모든 프레임워크 어셈블리가 이미 참조되었습니다. 개체 브라우저를 사용하여 Framework에서 참조를 탐색하십시오."

2. **확장**은 구성 요소 및 컨트롤의 외부 공급업체가 개발하고 대상 프레임워크를 확장한 모든 어셈블리가 나열됩니다. 사용자 애플리케이션의 목적에 따라 이러한 어셈블리가 필요할 수 있습니다.

   **확장**은 다음 위치에 등록된 어셈블리를 열거하여 채워집니다.

   32-bit 컴퓨터:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64-bit 컴퓨터:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   및 이전 버전의 [대상 프레임워크 식별자]

   예를 들어, 프로젝트가 32비트 컴퓨터에서 .NET Framework 4를 대상으로 지정하는 경우, **확장**은 *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx* 및 *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*에서 등록된 어셈블리를 열거합니다.

프로젝트의 프레임워크 버전에 따라 목록의 일부 구성 요소는 표시되지 않을 수 있습니다. 이 비동기화는 다음과 같은 경우에 발생할 수 있습니다.

- 최신 프레임워크 버전을 사용하는 구성 요소는 이전 버전을 대상으로 하는 프로젝트와 호환되지 않습니다.

   프로젝트의 대상 프레임워크 버전을 변경하는 방법에 대한 자세한 내용은 [프레임워크 대상 지정 개요](visual-studio-multi-targeting-overview.md)를 참조하세요.

- .NET Framework 4를 사용하는 구성 요소는 .NET Framework 4.5를 대상으로 하는 프로젝트와 호환되지 않습니다.

동일한 솔루션에 있는 다른 프로젝트의 출력에 대한 파일 참조를 추가하면 컴파일 오류가 발생할 수 있으므로 이 방법은 사용하지 않는 것이 좋습니다. 대신 **참조 추가** 대화 상자의 **프로젝트** 탭을 사용하여 프로젝트 간 참조를 만듭니다. 이렇게 하면 프로젝트에서 만드는 클래스 라이브러리를 보다 효율적으로 관리할 수 있으므로 개발 팀이 작업하기가 간편해집니다. 자세한 내용은 [끊어진 참조 문제 해결](../ide/troubleshooting-broken-references.md)을 참조하세요.

> [!NOTE]
> Visual Studio 2015 이상에서는 한 프로젝트의 대상 프레임워크 버전이 .NET Framework 4.5 이상이고 다른 프로젝트의 대상 버전이 .NET Framework 2, 3, 3.5 또는 4.0인 경우 프로젝트 참조 대신 파일 참조가 만들어집니다.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>참조 추가 대화 상자에서 어셈블리를 표시하려면

- 다음 위치 중 하나로 어셈블리를 이동하거나 복사합니다.

  - 현재 프로젝트 디렉터리. 이 어셈블리는 **찾아보기** 탭을 통해 찾을 수 있습니다.

  - 같은 솔루션에 있는 다른 프로젝트 디렉터리. 이 어셈블리는 **프로젝트** 탭을 통해 찾을 수 있습니다.

  \- 또는 -

- 표시할 어셈블리의 위치를 지정하는 레지스트리 키를 설정합니다.

  32비트 운영 체제의 경우 다음 레지스트리 키 중 하나를 추가합니다.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  64비트 운영 체제의 경우에는 32비트 레지스트리 하이브에 포함된 다음 레지스트리 키 중 하나를 추가합니다.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* 은 적용되는 최하위 프레임워크 버전입니다. *\<VersionMinimum\>* 이 v3.0인 경우 *AssemblyFoldersEx*에 지정된 폴더는 .NET Framework 3.0 이상을 대상으로 하는 프로젝트에 적용됩니다.

  *\<AssemblyLocation\>* 은 **참조 추가** 대화 상자에 표시하려는 어셈블리의 디렉터리(예: *C:\MyAssemblies*)입니다.

  `HKEY_LOCAL_MACHINE` 노드 아래에 레지스트리 키를 만들면 모든 사용자가 **참조 추가** 대화 상자에서 지정된 위치의 어셈블리를 볼 수 있습니다. `HKEY_CURRENT_USER` 노드 아래에 레지스트리 키를 만들면 현재 사용자에 대한 설정에만 영향을 줍니다.

  **참조 추가** 대화 상자를 다시 엽니다. 어셈블리가 **.NET** 탭에 나타나야 합니다. 어셈블리가 나타나지 않으면 지정된 *AssemblyLocation* 디렉터리에 어셈블리가 있는지 확인하고 Visual Studio를 다시 시작한 후 다시 시도합니다.

## <a name="projects-tab"></a>프로젝트 탭

**프로젝트** 탭은 **솔루션** 하위 탭에 현재 솔루션 내 모든 호환 가능한 프로젝트를 나열합니다.

프로젝트는 다른 버전의 프레임워크를 대상으로 하는 다른 프로젝트를 참조할 수 있습니다. 예를 들어, .NET Framework 4를 대상으로 하지만 .NET Framework 2용으로 빌드된 어셈블리를 참조하는 프로젝트를 만들 수 있습니다. 그러나 .NET Framework 2 프로젝트는 .NET Framework 4 프로젝트를 참조할 수 없습니다. 자세한 내용은 [Framework 대상 지정 개요](../ide/visual-studio-multi-targeting-overview.md)를 참조하세요.

> [!NOTE]
> .NET Framework 4를 대상으로 하는 프로젝트가 .NET Framework 4 클라이언트 프로필을 대상으로 하는 프로젝트와 호환되지 않습니다.

## <a name="shared-projects-tab"></a>공유 프로젝트 탭

참조 관리자 대화 상자의 **공유 프로젝트** 탭에서 공유 프로젝트에 대한 참조를 추가합니다. [공유 프로젝트](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows)를 사용하면 다양한 애플리케이션 프로젝트에서 참조되는 공통 코드를 작성할 수 있습니다.

## <a name="universal-windows-tab"></a>유니버설 Windows 탭

**유니버설 Windows** 탭은 Windows 운영 체제를 실행하는 플랫폼에 관련된 모든 SDK를 나열합니다.
이 탭에는 두 개의 하위 그룹이 있습니다. **핵심** 및  **확장 프로그램**.

### <a name="core-subgroup"></a>핵심 하위 그룹

유니버설 Windows 앱 프로젝트에는 기본적으로 유니버설 Windows SDK에 대한 참조가 있습니다. 따라서 **참조 관리자**의 **핵심** 하위 그룹은 유니버설 Windows SDK의 어셈블리를 열거하지 않습니다.

### <a name="extensions-subgroup"></a>확장 하위 그룹

**확장**은 대상 Windows 플랫폼을 확장하는 사용자 SDK를 나열합니다.

SDK는 Visual Studio에서 단일 구성 요소로 처리하는 파일의 컬렉션입니다. **확장** 탭에서, 참조 관리자 대화 상자가 호출된 프로젝트에 적용되는 SDK는 단일 항목으로 나열됩니다. SDK 콘텐츠는 프로젝트에 추가되면 모두 Visual Studio에서 사용되므로 IntelliSense, 도구 상자, 디자이너, 개체 브라우저, 빌드, 배포, 디버깅, 패키지의 SDK 콘텐츠를 활용하기 위해 사용자가 어떠한 추가 작업도 수행할 필요가 없습니다.

**확장** 탭에서 SDK를 표시하는 방법은 [방법: 소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)를 참조하세요.

> [!NOTE]
> 프로젝트가 다른 SDK에 종속된 SDK를 참조하는 경우, Visual Studio는 수동으로 두 번째 SDK에 대한 참조를 추가하지 않는 한 두 번째 SDK를 사용하지 않습니다. 사용자가 **확장** 탭에서 SDK를 선택하면, 참조 관리자 대화 상자를 통해 세부 정보 창에 SDK 종속성을 나열하여 SDK 종속성을 식별할 수 있습니다.

프로젝트 형식이 확장을 지원하지 않으면 이 탭은 참조 관리자 대화 상자에 나타나지 않습니다.

## <a name="com-tab"></a>COM 탭

**COM** 탭은 참조에 사용할 수 있는 COM 구성 요소를 모두 나열합니다. 내부 매니페스트가 포함된 등록 COM DLL에 참조를 추가하려는 경우 해당 DLL의 등록을 먼저 해제합니다. 그렇지 않으면 네이티브 DLL 대신 ActiveX 컨트롤 같은 어셈블리 참조가 추가됩니다.

프로젝트 형식이 COM을 지원하지 않으면 참조 관리자 대화 상자에 이 탭이 나타나지 않습니다.

## <a name="browse"></a>Browse

**찾아보기** 단추를 사용하여 파일 시스템의 구성 요소를 찾아볼 수 있습니다.

프로젝트는 다른 버전의 프레임워크를 대상으로 하는 구성 요소를 참조할 수 있습니다. 예를 들어 .NET Framework 4.7을 대상으로 하는 애플리케이션을 만들 수 있지만, .NET Framework 4를 대상으로 하는 구성 요소를 참조합니다. 자세한 내용은 [Framework 대상 지정 개요](../ide/visual-studio-multi-targeting-overview.md)를 참조하세요.

동일한 솔루션에 있는 다른 프로젝트의 출력에 대한 파일 참조를 추가하면 컴파일 오류가 발생할 수 있으므로 이 방법은 사용하지 않는 것이 좋습니다. 대신 참조 관리자 대화 상자의 **솔루션** 탭을 사용하여 프로젝트 간 참조를 만듭니다. 이렇게 하면 프로젝트에서 만드는 클래스 라이브러리를 보다 효율적으로 관리할 수 있으므로 개발 팀이 작업하기가 간편해집니다. 자세한 내용은 [끊어진 참조 문제 해결](../ide/troubleshooting-broken-references.md)을 참조하세요.

SDK를 찾아 프로젝트에 추가할 수는 없습니다. 파일(예: 어셈블리 또는 *.winmd*)만 찾아 프로젝트에 추가할 수 있습니다.

WinMD에 대한 파일 참조를 수행하는 경우, 예상되는 레이아웃은 *\<FileName>.winmd*, *\<FileName>.dll* 및 *\<FileName>.pri* 파일이 모두 나란히 배치되는 것입니다. 다음과 같은 시나리오에서 WinMD를 참조하는 경우, 불완전한 파일 집합이 프로젝트 출력 디렉터리에 복사되고, 그에 따라 빌드 및 런타임 오류가 발생합니다.

- **기본 구성 요소**: 네이티브 프로젝트에서는 연결되지 않은 네임스페이스 집합 각각에 대한 하나의 WinMD 및 그 구현으로 구성된 하나의 DLL을 만듭니다. WinMD는 서로 다른 이름을 갖게 됩니다. 이 기본 구성 요소 파일을 참조하는 경우, MSBuild에서는 서로 다른 이름을 가진 WinMD에서 하나의 구성 요소를 만드는 것을 인식하지 못합니다. 따라서 동일한 이름의 *\<FileName>.dll* 및 *\<FileName>.winmd*만 복사되어 런타임 오류가 발생합니다. 이 문제를 해결하기 위해서는 확장명 SDK를 만듭니다. 자세한 내용은 [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)를 참조하세요.

- **컨트롤 사용**: XAML 컨트롤은 최소 하나씩의 *\<FileName>.winmd*, *\<FileName>.dll*, *\<FileName>.pri*, *\<XamlName>.xaml* 및 *\<ImageName>.jpg*로 구성됩니다. 프로젝트를 빌드할 때 파일 참조와 연관된 리소스 파일은 프로젝트의 출력 디렉터리에 복사되지 않고 *\<FileName>.winmd*, *\<FileName>.dll* 및 *\<FileName>.pri*만 복사됩니다. 빌드 오류가 기록되어 사용자에게 리소스 *\<XamlName>.xaml* 및 *\<ImageName>.jpg*가 누락되었음을 알려줍니다. 성공적으로 빌드하려면 사용자는 이러한 리소스 파일을 수동으로 빌드 및 디버깅/런타임용 프로젝트 출력 디렉터리에 복사해야 합니다. 이 문제를 해결하려면 [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)의 단계에 따라 확장명 SDK를 만들거나, 프로젝트 파일을 편집하여 다음 속성을 추가합니다.

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > 이 속성을 추가하면 빌드 실행이 느려질 수 있습니다.

## <a name="recent"></a>최근 항목

**어셈블리**, **COM**, **Windows** 및 **찾아보기** 탭 각각은 최근에 프로젝트에 추가된 구성 요소의 목록을 열거하는 **최근 항목** 탭을 지원합니다.

## <a name="search"></a>검색

참조 관리자 대화 상자의 검색 창은 포커스가 있는 탭에 대해서 작동합니다. 예를 들어, 사용자가 **솔루션** 탭에 포커스가 있을 때 검색 창에 “System”을 입력한 경우, “System”을 포함하는 프로젝트 이름으로 구성된 솔루션이 아닌 한 어떠한 검색 결과도 반환되지 않습니다.

## <a name="see-also"></a>참조

- [프로젝트에서 참조 관리](../ide/managing-references-in-a-project.md)
